# Reading Classifier (Nearest-Example Companion) 🤖📊

A lightweight Python class that classifies a numeric sensor/reading as **"Normal"** or **"Unusual"** by comparing it to a small set of labeled example readings, using a nearest-neighbor approach.

## Overview

The `companion` class holds a dictionary of example readings mapped to labels (`Normal` / `Unusual`). To classify a new reading, it finds the closest known example (by absolute difference) and returns that example's label. The script also evaluates the classifier's accuracy against a small labeled test set and logs any readings classified as "Unusual".

## Features

- 🧠 Simple 1-nearest-neighbor classification based on labeled example data
- ✅ Built-in accuracy test against a sample test set, with mismatches printed for inspection
- 📥 Automatic logging of "Unusual" readings into the companion's `readings` history
- 🪶 Zero dependencies — pure Python, no external libraries required

## How It Works

1. A `companion` object is created with a `name` and a fixed set of example readings (`self.examples`), each mapped to a label.
2. `classify(reading)` finds the example key with the smallest absolute difference to the input reading and returns its label.
3. A `test` list of `(reading, expected_label)` pairs is run through the classifier:
   - Correct predictions increase an accuracy counter.
   - Incorrect predictions print the input, the predicted label, and the expected label.
4. Overall accuracy is printed as a percentage.
5. A new reading (`value = 80`) is classified; if the result is `"Unusual"`, it's appended to `my_companion.readings`.

## Getting Started

1. Make sure you have Python 3 installed.
2. Run the script:
   ```bash
   python AI_project.py
   ```
3. Review the console output for:
   - Any test cases the classifier got wrong
   - The overall accuracy percentage
   - The classification result for the sample `value = 80`
   - The current list of logged "Unusual" readings

## Customization

- **Example set**: Expand `self.examples` with more labeled readings to improve classification coverage.
- **Test set**: Modify the `test` list to evaluate against your own labeled data.
- **Input value**: Change the `value` variable to classify different readings.

## Known Issues / Notes

- The test set contains a label typo (`"unusual"` instead of `"Unusual"` for the first case), which will always be counted as a mismatch since label comparison is case-sensitive — worth fixing if you want accurate results.
- `sum` is used as a variable name, which shadows Python's built-in `sum()` function — consider renaming it (e.g. `correct`) for cleaner code.
- This is a nearest-neighbor lookup, not a trained machine learning model — accuracy depends entirely on how representative `self.examples` is.

## License

This project is open source and available under the [MIT License](LICENSE).
