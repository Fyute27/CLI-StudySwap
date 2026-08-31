# StudySwap - Acceptance Criteria

## 1. User Registration

### Feature
Student registration.

### Acceptance Criteria

- [ ] A student can open the registration page.
- [ ] The student can enter required registration information.
- [ ] The system validates required fields.
- [ ] The system prevents registration with an already-used email.
- [ ] A valid student account can be created successfully.
- [ ] The user receives confirmation that registration was successful.

---

## 2. User Login

### Feature
Student login.

### Acceptance Criteria

- [ ] A registered user can enter their email and password.
- [ ] Correct credentials allow the user to log in.
- [ ] Incorrect credentials are rejected.
- [ ] An appropriate error message is displayed for invalid credentials.
- [ ] The user is redirected to the appropriate page after successful login.

---

## 3. User Profile

### Feature
Profile management.

### Acceptance Criteria

- [ ] A logged-in user can view their profile.
- [ ] A user can edit allowed profile information.
- [ ] Updated information is saved correctly.
- [ ] A user cannot modify another user's profile.

---

## 4. Student Verification

### Feature
Student verification.

### Acceptance Criteria

- [ ] A student can submit required verification information.
- [ ] The system stores the verification status.
- [ ] A verified student is clearly identified.
- [ ] Unverified users cannot falsely display themselves as verified.

---

## 5. Create Listing

### Feature
Create a textbook or study-material listing.

### Acceptance Criteria

- [ ] A logged-in student can create a listing.
- [ ] The listing requires a title.
- [ ] The listing requires a description.
- [ ] The listing includes a price or exchange option.
- [ ] The listing includes a condition.
- [ ] The listing includes a category or course.
- [ ] The listing can include an image.
- [ ] A valid listing is saved in the database.
- [ ] The new listing appears in the marketplace.

---

## 6. Edit Listing

### Feature
Edit an existing listing.

### Acceptance Criteria

- [ ] The listing owner can edit their listing.
- [ ] Updated information is saved.
- [ ] Changes are visible when viewing the listing.
- [ ] A user cannot edit another user's listing.

---

## 7. Delete Listing

### Feature
Delete a listing.

### Acceptance Criteria

- [ ] The listing owner can delete their listing.
- [ ] The system asks for confirmation before deletion.
- [ ] Deleted listings no longer appear as available listings.
- [ ] A user cannot delete another user's listing.

---

## 8. Search

### Feature
Search for study materials.

### Acceptance Criteria

- [ ] Users can enter a search keyword.
- [ ] The system returns matching listings.
- [ ] Search results display relevant information.
- [ ] The system displays an appropriate message when no results are found.

---

## 9. Filter

### Feature
Filter study-material listings.

### Acceptance Criteria

- [ ] Users can filter listings by category.
- [ ] Users can filter listings by course.
- [ ] Users can filter by price.
- [ ] Users can filter by condition.
- [ ] Users can filter by sale or exchange.
- [ ] Results update according to the selected filters.

---

## 10. Listing Details

### Feature
View listing details.

### Acceptance Criteria

- [ ] Users can select a listing.
- [ ] The system displays the complete listing information.
- [ ] The seller information is displayed.
- [ ] The listing status is displayed.
- [ ] The buyer can access the contact seller option.

---

## 11. Contact Seller

### Feature
Chat or messaging between students.

### Acceptance Criteria

- [ ] A logged-in buyer can contact a seller.
- [ ] The buyer can send a message.
- [ ] The seller can receive the message.
- [ ] The seller can reply.
- [ ] Messages are associated with the correct users and listing.

---

## 12. Purchase or Exchange Request

### Feature
Request to purchase or exchange an item.

### Acceptance Criteria

- [ ] A buyer can send a purchase or exchange request.
- [ ] The seller can view the request.
- [ ] The seller can accept or reject the request.
- [ ] The request status is stored.
- [ ] The listing status is updated when appropriate.

---

## 13. Listing Status

### Feature
Manage listing availability.

### Acceptance Criteria

- [ ] A seller can mark a listing as available.
- [ ] A seller can mark a listing as reserved.
- [ ] A seller can mark a listing as sold.
- [ ] A seller can mark a listing as exchanged.
- [ ] The status is visible to users.

---

## 14. Rating and Review

### Feature
Rate and review another student.

### Acceptance Criteria

- [ ] A completed transaction allows users to submit a rating.
- [ ] The rating must be within the allowed rating range.
- [ ] A user can submit a written review.
- [ ] The rating and review are stored.
- [ ] Ratings are displayed on the appropriate user profile.

---

## 15. Transaction History

### Feature
View transaction history.

### Acceptance Criteria

- [ ] Users can view their completed transactions.
- [ ] Transaction information includes the relevant listing.
- [ ] Transaction information includes the other user.
- [ ] Transaction status is displayed correctly.

---

## 16. Security

### Feature
Protect user accounts and data.

### Acceptance Criteria

- [ ] Passwords are not stored as plain text.
- [ ] Users must authenticate before accessing protected features.
- [ ] Users cannot edit other users' listings.
- [ ] Users cannot delete other users' listings.
- [ ] Unauthorized users cannot access protected account information.
