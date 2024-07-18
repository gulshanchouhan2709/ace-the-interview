# Fork & Spawn

**Fork:** It's useful for creating worker processes to handle CPU-intensive tasks like image processing/uploading, heavy computation task etc. It's prevent to block the main worker thread to become a un-responsive.

```js

// server.js

const express = require('express');
const { fork } = require('child_process');
const app = express();
const port = 3000;

app.use(express.json());

// Route to handle image processing
app.post('/process-image', (req, res) => {
  const worker = fork('./worker.js');

  worker.send(req.body);

  worker.on('message', (result) => {
    res.send(result);
    worker.kill();
  });

  worker.on('error', (err) => {
    console.error(`Worker error: ${err}`);
    res.status(500).send('Error processing image');
  });

  worker.on('exit', (code) => {
    console.log(`Worker exited with code: ${code}`);
  });
});

app.listen(port, () => {
  console.log(`Server running at http://localhost:${port}`);
});


```

```js

const sharp = require('sharp'); // Image processing library

process.on('message', async (data) => {
  try {
    const { imageBuffer, width, height } = data;
    const processedImage = await sharp(imageBuffer)
      .resize(width, height)
      .toBuffer();
    process.send({ success: true, processedImage });
  } catch (error) {
    process.send({ success: false, error: error.message });
  }
});

```

**Spawn:** It's useful for running external commands or scripts and handling their input/output.

```js

// run_analysis.js

const { spawn } = require('child_process');

// Function to run the Python script and handle its output
const runPythonScript = (scriptPath, args) => {
  return new Promise((resolve, reject) => {
    const pythonProcess = spawn('python', [scriptPath, ...args]);

    let output = '';
    pythonProcess.stdout.on('data', (data) => {
      output += data.toString();
    });

    pythonProcess.stderr.on('data', (data) => {
      console.error(`stderr: ${data}`);
    });

    pythonProcess.on('close', (code) => {
      if (code !== 0) {
        reject(`Python script exited with code ${code}`);
      } else {
        resolve(output);
      }
    });
  });
};

// Example usage
runPythonScript('analysis.py', ['arg1', 'arg2'])
  .then(result => {
    console.log(`Script output: ${result}`);
  })
  .catch(err => {
    console.error(`Error: ${err}`);
  });

```

```js

import sys

def main():
    arg1 = sys.argv[1]
    arg2 = sys.argv[2]
    # Perform some data analysis
    result = f"Received arguments: {arg1}, {arg2}"
    print(result)

if __name__ == "__main__":
    main()

```


<hr>
