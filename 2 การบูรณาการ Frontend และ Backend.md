### 🌟 **การบูรณาการ Frontend และ Backend**  

📚 **หัวข้อสัปดาห์ที่ 6:**  
- การเชื่อมต่อ API กับ React  
- การจัดการ State (State Management)  
- การสร้างแอปที่สมบูรณ์จากการบูรณาการ Frontend และ Backend  

---

### 🚀 **1. การเชื่อมต่อ Backend (API Integration)**
**เป้าหมาย:** เพิ่มฟีเจอร์ที่ดึงและส่งข้อมูลไปยัง Backend จริง

#### 🏗 **Backend API ที่ควรเพิ่ม:**
- **GET** `/api/users`: ดึงข้อมูลผู้ใช้ทั้งหมด  
- **POST** `/api/users`: เพิ่มผู้ใช้ใหม่  
- **DELETE** `/api/users/:id`: ลบผู้ใช้  

#### 🔌 **การเชื่อมต่อ React กับ API:**
- ติดตั้ง **json-server** เพื่อจำลอง Backend:  
  ```bash
  npm install json-server --save-dev
  ```
- สร้าง `db.json`:
  ```json
  {
    "users": [
      { "id": 1, "name": "John Doe", "age": 25 },
      { "id": 2, "name": "Jane Smith", "age": 30 }
    ]
  }
  ```
- รัน json-server:
  ```bash
  npx json-server --watch db.json --port 5000
  ```

---

### 🎨 **2. เพิ่มหน้า User Management Page**  
**URL:** `/users`

#### 🧩 **โครงสร้างหน้า:**
```plaintext
<UsersPage>
 ├── <Header title="จัดการผู้ใช้" />
 ├── <UserList />          // แสดงรายชื่อผู้ใช้
 ├── <UserForm />          // แบบฟอร์มเพิ่มผู้ใช้ใหม่
 └── <Loader />            // แสดงสถานะ loading ขณะดึงข้อมูล
```

#### 📡 **ตัวอย่างโค้ดเชื่อมต่อ API:**
```javascript
import axios from 'axios';
import { useQuery, useMutation, useQueryClient } from '@tanstack/react-query';

function UserList() {
  const { data, isLoading } = useQuery(['users'], async () => {
    const response = await axios.get('http://localhost:5000/users');
    return response.data;
  });

  if (isLoading) return <p>กำลังโหลดข้อมูล...</p>;

  return (
    <ul>
      {data.map((user) => (
        <li key={user.id}>{user.name} - อายุ {user.age}</li>
      ))}
    </ul>
  );
}
```

---

### 💾 **3. การจัดการ State ด้วย React Query + Redux**  
- **React Query:** ใช้สำหรับการดึงข้อมูลและ sync กับ backend  
- **Redux:** ใช้จัดการ state ภายในแอป เช่น การแจ้งเตือน, user session

#### 🛠 **เพิ่ม slice ใน Redux:**
```javascript
const userSlice = createSlice({
  name: 'users',
  initialState: [],
  reducers: {
    setUsers: (state, action) => action.payload
  }
});
```

---

### 🌐 **4. การนำ Routing เพิ่มเติม**  
- ปรับเส้นทางใน `App.jsx`:
```jsx
<Link to="/users">Users</Link>
<Route path="/users" element={<UsersPage />} />
```

---

### 🌟 **5. ฟีเจอร์เพิ่มเติม (Optional)**
- ✅ **Search:** เพิ่มการค้นหาผู้ใช้แบบเรียลไทม์  
- ✅ **Pagination:** แบ่งหน้ารายชื่อผู้ใช้  
- ✅ **Optimistic UI:** อัปเดต UI ทันทีเมื่อมีการเพิ่มหรือลบข้อมูล  
- ✅ **Form Validation:** ตรวจสอบข้อมูลก่อนส่ง

---

### 🎯 **6. เชื่อมโยงกับหัวข้อสัปดาห์ที่ 6:**
| 💡 **หัวข้อ**              | 🎬 **ฟีเจอร์ที่สอดคล้อง**              |
|-------------------------|--------------------------------------|
| เชื่อมต่อ API กับ React   | การใช้ **axios** และ **React Query** ใน `UserList` |
| การจัดการ State           | การใช้ **Redux** และ **React Query** ร่วมกัน |
| การสร้างแอปสมบูรณ์       | มี **Frontend** (React), **Backend** (json-server), และการจัดการ routing แบบครบวงจร |

---

### 🌈 **7. สรุปแนวทางการขยายแอป**  
✅ นักศึกษาจะได้ฝึก **API Integration** กับ React  
✅ ได้สัมผัสการจัดการ **State Management** ทั้งฝั่ง Client และ Server  
✅ ได้สร้าง **SPA** ที่สามารถเพิ่ม/ลบข้อมูลได้แบบเรียลไทม์  

---
