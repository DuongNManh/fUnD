# ES6 – Constructor Function, Class, và Vấn đề `this`

## 1. Constructor Function (Trước ES6)

Trước khi ES6 giới thiệu cú pháp `class`, JavaScript sử dụng **constructor function** để tạo ra “kiểu đối tượng” tùy chỉnh.

### Ví dụ:

```js
function Cat(name, gender, color){
    this.name = name
    this.gender = gender
    this.color = color
}

// thêm method bằng prototype
Cat.prototype.meow = function(){
    console.log(`${this.name} is meowing!`)
}

let alex = new Cat('Alex', 'male', 'Orange')
alex.meow()
```

---

## 2. Thêm method trực tiếp trong constructor

```js
function Cat(name, gender, color){
    this.name = name
    this.gender = gender
    this.color = color

    this.meow = function(){
        console.log(`${this.name} is meowing!`)
    }
}

let alex = new Cat('Alex', 'male', 'Orange')
alex.meow()
```

### **Sự khác nhau giữa prototype và method trong constructor**

| Cách khai báo              | Lưu trữ ở đâu                              | Ưu / Nhược điểm                                                   |
| -------------------------- | ------------------------------------------ | ----------------------------------------------------------------- |
| `Cat.prototype.meow`       | Lưu ở prototype → shared giữa các instance | **Tối ưu bộ nhớ**, tốc độ tốt                                     |
| `this.meow = function(){}` | Tạo 1 bản copy mới cho mỗi instance        | Tốn bộ nhớ hơn nhưng method **giữ được context (`this`)** tốt hơn |

---

## 3. Class trong ES6

ES6 giới thiệu cú pháp `class` giúp code dễ đọc, gần giống các ngôn ngữ OOP khác.

```js
class Cat {
    constructor(name, gender, color){
        this.name = name
        this.gender = gender
        this.color = color
    }

    meow = function(){
        console.log(`${this.name} is meowing!`)
    }
}

let alex = new Cat('Alex', 'male', 'Orange')
alex.meow()
```

> Thực chất `class` chỉ là *syntactic sugar*, bên trong vẫn là constructor + prototype.

---

## 4. Vấn đề `this` trong class

`this` trong JavaScript phụ thuộc **vào cách hàm được gọi**, không phụ thuộc nơi định nghĩa.

### Ví dụ gây lỗi:

```js
function handle(cb){
    cb()
}

class Cat {
    constructor(name, gender, color){
        this.name = name
        this.gender = gender
        this.color = color
    }

    meow = function(){
        console.log(`${this.name} is meowing!`)
    }

    run() {
        handle(this.meow)
    }
}

const alex = new Cat('Alex', 'male', 'Orange')
alex.run()   // ❌ this = undefined → lỗi
```

### Vì sao lỗi?

`handle(this.meow)` → truyền function **không có context** → khi `cb()` chạy, JS đặt `this = undefined` (strict mode) → lỗi.

---

# 5. Các cách fix `this`

## ✔ Fix 1: Dùng `bind`

```js
run() {
    handle(this.meow.bind(this))
}
```

`bind` trả về function mới với `this` đã cố định.

---

## ✔ Fix 2: Dùng arrow function trong class

Arrow function **không có `this` riêng** → nó luôn lấy `this` từ class instance.

```js
meow = () => {
    console.log(`${this.name} is meowing!`)
}
```

Giờ dùng:

```js
run() {
    handle(this.meow)
}
```

---

## ✔ Fix 3: Dùng arrow function trong callback

```js
run() {
    handle(() => this.meow())
}
```

Callback lúc này do class gọi → giữ đúng `this`.

---

# 6. Khi nào dùng `bind`, arrow function, hay method prototype?

### **1. Dùng prototype method khi:**

* Tạo nhiều object → tiết kiệm bộ nhớ
* Không cần giữ `this` cố định (sẽ luôn gọi bằng `instance.method()`)

### **2. Dùng arrow function trong class khi:**

* Muốn method giữ `this` trong mọi tình huống
* Muốn pass method vào các callback như React, event handler

**Ví dụ thường gặp trong React:**

```js
onClick={this.handleClick} // nếu handleClick không phải arrow → mất this
```

### **3. Dùng `bind` khi:**

* Bạn muốn giữ `this` nhưng không muốn dùng arrow function (vì mỗi arrow function tạo một method mới trên mỗi instance)
* Tối ưu performance (arrow method làm tăng số lượng hàm trong memory)

---

# 7. Tóm tắt so sánh

| Khái niệm                   | Đặc điểm                  | Khi dùng                     |
| --------------------------- | ------------------------- | ---------------------------- |
| **Constructor Function**    | Cách tạo object trước ES6 | Code legacy, lib cũ          |
| **Class**                   | Dễ đọc, hiện đại, OOP hơn | Hầu hết dự án ES6+           |
| **Method Prototype**        | Shared, tối ưu bộ nhớ     | Object nhiều instance        |
| **Arrow Function in Class** | Giữ `this`, dễ dùng       | Khi truyền callback          |
| **bind(this)**              | Cố định context           | Performance tối ưu hơn arrow |

---
