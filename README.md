# 🅿️ Parking Space Management API  

A **FastAPI-based backend** to manage parking spaces in a parking lot.  
This API provides endpoints to **list all parking spaces, check empty slots, and update space availability** dynamically.  

---

## ⚒️ Tech Stack  

- 🚀 **FastAPI** – Web framework for building APIs  
- 🐘 **PostgreSQL / MySQL / SQLite** – Database (choose depending on your setup)  
- 🧰 **SQLAlchemy ORM** – For database modeling and queries  
- 📦 **Pydantic** – Data validation and request/response schemas  
- 🐍 **Python 3.9+** – Core language  

---

## ✨ Features  

✅ Get **full list** of parking spaces  
✅ **Update availability** status (`Vacant ↔ Occupied`)  
✅ Filter **empty slots** (with optional level filter)  
✅ Well-structured FastAPI project with dependency injection  
✅ Database integration with SQLAlchemy  

---

## 📂 Project Structure  

```
parking_space_api/
│── main.py                 # FastAPI entrypoint (your code here)
│── models.py               # SQLAlchemy models
│── database.py             # Database connection & Base setup
│── requirements.txt        # Dependencies
│── README.md               # Project documentation
```

---

## ⚙️ Setup & Run  

1. **Clone the repo**  
```bash
git clone https://github.com/your-username/parking-space-api.git
cd parking-space-api
```

2. **Create virtual environment**  
```bash
python -m venv venv
source venv/bin/activate   # Mac/Linux
venv\Scripts\activate      # Windows
```

3. **Install dependencies**  
```bash
pip install -r requirements.txt
```

4. **Setup database**  
- Update connection URL in `database.py`  
- Create tables  
```bash
python
>>> from database import Base, engine
>>> import models
>>> Base.metadata.create_all(bind=engine)
```

5. **Run FastAPI server**  
```bash
uvicorn main:app --reload
```

---

## 🚀 API Endpoints  

### 🔹 Get all parking spaces  
`GET /full_parking_space_list`  
Returns full list of spaces ordered by `space_id`.

---

### 🔹 Update availability of a space  
`PUT /parking_sapce_list/update/{id}`  
- Toggles availability between `Vacant` ↔ `Occupied`.

---

### 🔹 Get empty parking spaces  
`GET /empty_parking_list?level={level}`  
- Returns only **Vacant** slots.  
- Optional query param `level` filters by parking level.  

---

## 📝 Sample Output  

### Example: Get all parking spaces  
```json
[
  {
    "space_id": "A1",
    "Level": 1,
    "Availbility_status": "Vacant"
  },
  {
    "space_id": "A2",
    "Level": 1,
    "Availbility_status": "Occupied"
  }
]
```

### Example: Get empty spaces on Level 1  
`GET /empty_parking_list?level=1`  

```json
[
  {
    "space_id": "A1",
    "Level": 1,
    "Availbility_status": "Vacant"
  }
]
```

### Example: Toggle availability  
`PUT /parking_sapce_list/update/A1`  

```json
{
  "space_id": "A1",
  "Level": 1,
  "Availbility_status": "Occupied"
}
```

---

## 🎯 Future Enhancements  

- 🔑 JWT authentication & user roles  
- 📊 Dashboard with parking stats  
- 📡 WebSocket for real-time space updates  
- 🛠️ Admin panel for managing parking lot  
