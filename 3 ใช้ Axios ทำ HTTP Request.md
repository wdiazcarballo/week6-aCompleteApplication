### 🚀 **สอนการใช้ Axios ในโปรเจกต์ Express-API **

จากโค้ดที่นักศึกษามีตอนนี้ เป็น **Back-end API** ที่พัฒนาโดยใช้ **Express.js** เชื่อมต่อกับ **MongoDB** ผ่าน **Mongoose** ซึ่งสามารถเพิ่มและดึงข้อมูลสินค้า (**Products**) ได้ผ่านเส้นทาง `/api/products`  

---

### 🌐 **1. Axios คืออะไร?**  
- ✅ **Axios** คือ **ไลบรารีสำหรับทำ HTTP Request** (เช่น GET, POST, PUT, DELETE)  
- 🚀 ช่วยให้ **React** หรือ **JavaScript ฝั่ง Client** เรียกใช้งาน API ได้ง่ายขึ้น  
- 🔒 **รองรับ Promise** และสามารถ **จัดการ Error** ได้ดี  
- 🌍 สามารถดึงข้อมูลจาก Back-end (**Express API**) ที่นักศึกษาสร้างขึ้นมา

---

### 🔧 **2. ติดตั้ง Axios**  
ให้รันคำสั่งนี้ใน **โฟลเดอร์โปรเจกต์**:  
```bash
npm install axios
```

---

### 🎯 **3. ตัวอย่างการใช้งาน Axios กับโปรเจกต์นี้**  

#### 🏃 **3.1 ดึงข้อมูลสินค้าทั้งหมด (GET Request)**  
📌 **เชื่อมต่อกับเส้นทาง** `/api/products` ที่กำหนดใน `productRoutes.js`

```javascript
import axios from 'axios';
import React, { useEffect, useState } from 'react';

function ProductList() {
  const [products, setProducts] = useState([]);

  // 🔄 ดึงข้อมูลเมื่อคอมโพเนนต์ถูกโหลด
  useEffect(() => {
    axios.get('http://localhost:5000/api/products')
      .then((response) => {
        setProducts(response.data);
      })
      .catch((error) => {
        console.error('❌ เกิดข้อผิดพลาดในการดึงข้อมูล:', error);
      });
  }, []);

  return (
    <div>
      <h2>📦 รายการสินค้า</h2>
      <ul>
        {products.map((product) => (
          <li key={product._id}>
            🛍 {product.name} - 💰 {product.price} บาท
          </li>
        ))}
      </ul>
    </div>
  );
}

export default ProductList;
```

---

#### ✍️ **3.2 เพิ่มสินค้าใหม่ (POST Request)**  
📌 **เรียกใช้งาน** `/api/products` ด้วย **POST**

```javascript
import axios from 'axios';
import React, { useState } from 'react';

function AddProduct() {
  const [name, setName] = useState('');
  const [price, setPrice] = useState('');

  const handleSubmit = async (e) => {
    e.preventDefault();
    try {
      const newProduct = { name, price: parseFloat(price) };
      const response = await axios.post('http://localhost:5000/api/products', newProduct);
      alert(`✅ เพิ่มสินค้า ${response.data.name} สำเร็จ!`);
      setName('');
      setPrice('');
    } catch (error) {
      console.error('❌ เพิ่มสินค้าล้มเหลว:', error);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <h2>📝 เพิ่มสินค้าใหม่</h2>
      <input
        type="text"
        placeholder="ชื่อสินค้า"
        value={name}
        onChange={(e) => setName(e.target.value)}
        required
      />
      <input
        type="number"
        placeholder="ราคา"
        value={price}
        onChange={(e) => setPrice(e.target.value)}
        required
      />
      <button type="submit">💾 บันทึกสินค้า</button>
    </form>
  );
}

export default AddProduct;
```

---

### 📝 **4. ทำไมต้องใช้ Axios?**
| 💡 **ข้อดีของ Axios**      | 🚀 **เหตุผล**                                |
|--------------------|-----------------------------------------|
| 🌐 รองรับ Promise  | ใช้ `async/await` ได้อย่างสะดวก 🕒     |
| 🛡 จัดการ Error ง่าย | มี `.catch()` และสามารถใช้ `try/catch` ได้ 🔒  |
| 🔄 รองรับ JSON อัตโนมัติ | ไม่ต้องเขียน `JSON.stringify()` หรือ `JSON.parse()` เอง |
| 🌍 รองรับ CORS       | จัดการเรื่อง cross-origin ได้ดี 🔗          |

---

### ⚡ **5. รวมหน้าใน React เพื่อเรียก API ทั้งหมด**  
```javascript
import React from 'react';
import ProductList from './ProductList';
import AddProduct from './AddProduct';

function App() {
  return (
    <div>
      <h1>🛒 ระบบจัดการสินค้า</h1>
      <AddProduct />
      <ProductList />
    </div>
  );
}

export default App;
```

---

### 🔥 **6. สรุป (TL;DR)**  
- 🧭 **Axios** = เครื่องมือเรียก API ที่ **ง่ายและทรงพลัง**  
- 🏃 **GET Request** → เรียกดูสินค้า  
- ✍️ **POST Request** → เพิ่มสินค้า  
- ✅ ทำงานร่วมกับ API (`/api/products`) ที่สร้างด้วย **Express** ได้โดยลดเวลาการพัฒนา
