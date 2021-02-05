# Uncontrolled Components

The basic idea is letting the DOM handle the form data rather than React. This
helps reduce re-renders.

## Making and working with uncontrolled components

Typically, you will use `ref`s to access the DOM node for the form control.

```jsx
function UncontrolledInput() {
  const firstNameRef = useRef();
  
  useEffect(() => {
    // Take a copy of the input so it exists for clean up
    const firstNameInput = firstNameRef.current;
    
    firstNameInput.addEventListener('input', handleFirstNameChange);
    
    // Clean up
    return () => firstNameInput.removeEventListener('input', handleFirstNameChange);
  });

  return <input ref={nameRef} name="firstName" />;
}

function handleFirstNameChange(event) {
  // do something with the value when it changes
}
```

## Further Reading

- [Uncontrolled form validation with React](https://dev.to/bluebill1049/uncontrolled-form-for-react-2b3n)
  - These notes are largely based on Bill’s article here.
