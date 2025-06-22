
---

#  VibeCheck_Easy
```markdown


##  Features

- Bun instead of npm as npm is not working in my laptop 
- Express.js to serve HTTP endpoints

##  Sample Vibes Data (in `data/sampleVibes.js`)

```js
[
  {
    id: 1,
    mood: ' ',
    song: ' ',
    user: ' '
  },
]

like this i have taken , three 3 songs from 3 different mmovies
```


###  Start the server

```bash
bun server.js
```

> Server will start on port `5000` and display:
>
> ```
>  Server blasting off on port 5000
> ```

---

##  API Endpoints

### `GET /`

Returns a simple welcome message:
* `GET http://localhost:5000/`
```
 Welcome to VibeCheck API – Check your vibe, share your tribe!
```
![1](https://github.com/user-attachments/assets/860cf6f8-cbf4-46e4-99b5-60a52b368d32)

---

### `GET /api/v1/vibes`
* `GET http://localhost:5000/api/v1/vibes`
Returns a list of all sample vibes in JSON format:

```json
[
  {
    "id": 1,
    "mood": " ",
    "song": " ",
    "user": " "
  },
  ........... SO ON.. end of the list
]
```
![2](https://github.com/user-attachments/assets/c9657056-0b3d-4a91-9349-2e48c08f66c6)

---

### `GET /api/v1/vibes/:id`
* `GET http://localhost:5000/api/v1/vibes/1`
Returns a single vibe matching the provided ID.

**Example:**

`GET /api/v1/vibes/2`

```json
{
  "id":  ,
  "mood": "_",
  "song": "_",
  "user": "_"
}
```
![3](https://github.com/user-attachments/assets/487d53b3-c14b-4ea8-8313-90bc7bb6c8cd)

If the ID is not found:
* `GET http://localhost:5000/api/v1/vibes/99` (not found)
```json
{
  "success": false,
  "message": "That vibe is off the grid, not found."
}
```
![4](https://github.com/user-attachments/assets/952abfd3-d0cb-465a-b1b0-8aac24711ab9)

---


#  VibeCheck_Advanced 

```markdown



##  Features

-  User Signup and Login (JWT-based Auth)
-  Password hashing with bcrypt
-  Protected routes for vibe posting
-  Public feed showing all vibes with user info
-  MongoDB Atlas for cloud storage

##  Project Structure


vibecheck-api/
├── config/             # MongoDB connection
├── controllers/        # Logic for auth & vibe handling
├── middleware/         # Authentication middleware
├── models/             # User and Vibe Mongoose schemas
├── routes/             # API route definitions
├── .env                # Environment variables (local only)
├── server.js           # Entry point
├── package.json        # Project config

````

---

##  Steps to finish

### 1. Setup `.env`

Create a `.env` file in the root directory:

```env
PORT=5000
MONGO_URI=your_mongo_connection_string
JWT_SECRET=your_secret_key
JWT_EXPIRE=30d
```

>  Never commit this file to Git!

### 2. Start the Server

```bash
node server.js
```

You should see:

```
 Server blasting off on port 5000
MongoDB Connected: <your_host>
```

---

##  API Endpoints & Postman Test Flow

### 1️ Signup Endpoint

**POST** `http://localhost:5000/api/v1/auth/signup`

**Body (JSON):**

```json
{
  "username": "kowshik",
  "email": "kowshik@example.com",
  "password": "123456"
}
```
![1](https://github.com/user-attachments/assets/b31a4133-12ef-4563-8e16-fb1371d3c63b)

---

### 2️ Login Endpoint *(save the JWT token)*

**POST** `http://localhost:5000/api/v1/auth/login`

**Body (JSON):**

```json
{
  "email": "kowshik@example.com",
  "password": "123456"
}
```
![2](https://github.com/user-attachments/assets/b8f62945-d1ee-4982-af9f-fe086b6b4bb2)

---

### 3️ Post Vibe (Unauthorized - should fail)

**POST** `http://localhost:5000/api/v1/vibes`

**Body (JSON):**

```json
{
  "mood": "energetic",
  "song": "jai balayya"
}
```
![3](https://github.com/user-attachments/assets/a4d4635e-9e85-437c-b9e7-d23614e981bc)
---

### 4️ Post Vibe (Authorized - should succeed)

**POST** `http://localhost:5000/api/v1/vibes`

**Headers:**

```
Authorization: Bearer <MY_JWT_TOKEN>
```

**Body (JSON):**

```json
{
  "mood": ".....",
  "song": "......"
}
```
![4](https://github.com/user-attachments/assets/3625e6c9-bcf8-4308-b834-b321ceb14a3d)


---

### 5️ Get All Vibes

**GET** `http://localhost:5000/api/v1/vibes`
![5](https://github.com/user-attachments/assets/0e04d155-d16f-4189-9375-90b70065b91a)


---

### 6.Check the data in mongodb
![6](https://github.com/user-attachments/assets/3bcf716e-000a-43a4-8d62-57c39523602d)

---

