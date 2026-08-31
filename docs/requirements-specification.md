# StudySwap - Requirements Specification

## 1. Introduction

### 1.1 Purpose

This document defines the functional and non-functional requirements for the StudySwap website.

StudySwap is a student marketplace that allows university students to buy, sell, and exchange used textbooks, notes, and study materials.

### 1.2 Target Users

The system is designed for university students, especially students from Year 1 to Year 4.

### 1.3 Main Objective

The main objective is to provide students with a simple, organized, and trustworthy platform for exchanging study materials.

---

# 2. Functional Requirements

## FR-01: User Registration

The system shall allow a new student to create an account.

The registration form should include:

- Student name
- Email
- Password
- University information
- Student ID or verification information

The system shall validate required information before creating the account.

## FR-02: User Login

The system shall allow registered users to log in using their account credentials.

The system shall reject incorrect login information.

## FR-03: User Logout

The system shall allow users to securely log out of their account.

## FR-04: User Profile

The system shall allow users to:

- View their profile.
- Edit profile information.
- View their listings.
- View their ratings and reviews.

## FR-05: Student Verification

The system shall provide a student verification process.

Verified users should be identifiable as verified students.

## FR-06: Create Listing

A logged-in user shall be able to create a listing for a study material.

A listing should contain:

- Title
- Description
- Category
- Course/subject
- Price
- Condition
- Image
- Sale or exchange option

## FR-07: Edit Listing

The owner of a listing shall be able to edit listing information.

## FR-08: Delete Listing

The owner of a listing shall be able to remove their listing.

## FR-09: View Listings

Users shall be able to view available study-material listings.

Each listing should display:

- Title
- Image
- Price
- Condition
- Seller
- Course/subject
- Listing status

## FR-10: Search

The system shall allow users to search for study materials using keywords.

## FR-11: Filter

The system shall allow users to filter listings by:

- Category
- Course
- Price
- Condition
- Sale/exchange type

## FR-12: Listing Details

The system shall provide a detailed page for each listing.

The detail page shall display the complete listing information and seller information.

## FR-13: Contact Seller

A logged-in buyer shall be able to contact the seller through the website.

Users can discuss:

- Price
- Book condition
- Availability
- Exchange arrangements
- Meeting location

## FR-14: Purchase/Exchange Request

A buyer shall be able to express interest in purchasing or exchanging an item.

The seller shall be able to accept or reject the request.

## FR-15: Listing Status

A seller shall be able to mark a listing as:

- Available
- Reserved
- Sold
- Exchanged

## FR-16: Rating and Review

After a transaction or exchange, users shall be able to rate and review each other.

The system shall store the rating and review.

## FR-17: My Listings

Users shall be able to view all listings they have created.

## FR-18: Transaction History

The system should store completed transactions or exchanges between users.

Users should be able to view their transaction history.

---

# 3. Non-Functional Requirements

## NFR-01: Usability

The website should have a simple and easy-to-understand interface.

A university student should be able to find a textbook without extensive instructions.

## NFR-02: Performance

The website should load normal pages within a reasonable amount of time.

Search results should be returned quickly.

## NFR-03: Security

The system shall protect user account information.

Passwords shall not be stored as plain text.

Users shall only be allowed to edit or delete their own listings.

## NFR-04: Reliability

The system should correctly store user, listing, and transaction information.

## NFR-05: Availability

The website should be accessible to users through a standard web browser.

## NFR-06: Compatibility

The website should work with modern browsers such as:

- Google Chrome
- Microsoft Edge
- Mozilla Firefox
- Safari

## NFR-07: Maintainability

The source code should be organized into clear components so that future developers can modify and extend the system.

## NFR-08: Scalability

The system should be designed so that future features such as mobile applications, AI recommendations, online payments, and delivery services can be added.

---

# 4. Data Requirements

The system should store information about:

- Users
- Student verification
- Listings
- Categories
- Courses
- Messages
- Transactions
- Ratings
- Reviews

---

# 5. User Roles

## Student

A student can:

- Register
- Login
- Manage profile
- Search listings
- Create listings
- Edit their listings
- Delete their listings
- Contact sellers
- Buy/exchange materials
- Rate other users

## Administrator

An administrator can:

- Manage users
- Manage listings
- Manage reported content
- Manage categories
- Monitor the platform
- Remove inappropriate listings or accounts
