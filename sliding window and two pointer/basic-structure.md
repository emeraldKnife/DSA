In a standard sliding window, you should always follow this exact sequence:

- Expand: Add the new element at `j` to your window state.

- Shrink (if necessary): If the window becomes invalid `(count > k)`, move `i` forward until the window is valid again.

- Update: Now that you are 100% sure the window `[i, j]` is valid, calculate its length `(j - i + 1)` and update `max_len`.

```
Expand &rarr; Shrink &rarr; Update
```
