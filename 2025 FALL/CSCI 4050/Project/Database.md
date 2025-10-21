**We currently have:**

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
- password_reset_token
- password_reset_token_expires_at

movies:
- movie_id
- title
- status: NOW_PLAYING | UPCOMING
- genres
- rating
- release_date
- synopsis
- trailer_link
- poster_link
- cast_names
- directors
- producers

payment_info:
- payment_info_id
- user_id
- card_number
- billing_address
- expiration_date
- cardholder_name

bookings:
- booking_id
- user_id
- payment_id
- movie_id
- promotion_id
- num_tickets

promotions:
- promotion_id
- promo_code

show_dates:
- show_date_id
- movie_id
- show_date

show_times:
- show_time_id
- show_date_id
- start_time
- end_time

show_rooms:
- show_room_id
- num_seats

tickets:
- ticket_id
- booking_id
- tic_type

**I want to modify to existing tables or add the following:**

address:
- address_id
- user_id
- street
- state
- country
- zip
- type: home | billing

admin:
- admin_id
- email
- password

user:
- user_id
- address_id: address ('home')
- email
- phone_number
- first_name
- last_name
- status: user_status ('suspended' | 'active' | 'inactive')
- password
- phone_number
- verification_token
- verification_token_expires_at
- password_reset_token
- password_reset_token_expires_at
- profile_image_link

user_status:
- user_status_id
- status: 'suspended' | 'active' | 'inactive'

movie:
- movie_id
- title
- status: movie_type (EXPIRED | NOW_PLAYING | UPCOMING)
- genres
- rating
- release_date
- synopsis
- trailer_link
- poster_link
- cast_names
- directors
- producers

movie_type:
- movie_type_id:
- type: EXPIRED | NOW_PLAYING | UPCOMING

booking:
- booking_id
- user_id
- payment_id
- movie_id
- promotion_id
- ... what else?

payment_card:
- payment_id
- user_id
- address_id: billing
- card_number
- cardholder_name
- default: true/false

payment_card_type:
- payment_card_type_id:
- type: 'Visa' | 'MasterCard' | 'AmericanExpress' | ''

promotion:
- promo_id
- title
- discount
- description
- image_link

movie_show:
- movie_show_id
- movie_id
- show_room_id
- 

show_room:
- show_room_id
- name
- capacity

show_date:
- show_date_id
- show_date
- (shouldn't include movie_id since thats bad database practice, right?)

show_time:
- show_time_id
- show_date_id
- start_time
- end_time

ticket:
- ticket_id
- booking_id
- type:  ticket_type

ticket_type:
- ticket_type_id
- seat_id:
- child
- adult
- senior

show_seat:
- show_seat_id:

**Notes/Questions:**
- we want to include separate type classes if we can to practice decoupling?
- for the option during registration "enroll for payments," do i have that as a field in users table or payment_card table?
- how should we deal with considering what is considered now_playing or upcoming?

