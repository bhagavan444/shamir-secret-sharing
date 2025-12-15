# Shamir's Secret Sharing - Polynomial Reconstruction

This project implements Shamir's Secret Sharing scheme using Lagrange Interpolation to find the secret constant term of a polynomial from given points.

## Problem Statement

Given a set of points (x, y) where:
- x values are sequential (1, 2, 3, ...)
- y values are encoded in different number bases
- We need to find the constant term (secret) of the polynomial that passes through these points

## Algorithm

1. **Base Conversion**: Convert y-values from their respective bases to base 10
2. **Point Collection**: Extract (x, y) pairs from JSON input
3. **Lagrange Interpolation**: Calculate the polynomial value at x=0 using the formula:
```
   f(0) = Σ(yi × Π(-xj/(xi-xj))) for i≠j
```
4. **Secret Extraction**: The result f(0) is the constant term (the secret)

## Project Structure
```
SHAMIR-SECRET/
├── solution.js       # Main program file
├── testcase1.json    # Test case 1 data
├── testcase2.json    # Test case 2 data
├── output.json       # Generated results (created after running)
└── README.md         # This file
```

## Prerequisites

- Node.js (version 12 or higher)
- No external dependencies required (uses built-in modules only)

## Installation

1. Clone or download this repository
2. Ensure Node.js is installed on your system
3. Navigate to the project directory
```bash
cd shamir-secret
```

## How to Run

1. Open terminal in the project directory
2. Run the program:
```bash
node solution.js
```

3. You'll see a menu with three options:
```
   Select which test case to run:
   1. Test Case 1
   2. Test Case 2
   3. Both Test Cases
   
   Enter your choice (1, 2, or 3):
```

4. Enter your choice (1, 2, or 3) and press Enter

## Input Format

The input is in JSON format with the following structure:
```json
{
    "keys": {
        "n": 4,        // Total number of roots provided
        "k": 3         // Minimum roots required (k = m + 1, where m is polynomial degree)
    },
    "1": {
        "base": "10",
        "value": "4"
    },
    "2": {
        "base": "2",
        "value": "111"
    }
    // ... more points
}
```

## Test Cases

### Test Case 1
- n = 4 (4 points provided)
- k = 3 (minimum 3 points needed)
- Polynomial degree = 2
- Points in different bases (base 10, base 2, base 4)

### Test Case 2
- n = 10 (10 points provided)
- k = 7 (minimum 7 points needed)
- Polynomial degree = 6
- Points in various bases (base 3 to base 16)

## Output

The program displays:
1. All points with their converted y-values
2. Final points in format: (x,y)
3. The SECRET (constant term c)
4. Results summary

### Sample Output:
```
==================================================
TEST CASE 1
==================================================
n (total roots provided): 4
k (minimum roots required): 3
Polynomial degree: 2

Point 1: x = 1, y = 4
  (Original: base 10, value "4")
Point 2: x = 2, y = 7
  (Original: base 2, value "111")
Point 3: x = 3, y = 12
  (Original: base 10, value "12")
Point 6: x = 6, y = 39
  (Original: base 4, value "213")

Final points:

(1,4), (2,7), (3,12), (6,39)

**************************************************
SECRET (Constant term c): 3
**************************************************
```

## Output Files

### output.json
Contains the secrets and metadata for the test cases:
```json
{
  "testCase1": {
    "secret": "3",
    "n": 4,
    "k": 3
  },
  "testCase2": {
    "secret": "calculated_value",
    "n": 10,
    "k": 7
  }
}
```

## Features

- ✅ Interactive menu to select test cases
- ✅ Supports multiple number bases (2-16)
- ✅ Uses BigInt for handling large numbers
- ✅ Lagrange interpolation for polynomial reconstruction
- ✅ Displays points in readable format
- ✅ Saves results to JSON file
- ✅ No external dependencies

## Mathematical Background

**Shamir's Secret Sharing** is a cryptographic algorithm that divides a secret into multiple parts (shares). The secret can only be reconstructed when a sufficient number of shares are combined.

**Lagrange Interpolation** is used to reconstruct the polynomial from the given points. For a polynomial of degree m, we need at least k = m + 1 points to uniquely determine it.

## Error Handling

The program handles:
- Missing JSON files (will throw error)
- Invalid JSON format
- Invalid user input (displays error message)
- Large number calculations using BigInt

## Troubleshooting

**Error: Cannot find module 'fs'**
- Make sure you're running Node.js (not browser JavaScript)

**Error: Cannot read file 'testcase1.json'**
- Ensure the JSON files are in the same directory as solution.js

**Error: Invalid choice**
- Enter only 1, 2, or 3 when prompted

## Technical Details

- Language: JavaScript (Node.js)
- Number Handling: BigInt for large integers
- I/O: File System (fs) module for reading/writing files
- User Input: readline module for interactive menu

## Author

Created as a solution for Shamir's Secret Sharing assignment

## License

Free to use for educational purposes

## Contact
<img width="1919" height="1116" alt="image" src="https://github.com/user-attachments/assets/fe8fc550-a5af-4e20-a6ea-3a4e74360171" />
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/fbd89935-11e6-4873-a2a9-84504082ee3a" />
<img width="1919" height="1199" alt="image" src="https://github.com/user-attachments/assets/2a611ee0-12de-4ea0-be93-96b256fc7de8" />






For questions or issues, please refer to the assignment documentation.
