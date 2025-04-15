# Credit Card Checker

## Overview
This project implements a credit card validation system that can identify valid and invalid credit card numbers using the Luhn algorithm. It also identifies which credit card companies have issued potentially invalid cards.

## Features
- **Card Validation**: Uses the Luhn algorithm to check if a credit card number is valid
- **Invalid Card Detection**: Identifies which credit cards in a batch are invalid
- **Company Identification**: Determines which companies issued the invalid cards based on the first digit

## How It Works

### Validation Logic
The code uses the Luhn algorithm which follows these steps:
1. Starting from the check digit (rightmost), iterate to the left
2. Double every second digit (excluding the check digit)
3. If doubling results in a number greater than 9, subtract 9
4. Sum all digits (both doubled and non-doubled)
5. Check if the sum is divisible by 10 (modulo 10 equals 0)

### Functions

#### `validateCred(cards)`
Takes an array of digits representing a credit card number and returns `true` if the number is valid according to the Luhn algorithm, or `false` if invalid.

#### `findInvalidCards(cards)`
Takes a nested array of credit card numbers and returns a new nested array containing only the invalid card numbers.

#### `idInvalidCardCompanies(invalidCards)`
Takes a nested array of invalid credit card numbers and returns an array of companies that issued those invalid cards. The companies are identified based on the first digit:
- 3: American Express (Amex)
- 4: Visa
- 5: Mastercard
- 6: Discover

The function removes duplicates, so each company appears only once in the returned array.

## Sample Usage

```javascript
// Validate a single card
const isValid = validateCred(valid1);
console.log(isValid); // true

// Find all invalid cards in a batch
const invalidCardsList = findInvalidCards(batch);
console.log(invalidCardsList);

// Identify companies with invalid cards
const invalidCompanies = idInvalidCardCompanies(invalidCardsList);
console.log(invalidCompanies); // ['Visa', 'Mastercard', 'Amex', 'Discover']
```

## Technologies Used
- JavaScript
- Node.js

## Project Background
This project was developed as part of the Codecademy Full-stack Engeenier path course to demonstrate understanding of functions, loops, and arrays in JavaScript.