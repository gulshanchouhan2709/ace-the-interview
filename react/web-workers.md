# Web Workers

Web workers are a powerful feature in JavaScript that allow us to run scripts in the background, separate from the main thread of web application. This is particularly useful for performing heavy computations or long-running tasks otherwise block the main thread and make the web page unresponsive.

Use Cases for Web Workers:

- Heavy Calculations: When your application needs to perform complex mathematical operations, image processing, or any other CPU-intensive tasks, offloading them to a worker keeps the main thread free.

- File Processing: Uploading or manipulating large files can be handled in a worker, preventing the main thread from becoming unresponsive.

Below is the example of large file upload in chunks via "web worker".

```js

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Large File Upload with Web Worker</title>
</head>
<body>
    <h1>Upload Large File</h1>
    <input type="file" id="file-upload" accept=".txt,.csv">
    <button id="upload-btn">Upload</button>
    <p id="status"></p>

    <script src="worker.js"></script>
    <script>
        const fileUpload = document.getElementById('file-upload');
        const uploadBtn = document.getElementById('upload-btn');
        const statusEl = document.getElementById('status');

        uploadBtn.addEventListener('click', () => {
            const file = fileUpload.files[0];
            if (!file) {
                statusEl.textContent = 'Please select a file';
                return;
            }

            const worker = new Worker('worker.js');
            worker.onmessage = (event) => {
                const message = event.data;
                statusEl.textContent = message;
                if (message === 'Upload complete!') {
                    // Handle successful upload (e.g., clear file input, show success message)
                }
            };
            worker.postMessage({ file: file }); // Send file data to worker
        });
    </script>
</body>
</html>

```

```js

self.addEventListener('message', (event) => {
    const data = event.data;
    const file = data.file;

    // Function to handle file processing in chunks
    function uploadChunk(reader, start, end) {
        const chunk = file.slice(start, end);
        reader.readAsArrayBuffer(chunk); // Read file data in chunks

        reader.onload = (e) => {
            // Send chunk data to server (replace with your actual upload logic)
            const formData = new FormData();
            formData.append('chunk', e.target.result);
            fetch('/upload', {
                method: 'POST',
                body: formData,
            })
            .then(() => {
                const nextStart = end;
                const nextEnd = Math.min(nextStart + chunkSize, file.size);
                if (nextStart < file.size) {
                    uploadChunk(reader, nextStart, nextEnd);
                } else {
                    self.postMessage('Upload complete!'); // Notify main thread of completion
                }
            })
            .catch((error) => {
                self.postMessage(`Upload failed: ${error}`); // Handle upload errors
            });
        };
    }

    const chunkSize = 1024 * 1024; // Define chunk size for efficient upload
    const reader = new FileReader();

    uploadChunk(reader, 0, chunkSize); // Start uploading the first chunk
});


```

<hr>