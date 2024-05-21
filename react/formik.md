# Formik

Formik is a popular library for managing forms in React applications. It provides a convenient way to handle form state, validation, and submission.

```js

import React from 'react';
import { Formik, Form, Field, ErrorMessage } from 'formik';
import * as Yup from 'yup';

const LoginForm = () => {
  // Define initial values
  const initialValues = {
    email: '',
    password: ''
  };

  // Define validation schema using Yup
  const validationSchema = Yup.object({
    email: Yup.string().email('Invalid email format').required('Required'),
    password: Yup.string().min(6, 'Password must be at least 6 characters').required('Required')
  });

  // Define onSubmit function
  const onSubmit = (values) => {
    console.log('Form data', values);
  };

  return (
    <Formik
      initialValues={initialValues}
      validationSchema={validationSchema}
      onSubmit={onSubmit}
    >
      {formik => (
        <Form>
          <div>
            <label htmlFor="email">Email</label>
            <Field type="email" id="email" name="email" />
            <ErrorMessage name="email" component="div" />
          </div>

          <div>
            <label htmlFor="password">Password</label>
            <Field type="password" id="password" name="password" />
            <ErrorMessage name="password" component="div" />
          </div>

          <button type="submit" disabled={!formik.isValid || formik.isSubmitting}>
            Submit
          </button>
        </Form>
      )}
    </Formik>
  );
};

export default LoginForm;

```

Explanation:-

Formik Component: This component wraps the form elements and handles the form state and validation.

initialValues: An object containing the initial values of the form fields.

validationSchema: Using Yup, a validation schema is defined to handle the validation rules.

onSubmit: A function that is called when the form is submitted.

Field Component: Used to create form fields. It automatically hooks into Formik's state and handles form values.

ErrorMessage Component: Displays validation error messages for the corresponding fields.

<hr>