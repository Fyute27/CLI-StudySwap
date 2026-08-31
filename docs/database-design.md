# StudySwap - Database Design

## 1. Database Overview

The StudySwap database stores information required to operate the student marketplace.

The database manages:

- Student accounts
- Student verification
- Study-material listings
- Categories
- Courses
- Messages
- Transactions
- Ratings
- Reviews

---

# 2. Entity Relationship Overview

The main relationships are:

```text
USER
 |
 | 1
 |
 |----< LISTING
 |
 |----< MESSAGE
 |
 |----< TRANSACTION
 |
 |----< RATING


LISTING
 |
 |----< MESSAGE
 |
 |----< TRANSACTION
 |
 |---- CATEGORY
 |
 |---- COURSE


TRANSACTION
 |
 |----< RATING
```

---

# 3. Entity Definitions

## 3.1 User

This table stores student account information.

| Field Name | Data Type | Description |
| --- | --- | --- |
| user_id | INT / UUID | Primary key |
| full_name | VARCHAR | User full name |
| email | VARCHAR | Unique email address |
| password_hash | VARCHAR | Hashed password |
| university | VARCHAR | University name |
| student_id | VARCHAR | Student identification number |
| verification_status | BOOLEAN | Indicates whether the user is verified |
| created_at | DATETIME | Account creation date |
| updated_at | DATETIME | Last profile update |

### Relationships
- One user can create many listings.
- One user can send many messages.
- One user can participate in many transactions.
- One user can receive many ratings.

## 3.2 Verification

This table stores status and evidence of student verification.

| Field Name | Data Type | Description |
| --- | --- | --- |
| verification_id | INT / UUID | Primary key |
| user_id | INT / UUID | Foreign key to User |
| verification_type | VARCHAR | Student ID, email, or university proof |
| verification_document | VARCHAR | File or reference to uploaded proof |
| status | VARCHAR | Pending, approved, rejected |
| reviewed_by | INT / UUID | Admin handling the verification |
| created_at | DATETIME | Verification request date |
| reviewed_at | DATETIME | Date reviewed |

### Relationships
- Each verification record belongs to one user.

## 3.3 Listing

This table stores details related to posted study materials.

| Field Name | Data Type | Description |
| --- | --- | --- |
| listing_id | INT / UUID | Primary key |
| user_id | INT / UUID | Seller who created the listing |
| category_id | INT / UUID | Foreign key to Category |
| course_id | INT / UUID | Foreign key to Course |
| title | VARCHAR | Listing title |
| description | TEXT | Product or material description |
| price | DECIMAL | Listing price |
| condition | VARCHAR | New, good, used, damaged |
| listing_type | VARCHAR | Sale or exchange |
| image_url | VARCHAR | Image file reference |
| status | VARCHAR | Available, reserved, sold, exchanged |
| created_at | DATETIME | Listing creation date |
| updated_at | DATETIME | Last update date |

### Relationships
- Many listings belong to one user.
- Each listing belongs to one category.
- Each listing belongs to one course.
- A listing may have many messages and transactions.

## 3.4 Category

This table stores listing categories.

| Field Name | Data Type | Description |
| --- | --- | --- |
| category_id | INT / UUID | Primary key |
| category_name | VARCHAR | Example: textbook, notes, lab manual |
| description | TEXT | Category description |

### Relationships
- One category can be assigned to many listings.

## 3.5 Course

This table stores academic course information.

| Field Name | Data Type | Description |
| --- | --- | --- |
| course_id | INT / UUID | Primary key |
| course_code | VARCHAR | Course code such as CS101 |
| course_name | VARCHAR | Full course name |
| department | VARCHAR | Department or faculty |

### Relationships
- One course can be associated with many listings.

## 3.6 Message

This table stores messages between buyers and sellers.

| Field Name | Data Type | Description |
| --- | --- | --- |
| message_id | INT / UUID | Primary key |
| sender_id | INT / UUID | User sending the message |
| receiver_id | INT / UUID | User receiving the message |
| listing_id | INT / UUID | Related listing |
| message_text | TEXT | Message content |
| sent_at | DATETIME | Date and time sent |

### Relationships
- A message belongs to one sender and one receiver.
- A message can reference one listing.

## 3.7 Transaction

This table stores completed or active purchase/exchange transactions.

| Field Name | Data Type | Description |
| --- | --- | --- |
| transaction_id | INT / UUID | Primary key |
| listing_id | INT / UUID | Related listing |
| buyer_id | INT / UUID | User purchasing or exchanging |
| seller_id | INT / UUID | User selling the item |
| transaction_type | VARCHAR | Sale or exchange |
| status | VARCHAR | Pending, accepted, rejected, completed |
| created_at | DATETIME | Transaction creation date |
| updated_at | DATETIME | Last status update |

### Relationships
- One listing can have many transactions.
- One buyer and one seller participate in each transaction.
- A transaction may produce one rating.

## 3.8 Rating

This table stores ratings given after completed transactions.

