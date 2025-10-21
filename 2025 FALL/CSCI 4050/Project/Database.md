**I currently have:**

users:
- id
- address (should be 'street')
- country
- email
- first_name
- is_active (registered or unregistered, registered whenever clicking verification link)
- last_name
- password
- phone_number
- state
- verification_token
- verification_token_expires_at

bookings:
- 

promotions:
- promotion_id
- promo_code

**I want to modify to or add:**

users:
- id
- address (should be 'street')
- first_name
- status: active | inactive | suspended
- last_name
- password
- phone_number
- verification_token
- verification_token_expires_at
- profile_image_link

address:
- address_id
- user_id
- street
- state
- country
- zip
- type: home | billing

payment_card:
- payment_id
- user_id
- card_number
- 
- cardholder_name
- default: true/false

promotions:
- promo_id
- title
- discount
- description
- image_link

**Notes:**
- i want to include an address class separately to practice mvc and decoupling and database normalization.
- for the option during registration "enroll for payments," do i have that as a field in users table or payment_card table
- 