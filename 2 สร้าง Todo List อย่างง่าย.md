# 📚 การสร้าง To-Do List ด้วย Redux 

### 🎯 **เป้าหมายของกิจกรรมนี้:**  
- สอนการใช้งาน **Redux** ใน **React** ผ่านโปรเจกต์ **To-Do List**  
- อธิบายแนวคิดหลักของ Redux ได้แก่ `Store`, `Actions`, `Reducers`, `Dispatch`, และ `Selector`  
- ทำความเข้าใจการใช้ **Redux Toolkit** ซึ่งช่วยให้เขียน Redux ได้ง่ายขึ้น

---

## 🌟 **1. เตรียมโปรเจกต์**  
### ✅ **1.1 สร้าง React App**  
```bash
npx create-react-app redux-todo
cd redux-todo
```

### ✅ **1.2 ติดตั้ง Redux และ Redux Toolkit**  
```bash
npm install @reduxjs/toolkit react-redux
```
- `@reduxjs/toolkit`: ไลบรารีสำหรับการทำงานกับ Redux ได้อย่างมีประสิทธิภาพ  
- `react-redux`: ช่วยเชื่อมต่อ Redux กับ React Components

---

## 🏗 **2. สร้าง Redux Store**  

### ✅ **2.1 สร้างไฟล์ `store.js` ในโฟลเดอร์ `src`**  
```javascript
// src/store.js
import { configureStore } from '@reduxjs/toolkit';
import todoReducer from './todoSlice';

const store = configureStore({
  reducer: {
    todos: todoReducer,
  },
});

export default store;
```

📌 **อธิบาย:**  
- `configureStore`: สร้าง store และตั้งค่า middleware ให้อัตโนมัติ  
- `todos`: ชื่อ state หลักที่เราจะใช้ในโปรเจกต์นี้  

---

## 📝 **3. สร้าง Slice สำหรับ To-Do**  
### ✅ **3.1 สร้างไฟล์ `todoSlice.js`**  
```javascript
// src/todoSlice.js
import { createSlice } from '@reduxjs/toolkit';

export const todoSlice = createSlice({
  name: 'todos',
  initialState: [],
  reducers: {
    addTodo: (state, action) => {
      state.push({ id: Date.now(), text: action.payload, completed: false });
    },
    toggleTodo: (state, action) => {
      const todo = state.find((todo) => todo.id === action.payload);
      if (todo) {
        todo.completed = !todo.completed;
      }
    },
    deleteTodo: (state, action) => {
      return state.filter((todo) => todo.id !== action.payload);
    },
  },
});

export const { addTodo, toggleTodo, deleteTodo } = todoSlice.actions;
export default todoSlice.reducer;
```

📌 **อธิบาย:**  
- `addTodo`: เพิ่มรายการใหม่  
- `toggleTodo`: เปลี่ยนสถานะเสร็จ/ไม่เสร็จ  
- `deleteTodo`: ลบรายการออกจาก state  

---

## 🔗 **4. เชื่อมต่อ Redux Store กับ React App**  
### ✅ **4.1 แก้ไขไฟล์ `index.js`**  
```javascript
// src/index.js
import React from 'react';
import ReactDOM from 'react-dom/client';
import { Provider } from 'react-redux';
import store from './store';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <Provider store={store}>
    <App />
  </Provider>
);
```

📌 **อธิบาย:**  
- `Provider`: ครอบ `App` ทั้งหมดเพื่อให้ทุกคอมโพเนนต์เข้าถึง Redux store ได้

---

## 🖋 **5. สร้าง UI สำหรับ To-Do List**  

### ✅ **5.1 สร้างคอมโพเนนต์ `TodoInput.js`**  
```javascript
// src/components/TodoInput.js
import React, { useState } from 'react';
import { useDispatch } from 'react-redux';
import { addTodo } from '../todoSlice';

function TodoInput() {
  const [text, setText] = useState('');
  const dispatch = useDispatch();

  const handleSubmit = (e) => {
    e.preventDefault();
    if (text.trim()) {
      dispatch(addTodo(text));
      setText('');
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        placeholder="📝 เพิ่มงานที่ต้องทำ..."
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
      <button type="submit">➕ เพิ่ม</button>
    </form>
  );
}

export default TodoInput;
```

---

### ✅ **5.2 สร้างคอมโพเนนต์ `TodoList.js`**  
```javascript
// src/components/TodoList.js
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { toggleTodo, deleteTodo } from '../todoSlice';

function TodoList() {
  const todos = useSelector((state) => state.todos);
  const dispatch = useDispatch();

  return (
    <ul>
      {todos.map((todo) => (
        <li
          key={todo.id}
          style={{
            textDecoration: todo.completed ? 'line-through' : 'none',
            cursor: 'pointer',
          }}
          onClick={() => dispatch(toggleTodo(todo.id))}
        >
          {todo.text}
          <button onClick={() => dispatch(deleteTodo(todo.id))}>❌ ลบ</button>
        </li>
      ))}
    </ul>
  );
}

export default TodoList;
```

📌 **อธิบาย:**  
- `useSelector`: ดึงข้อมูล `todos` จาก Redux store  
- `useDispatch`: เรียก `toggleTodo` และ `deleteTodo` เมื่อผู้ใช้คลิก

---

### ✅ **5.3 รวมคอมโพเนนต์ใน `App.js`**  
```javascript
// src/App.js
import React from 'react';
import TodoInput from './components/TodoInput';
import TodoList from './components/TodoList';

function App() {
  return (
    <div style={{ textAlign: 'center', padding: '20px' }}>
      <h1>📝 To-Do List ด้วย Redux</h1>
      <TodoInput />
      <TodoList />
    </div>
  );
}

export default App;
```

---

## 🏃 **6. ทดสอบโปรเจกต์**  
1. ✅ รันโปรเจกต์:  
   ```bash
   npm start
   ```
2. 📝 ลองเพิ่มงานที่ต้องทำ  
3. 🏃 คลิกเพื่อเปลี่ยนสถานะเสร็จ/ไม่เสร็จ  
4. ❌ ลบงานที่ไม่ต้องการออก

---

## 🎯 **สรุปสิ่งที่ได้เรียนรู้:**  
- 🔄 **Redux Store**: ศูนย์กลางเก็บข้อมูล  
- 📤 **Actions**: วิธีการร้องขอการเปลี่ยนแปลงข้อมูล  
- 🛠 **Reducers**: กำหนดวิธีการเปลี่ยนข้อมูลตาม action  
- 🏃 **Dispatch**: กลไกเรียกใช้งาน action  
- 🔍 **Selector**: ดึงข้อมูลจาก store มาใช้ในคอมโพเนนต์  

---