| Field Name | Data Type | Description |
| --- | --- | --- |
| rating_id | INT / UUID | Primary key |
| transaction_id | INT / UUID | Related transaction |
| reviewer_id | INT / UUID | User who leaves the rating |
| rated_user_id | INT / UUID | User being rated |
| rating_value | INT | Rating score, usually 1-5 |
| review_text | TEXT | Additional written feedback |
| created_at | DATETIME | Rating date |

### Relationships
- One transaction can have one rating.
- One reviewer rates one user.

## 3.9 Review

This table stores review information separately from ratings if needed.

| Field Name | Data Type | Description |
| --- | --- | --- |
| review_id | INT / UUID | Primary key |
| user_id | INT / UUID | User who receives the review |
| reviewer_id | INT / UUID | User leaving the review |
| listing_id | INT / UUID | Related listing |
| review_text | TEXT | Review content |
| created_at | DATETIME | Review creation date |

### Relationships
- Each review belongs to one user and one reviewer.
- A review may be linked to a listing.

---

# 4. Relationships Summary

## One-to-Many Relationships
- One user can have many listings.
- One user can have many messages sent.
- One user can have many transactions.
- One listing can have many messages.
- One listing can have many transactions.
- One category can have many listings.
- One course can have many listings.
- One user can have many ratings received.

## One-to-One Relationships
- One user can have one verification record at a time.
- One transaction can have one rating.

---

# 5. Suggested Database Schema (SQL Example)

```sql
CREATE TABLE users (
    user_id INT PRIMARY KEY AUTO_INCREMENT,
    full_name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    university VARCHAR(255),
    student_id VARCHAR(100),
    verification_status BOOLEAN DEFAULT FALSE,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE verifications (
    verification_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    verification_type VARCHAR(100),
    verification_document VARCHAR(255),
    status VARCHAR(50) DEFAULT 'pending',
    reviewed_by INT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    reviewed_at DATETIME,
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

CREATE TABLE categories (
    category_id INT PRIMARY KEY AUTO_INCREMENT,
    category_name VARCHAR(100) NOT NULL,
    description TEXT
);

CREATE TABLE courses (
    course_id INT PRIMARY KEY AUTO_INCREMENT,
    course_code VARCHAR(50) NOT NULL,
    course_name VARCHAR(255) NOT NULL,
    department VARCHAR(255)
);

CREATE TABLE listings (
    listing_id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT NOT NULL,
    category_id INT,
    course_id INT,
    title VARCHAR(255) NOT NULL,
    description TEXT NOT NULL,
    price DECIMAL(10,2),
    condition VARCHAR(50),
    listing_type VARCHAR(50),
    image_url VARCHAR(255),
    status VARCHAR(50) DEFAULT 'available',
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(user_id),
    FOREIGN KEY (category_id) REFERENCES categories(category_id),
    FOREIGN KEY (course_id) REFERENCES courses(course_id)
);

CREATE TABLE messages (
    message_id INT PRIMARY KEY AUTO_INCREMENT,
    sender_id INT NOT NULL,
    receiver_id INT NOT NULL,
    listing_id INT,
    message_text TEXT NOT NULL,
    sent_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (sender_id) REFERENCES users(user_id),
    FOREIGN KEY (receiver_id) REFERENCES users(user_id),
    FOREIGN KEY (listing_id) REFERENCES listings(listing_id)
);

CREATE TABLE transactions (
    transaction_id INT PRIMARY KEY AUTO_INCREMENT,
    listing_id INT NOT NULL,
    buyer_id INT NOT NULL,
    seller_id INT NOT NULL,
    transaction_type VARCHAR(50),
    status VARCHAR(50) DEFAULT 'pending',
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    updated_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (listing_id) REFERENCES listings(listing_id),
    FOREIGN KEY (buyer_id) REFERENCES users(user_id),
    FOREIGN KEY (seller_id) REFERENCES users(user_id)
);

CREATE TABLE ratings (
    rating_id INT PRIMARY KEY AUTO_INCREMENT,
    transaction_id INT NOT NULL,
    reviewer_id INT NOT NULL,
    rated_user_id INT NOT NULL,
    rating_value INT CHECK (rating_value BETWEEN 1 AND 5),
    review_text TEXT,
    created_at DATETIME DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (transaction_id) REFERENCES transactions(transaction_id),
    FOREIGN KEY (reviewer_id) REFERENCES users(user_id),
    FOREIGN KEY (rated_user_id) REFERENCES users(user_id)
);
``` 

---

# 6. Data Integrity Considerations

- Email addresses should be unique.
- Passwords should be stored only as hash values.
- Listings should not be deleted without checking active transactions.
- Transactions should be validated to ensure buyer and seller are different users.
- Listing status should be restricted to valid values such as available, reserved, sold, and exchanged.
- Ratings should be limited to valid score ranges.

---

# 7. Assumptions

- A user may create multiple listings.
- A student may buy, sell, or exchange more than one item.
- Each transaction may result in a rating.
- Categories and courses are stored separately to support search and filtering.
- Message communication is tracked per listing to maintain context.
