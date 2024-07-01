## working with forms
#### error handling
```
/* Form error handling
============================= */
/* The following code is used to place the icon in the after pseudo element. Because after and before are not possible in an input, we need to use a span that will be positioned on the right of our input. */

input:not(:placeholder-shown) ~ .form-field-icon::after {
    height: 100%;
    right: 0;
    pointer-events: none;
    position: absolute;
    top: 0;
    width: 1.3em;
  }
  
  /* Because inputs are invalid by default, we need to be careful and show the icon when we are not in focus and when when the input is not empty (placeholder-shown). Careful with this one because it is not supported everywhere. */
  
  input:required:invalid:not(:focus):not(:placeholder-shown) ~ .form-field-icon::after {
    content: '✘';
    color: var(--error-color);
  }
  
  input:required:valid ~ .form-field-icon::after {
    content: '✔';
    color: var(--valid-color);
  }
  
  /* We want to hide the helper text when we are not in focus. The tilte allows us to select a sibling element in CSS */
  
  input:required:valid ~ .form-help {
    max-height: 0;
  }
  
  /* Showing a border in a different color is good but not enough. For accessibility purposes, we added an icon when the input is valid or invalid to have a visual distinction that is not only color based.*/
  
  input:required:invalid:not(:focus):not(:placeholder-shown),
  textarea:invalid:not(:focus):not(:placeholder-shown) {
    border: 0.1rem solid var(--error-color);
  }
  
  input:required:valid:not(:placeholder-shown),
  textarea:valid:not(:placeholder-shown) {
    border: 0.1rem solid var(--valid-color);
  }
```