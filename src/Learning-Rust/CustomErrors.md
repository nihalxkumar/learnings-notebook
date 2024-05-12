# Custom Errors

Functions may fail in more than one way

### Error Enumerations

- allows errors to be easily defined.
- can match on different error types.
    - prefer using match wherever possible with errors.

### Error Requirements

- must implement the Debug trait
    - Displays error info in debug context.
- Display traits.
    - Displays error info in user context.
- must implement the Error trait.
    - Interoperability with code using dynamic errors.

### Manual Error Creation

```rust, ignore
#[derive(Debug)]
enum LockError {
    MechanicalError(i32),
    NetworkError,
    NotAuthorized,
}

use std::error::Error;

impl Error for LockError {} // will work with default implementation

use std::fmt;

impl fmt::Display for LockError {
    fn fmt(&self, f: &mut fmt::Formatter) -> fmt::Result {
        match self {
            LockError::MechanicalError(ref err) => write!(f, "Mechanical error: {}", err),
            LockError::NetworkError => write!(f, "Network error"),
            LockError::NotAuthorized => write!(f, "Not authorized"),
        }
    }
}
```

### Using `thiserror` crate

`thiserror` crate provides a procedural macro to derive the Error trait.

```rust, ignore
#[derive(Debug, Error)]
enum LockError {
    #[error("Mechanical error: {0}")]
    MechanicalError(i32),
    #[error("Network error")]
    NetworkError,
    #[error("Not authorized")]
    NotAuthorized,
}

fn lock_door() -> Result<(), LockError> {
    // code
    Err(LockError::NotAuthorized)
}
```

### Error Conversion

```rust, ignore
use thiserror::Error;

#[derive(Debug, Error)]
enum NetworkError {
    #[error("Connection timed out")]
    Timeout,
    #[error("Connection reset by peer")]
    Reset,
    #[error("Unreachable")]
    Unreachable
}

enum LockError {
    #[error("Mechanical error: {0}")]
    MechanicalError(i32),
    #[error("Network error")]
    // type conversion
    NetworkError(#[from] NetworkError),
    #[error("Not authorized")]
    NotAuthorized,
}
```

```admonish note
Never put unrelated error into a single enumeration

changes to the enumeration will cascade across the codebase
```


