# Tool Functions

Plain Python functions that get executed automatically when Claude determines it needs extra information to help a user.

## Key Characteristics

- Plain Python functions, called by Claude when needed
- Must use descriptive function names and argument names
- Should validate inputs and raise errors with meaningful messages
- Error messages are visible to Claude, letting it retry with corrected parameters

## Best Practices

1. Well-named functions and arguments
2. Input validation, with immediate error-raising for invalid inputs
3. Meaningful error messages that guide correction

## Example

```python
def get_current_datetime(date_format="%Y%m%d %H:%M:%S"):
    if not date_format:
        raise ValueError("date format cannot be empty")
    return datetime.now().strftime(date_format)
```

## Tool Function Workflow

Claude identifies a need for information → calls the tool function → receives a result or error → may retry with corrections if an error occurred.

## Purpose

Extend Claude's capabilities beyond its training data — giving it access to real-time information like the current datetime, weather, etc.
