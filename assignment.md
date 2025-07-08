# Assignment

## Brief

Create an ERD for each of the following case study question.

## Instructions

Paste the answer as DBML in the answer code section below each question.

### Question 1

Construct an ERD for a social media company whose database includes information about users, their followers, and the posts that they make. Users can follow multiple users and create multiple posts.

Each entity has the following attributes:

- User: id, username, email, created_at
- Post: id, title, body, user_id, status, created_at
- Follows: following_user_id, followed_user_id, created_at

Answer:

```dbml
Table users {
  id int [pk, increment]
  username varchar
  email varchar
  created_at datetime
}

Table posts {
  id int [pk, increment]
  title varchar
  body text
  user_id int [ref: > users.id]
  status varchar
  created_at datetime
}

Table follows {
  following_user_id int [ref: > users.id]
  followed_user_id int [ref: > users.id]
  created_at datetime

  Indexes {
    (following_user_id, followed_user_id) [unique]
  }
}
```

### Question 2

Construct an ERD for a company that sells books online. The company has a website where customers can browse available books and add them to their shopping carts. Each cart can contain multiple books.

There are 4 entities, think of what attributes each entity should have.

- Customer
- Book
- Cart
- CartItem

Answer:

```dbml
Table customers {
  id int [pk, increment]
  name varchar
  email varchar
  created_at datetime
}

Table books {
  id int [pk, increment]
  title varchar
  author varchar
  price decimal
  isbn varchar
  published_date date
}

Table carts {
  id int [pk, increment]
  customer_id int [ref: > customers.id]
  created_at datetime
  status varchar
}

Table cart_items {
  id int [pk, increment]
  cart_id int [ref: > carts.id]
  book_id int [ref: > books.id]
  quantity int
  added_at datetime

  Indexes {
    (cart_id, book_id) [unique]
  }
}

```

## Submission

- Submit the URL of the GitHub Repository that contains your work to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
