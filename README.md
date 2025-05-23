# Langford Log Backend

This is the Node.js + Express backend server for the **Langford Log App**, which processes time logs submitted by foremen via the React Native frontend. It handles:

- ✅ Receiving log data (form fields + photos)
- ✅ Sending log summary via email to company
- ✅ Accepting up to 10 photo uploads using Multer
- ✅ Hosted on Render for 24/7 public access

---

## 🛠 Tech Stack

- **Express.js** - lightweight API framework
- **Multer** - middleware for handling photo uploads
- **Nodemailer** - used to send log submissions via email
- **Render** - cloud platform hosting the API

---

## 📥 API Endpoint

### `POST /submit-log`

Handles a complete log submission.

#### 🔐 Fields:

| Field             | Type       | Description                         |
|------------------|------------|-------------------------------------|
| `foreman`         | `string`   | Name of the foreman                 |
| `date`            | `string`   | Date in MM/DD/YYYY format           |
| `employees`       | `string`   | JSON stringified array of employees and hours |
| `taskDescription` | `string`   | Brief description of the daily work |
| `photos`          | `file[]`   | Up to 10 image files                |

#### ✅ Example `employees` array:

```json
[
  { "name": "Employee 1", "hours": "8" },
  { "name": "Employee 2", "hours": "6" }
]
```

---

## 🌐 Deployment

The backend is deployed on **Render**:

```
https://langford-log-backend.onrender.com
```

No authentication is currently required.

---

## 🔒 Environment Variables

Set these in your Render environment:

| Name         | Description                        |
|--------------|------------------------------------|
| `EMAIL_USER` | Sender email (e.g. colepuls@me.com)|
| `EMAIL_PASS` | App-specific password or token     |

These are used by Nodemailer for sending log submission emails.

---

## ▶️ Run Locally

```bash
cd backend
npm install
node index.js
```

By default runs on `http://localhost:4000`.

---

## 📂 Folder Structure

```
backend/
├── index.js          # Main API logic
├── package.json      # Dependencies
├── uploads/          # Temporary photo uploads
```

---

## ✅ Future Plans

- [ ] PDF summary email format
- [ ] Store logs in a database (MongoDB or Supabase)
- [ ] Basic API auth for identifying who submitted
- [ ] Admin panel for viewing past logs

---

## 👨‍💻 Author

Made by [Cole Puls](https://github.com/colepuls)  
Contact: [colepuls@me.com](mailto:colepuls@me.com)

---

## 📄 License

MIT License
