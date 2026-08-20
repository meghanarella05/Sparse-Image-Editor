# Sparse-Image-Editor

# Sparse Image Editor

A tiny black-and-white image editor that stores pictures **only** as a sparse matrix (array of triples).

No real 2-D array is ever allocated.  
The entire program forces you to keep a 2-D mental model while the data lives in a 1-D list of `{row, col, value}` records.

This project exists to practise the exact thinking model taught in the sparse-matrix lab.

---

## Core Idea

- A normal image is a 2-D grid.
- Most pixels are background (0). Only the drawn strokes are non-zero.
- We store **only** the non-zero pixels as triples:
  ```c
  { row, col, value }

  Features (in order of difficulty)
1. Create & Display

Load a list of triples (hard-coded or typed).
Print the image as a normal grid of # and spaces
without ever creating a 2-D array.
Forces the question:
“For every logical (i, j), does a matching triple exist?”

2. Transpose

Implement both naïve and fast transpose.
Show original and transposed image side-by-side.
Visual proof that swapping .row and .col is the sparse equivalent of
matrix[j][i] = matrix[i][j].

3. Rotate 90° / Flip

Pure index remapping of the existing triples.
Same mental model, different arithmetic.

4. Crop / Region Extract

Given a rectangular window, keep only the triples inside it.
Re-number coordinates so the crop starts at (0,0).
Teaches that the logical 2-D coordinate system is independent of storage order.

5. Overlay (“OR”)

Merge two sparse images.
If the same (row, col) exists in both, keep one.
Forces you to treat the list of triples as a set of positions on a 2-D plane.

6. (Optional) Dilation / Thicken Lines

For every existing triple, also insert its four neighbours (if missing).
Still operating on the abstract 2-D grid — just generating new triples.


Why this project?

You never escape the “array of objects” representation.
Every feature forces the 2-D mental model while data lives in a 1-D list.
Transpose becomes a visual, satisfying operation instead of abstract numbers.
Perfect demo for a TA:
“See? Same 2-D thinking — only the storage changed.”
