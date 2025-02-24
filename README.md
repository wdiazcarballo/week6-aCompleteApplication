# 📚 **สัปดาห์ที่ 6: การเชื่อมต่อ Frontend กับ Backend ด้วย React, Redux และ Axios**  

## 🎯 **ภาพรวมของสัปดาห์นี้**  
กิจกรรมในสัปดาห์นี้:  
- 📖 ทบทวนแนวคิดหลักของ **React**  
- 🔄 ทำความเข้าใจ **Redux** สำหรับการจัดการข้อมูลในแอปพลิเคชัน  
- 🌐 เรียนรู้การใช้ **Axios** เพื่อเรียกใช้งาน API (HTTP Request)  
- 🔗 **บูรณาการ** (Integration) ระหว่าง **Frontend (React + Redux)** และ **Backend (Express + MongoDB)**  

---

## 📝 **ขั้นตอนในการเรียนรู้**  

### ✅ **1. ทบทวน React (`1 ทบทวน React.md`)**  
- 📌 **เนื้อหาที่ควรโฟกัส:**  
  - โครงสร้างของคอมโพเนนต์ใน React  
  - การจัดการ **state** และ **props**  
  - แนวคิดเรื่อง **Virtual DOM**  
  - **React Router** สำหรับการนำทาง (Navigation)  

- 💡 **กิจกรรม:**  
  - อ่านสรุป **React.md**  
  - ทำแบบฝึกหัดสร้างคอมโพเนนต์ง่าย ๆ เพื่อทบทวน  

---

### ✅ **2. ทบทวน Redux (`2 ทบทวน Redux.md`)**  
- 📌 **เนื้อหาที่ควรโฟกัส:**  
  - 🔄 **Store, Actions, Reducers** คืออะไร?  
  - 🧭 **Dispatch** ทำงานอย่างไรในการเปลี่ยน state  
  - 🏛 **Selector** สำหรับดึงข้อมูลจาก Store  
  - 🛡 การใช้ **Redux Toolkit** เพื่อทำงานกับ Redux ได้ง่ายขึ้น  

- 💡 **กิจกรรม:**  
  - อ่าน **Redux.md**  
  - ลองสร้าง Redux Store เพื่อจัดการข้อมูลง่าย ๆ เช่น **Todo List**  

---

### ✅ **3. ใช้ Axios ทำ HTTP Request (`3 ใช้ Axios ทำ HTTP Request.md`)**  
- 🌐 **Axios คืออะไร?**  
  - **Axios** เป็นไลบรารีสำหรับการส่ง **HTTP Request** (เช่น GET, POST, PUT, DELETE)  
  - ช่วยให้ React เชื่อมต่อกับ **Backend API** ได้อย่างสะดวกและปลอดภัย  

- ⚡ **เนื้อหาที่จะได้เรียนรู้:**  
  - ติดตั้ง **Axios** (`npm install axios`)  
  - **GET** ข้อมูลสินค้าจาก Backend  
  - **POST** ข้อมูลสินค้าใหม่ไปยัง Backend  
  - จัดการ **Error Handling** ด้วย `.catch()` และ `try/catch`  

- 💡 **กิจกรรม:**  
  - เขียนคอมโพเนนต์ React ที่ดึงข้อมูลจาก API ด้วย Axios  
  - ทดสอบการเพิ่มข้อมูลผ่านแบบฟอร์ม  

---

### ✅ **4. การบูรณาการ Frontend และ Backend (`4 การบูรณาการ Frontend และ Backend.md`)**  
- 🔗 **Frontend (React + Redux + Axios)** กับ **Backend (Express + MongoDB)**  
- ⚡ **สิ่งที่จะได้ฝึกฝน:**  
  - เชื่อมต่อ API `/api/products` จาก Backend ที่สร้างด้วย Express  
  - จัดการ state ของข้อมูลด้วย Redux  
  - ทำให้ UI อัปเดตแบบเรียลไทม์เมื่อมีการเพิ่มหรือลบสินค้า  
  - ใช้ **React Router** ในการนำทางระหว่างหน้า  

- 💡 **กิจกรรม:**  
  - เขียนฟังก์ชันสำหรับเพิ่ม ลบ และแสดงข้อมูลสินค้าทั้งหมด  
  - ตรวจสอบการทำงานของระบบแบบ **End-to-End**  

---

## 💡 **⭐ เทคนิคที่ควรนำไปใช้**  
- 🧭 ใช้ **Redux** เพื่อให้ข้อมูลในแอปพลิเคชันสอดคล้องกันในทุกคอมโพเนนต์  
- 🌐 ใช้ **Axios** เพื่อจัดการ API Call อย่างมีประสิทธิภาพและปลอดภัย  
- 🏗 **แยกคอมโพเนนต์** ให้ชัดเจน เช่น `ProductList`, `AddProduct`, และ `ProductDetail`  
- 🛡 **จัดการข้อผิดพลาด** ในทุกการเรียกใช้งาน API  

---

## 🚀 **🎯 ผลลัพธ์ที่คาดหวัง (Learning Outcomes)**  
เมื่อจบสัปดาห์นี้ นักศึกษาจะสามารถ:  
- ✅ สร้างและจัดการ **React Components** ได้อย่างถูกต้อง  
- 🔄 ใช้ **Redux** ในการจัดการข้อมูลร่วมกันระหว่างคอมโพเนนต์  
- 🌐 เชื่อมต่อ **Frontend** กับ **Backend API** ด้วย **Axios**  
- 🔗 ทำให้แอปพลิเคชันสามารถทำงานแบบ **Full-stack** ได้อย่างสมบูรณ์  

---

---
