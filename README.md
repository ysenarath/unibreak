# unibreak

Python bindings for the [unicode-segmentation](https://crates.io/crates/unicode-segmentation) Rust crate, providing fast and accurate Unicode text segmentation operations.

## Installation

```bash
pip install unibreak
```

## Features

- Unicode-aware word boundary detection and splitting
- Grapheme cluster operations (visible character handling)
- Index-based boundary operations
- High performance through Rust implementation

## Usage

```python
import unibreak

# Split text into words
text = "Hello, 世界! How are you?"
words = unibreak.split_words(text)
# ['Hello', ',', ' ', '世', '界', '!', ' ', 'How', ' ', 'are', ' ', 'you', '?']

# Split into grapheme clusters (visible characters)
text = "👨‍👩‍👧‍👦 é"
graphemes = unibreak.split_graphemes(text)
# ["👨\u200d👩\u200d👧\u200d👦", " ", "é"]

# Get word boundary indices
text = "Hello world"
# Get detailed word boundary information
bounds = unibreak.split_word_bound_indices(text)
# [(0, 'Hello'), (5, ' '), (6, 'world')]

indices = unibreak.word_indices(text)
# [0, 5, 6]

# Get grapheme cluster boundary indices
indices = unibreak.grapheme_indices(text)
# Get word boundary indices

# Count grapheme clusters (visible characters)
length = unibreak.grapheme_len("👨‍👩‍👧‍👦 abc")
# 5

# Check if an index is at a word boundary
is_boundary = unibreak.is_word_boundary("Hello world", 5)
# True
```

## API Reference

### `split_words(text: str) -> List[str]`
Split text into words using Unicode word boundaries.

### `split_graphemes(text: str) -> List[str]`
Split text into grapheme clusters (visible characters).

### `word_indices(text: str) -> List[int]`
Get word boundary indices in text.

### `split_word_bound_indices(text: str) -> List[Tuple[int, str]]`
Get word boundary indices along with their corresponding text segments.

### `grapheme_indices(text: str) -> List[int]`
Get grapheme cluster boundary indices in text.

### `grapheme_len(text: str) -> int`
Count grapheme clusters (visible characters) in text.

### `is_word_boundary(text: str, index: int) -> bool`
Check if the given index is at a word boundary.

## License

MIT License

## Development

This project uses:
- [PyO3](https://pyo3.rs) for Rust-Python bindings
- [unicode-segmentation](https://crates.io/crates/unicode-segmentation) for Unicode text segmentation
