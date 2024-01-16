# Solana Review Program

## Overview

The Solana Review Program is a decentralized application (DApp) built on the Solana blockchain that allows users to create and manage reviews for various entities. This smart contract enables users to add new reviews or update existing ones in a secure and decentralized manner.

## Functionality

### 1. Add Review

Users can add new reviews to the system by providing details such as the review title, rating, description, and location. Each review is associated with a unique program-derived account (PDA) on the Solana blockchain.

### 2. Update Review

Existing reviews can be updated by the original reviewer. Users can modify the rating, description, and location of their reviews.

### 3. Smart Contract Security

The smart contract employs Solana's program-derived address (PDA) mechanism for creating unique accounts associated with each review. This ensures that reviews are stored securely and can only be modified by the original reviewer.

### 4. Rating Validation

The program includes validation to ensure that the rating provided in a review falls within a valid range (1 to 10). This helps maintain the integrity of the rating system.

## How to Use

1. **Add a New Review:**
   - Call the `add_review` function, providing the required parameters (title, rating, description, location).
   - The smart contract creates a new PDA associated with the review and stores the review details securely.

2. **Update an Existing Review:**
   - Call the `update_review` function, providing the required parameters (title, rating, description, location).
   - The smart contract verifies the ownership of the review and updates the specified details.

## Building and Deploying

To deploy this Solana program:

1. Clone the repository.
2. Install the required dependencies.
3. Build the program using the Solana development tools.
4. Deploy the program to the Solana blockchain.

Ensure that you have Solana CLI and Rust installed on your system. Detailed instructions for building and deploying Solana programs can be found in the Solana documentation.

## Example

```rust
// Example usage in a Solana program client

// Add a new review
let title = "Great Restaurant".to_string();
let rating = 5;
let description = "Wonderful dining experience.".to_string();
let location = "123 Main St".to_string();

let instruction = ReviewInstruction::AddReview {
    title,
    rating,
    description,
    location,
};

// Call the smart contract
invoke_signed(&add_review_instruction, &account_infos, &[&signer_seeds])?;

// Update an existing review
let updated_rating = 4;
let updated_description = "Good food, but service could improve.".to_string();
let updated_location = "456 Oak St".to_string();

let update_instruction = ReviewInstruction::UpdateReview {
    title,
    rating: updated_rating,
    description: updated_description,
    location: updated_location,
};

// Call the smart contract
invoke_signed(&update_review_instruction, &account_infos, &[&signer_seeds])?;
```

## License

This Solana Review Program is distributed under the MIT License. See the `LICENSE` file for more details.
