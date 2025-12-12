# ⚙️ JavaScript: Tham trị, Tham chiếu và Cách Copy Dữ liệu

---

## 🧩 1. Khái niệm cơ bản

Trong JavaScript, **mọi giá trị** được truyền hoặc gán **theo hai cách**:

| Loại dữ liệu                         | Cách truyền                           | Giải thích                                                                             |
| ------------------------------------ | ------------------------------------- | -------------------------------------------------------------------------------------- |
| **Kiểu nguyên thủy (Primitive)**     | 🔹 **Tham trị (Pass by Value)**       | Gán **một bản sao giá trị** — thay đổi biến sao chép **không ảnh hưởng** biến gốc.     |
| **Kiểu tham chiếu (Reference Type)** | 🔸 **Tham chiếu (Pass by Reference)** | Gán **địa chỉ tham chiếu** đến vùng nhớ — thay đổi giá trị **ảnh hưởng** đến biến gốc. |

---

## 🧱 2. Tham trị (Pass by Value)

### ✅ Các kiểu dữ liệu nguyên thủy:

* `string`
* `number`
* `boolean`
* `undefined`
* `null`
* `symbol`
* `bigint`

### 🧠 Ví dụ:

```js
let a = 10;
let b = a;  // Sao chép giá trị của a

b = 20;

console.log(a); // 10  (không đổi)
console.log(b); // 20
```

📘 **Giải thích:**
`a` và `b` lưu hai bản sao **độc lập** của giá trị `10`.

---

## 🧭 3. Tham chiếu (Pass by Reference)

### ✅ Các kiểu dữ liệu phức hợp (object type):

* `Object`
* `Array`
* `Function`
* `Date`, `Map`, `Set`, …

### 🧠 Ví dụ:

```js
let user1 = { name: 'duong', age: 24 };
let user2 = user1; // Gán cùng vùng nhớ

user2.age = 30;

console.log(user1.age); // 30  ✅ Ảnh hưởng cả user1
```

📘 **Giải thích:**
`user1` và `user2` **trỏ cùng địa chỉ vùng nhớ**, nên thay đổi một trong hai sẽ làm thay đổi cả hai.

---

## 🪞 4. Copy (Sao chép dữ liệu)

### 🔹 4.1. Shallow Copy (Sao chép nông)

Copy **chỉ cấp đầu tiên** của object — các object con **vẫn dùng cùng tham chiếu**.

#### Cách 1 — Spread syntax (`...`)

```js
const user = {
  name: 'duong',
  skills: ['JS', 'Flutter']
};

const clone = { ...user };

clone.name = 'nguyen';
clone.skills.push('C#');

console.log(user.name); // "duong"  (độc lập)
console.log(user.skills); // ['JS', 'Flutter', 'C#']  ⚠️ bị ảnh hưởng
```

#### Cách 2 — `Object.assign()`

```js
const clone = Object.assign({}, user);
```

📘 **Cả hai cách trên** chỉ sao chép **cấp 1**, nên vẫn bị “dính” nếu có object hoặc array lồng trong.

---

### 🔸 4.2. Deep Copy (Sao chép sâu)

Copy **toàn bộ dữ liệu**, bao gồm cả các object con.
Không còn liên kết với object gốc.

#### Cách 1 — JSON

```js
const deepClone = JSON.parse(JSON.stringify(user));
```

* ✅ Ưu điểm: Dễ dùng
* ⚠️ Nhược điểm: Mất kiểu dữ liệu đặc biệt (`Date`, `Map`, `Set`, `undefined`, `function`…)

#### Cách 2 — structuredClone (ES2021+)

```js
const deepClone = structuredClone(user);
```

* ✅ Ưu điểm: Sao chép sâu an toàn, giữ nguyên cấu trúc
* ⚠️ Nhược điểm: Không sao chép được function hoặc các kiểu đặc biệt như `WeakMap`.

---

## ⚖️ 5. So sánh Shallow vs Deep Copy

| Đặc điểm                | Shallow Copy          | Deep Copy                             |
| ----------------------- | --------------------- | ------------------------------------- |
| Mức độ sao chép         | Chỉ cấp 1             | Toàn bộ cấu trúc                      |
| Object lồng nhau        | Giữ cùng tham chiếu   | Tạo mới hoàn toàn                     |
| Cách thực hiện phổ biến | Spread, Object.assign | JSON.parse/stringify, structuredClone |
| Ảnh hưởng dữ liệu gốc   | Có thể có             | Không                                 |

---

## 🔄 6. Truyền vào hàm

### 🧠 Với kiểu nguyên thủy (tham trị):

```js
function change(x) {
  x = 100;
}

let num = 10;
change(num);

console.log(num); // 10 (không đổi)
```

### 🧠 Với object (tham chiếu):

```js
function updateUser(u) {
  u.name = 'new name';
}

let user = { name: 'duong' };
updateUser(user);

console.log(user.name); // "new name" ✅ bị thay đổi
```

---

## 🧮 7. Tổng kết

| Loại dữ liệu       | Truyền           | Ảnh hưởng khi sửa biến copy | Ví dụ copy phổ biến                                   |
| ------------------ | ---------------- | --------------------------- | ----------------------------------------------------- |
| **Primitive**      | Tham trị         | ❌ Không ảnh hưởng           | `a = b`                                               |
| **Object / Array** | Tham chiếu       | ✅ Ảnh hưởng                 | `const b = a`                                         |
| **Shallow Copy**   | Sao chép cấp 1   | ⚠️ Ảnh hưởng phần con       | `{...a}`, `Object.assign`                             |
| **Deep Copy**      | Sao chép toàn bộ | ❌ Hoàn toàn tách biệt       | `structuredClone(a)`, `JSON.parse(JSON.stringify(a))` |

---
