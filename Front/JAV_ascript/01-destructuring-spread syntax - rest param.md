# 🧩 JavaScript: Destructuring, Spread Syntax, và Rest Parameter

## 1. 🎯 Destructuring (Phân rã)

### 🧱 Destructuring với Object

Thay vì truy xuất từng thuộc tính bằng cú pháp chấm (`.`):

```js
const user = {
  name: 'duong',
  age: 24,
  sex: 'male'
};

const name = user.name;
const age = user.age;
const sex = user.sex;
```

👉 Ta có thể **rút gọn** bằng **object destructuring**:

```js
const { name, age, sex } = user;

console.log(name); // "duong"
console.log(age);  // 24
console.log(sex);  // "male"
```

Kết quả **tương đương** với cách truy xuất thủ công ở trên.

---

### 🧮 Destructuring với Array

Với mảng, ta có thể phân rã các phần tử theo vị trí:

```js
const list = [
  1,
  function (a, b) {
    return a + b;
  }
];

const [value, sum] = list;

console.log(value); // 1
console.log(sum(3, 4)); // 7
```

✅ `value` nhận giá trị phần tử đầu tiên
✅ `sum` nhận giá trị phần tử thứ hai (một hàm)

---

## 2. 🌊 Spread Syntax (`...`)

Dùng để **sao chép nông (shallow copy)** hoặc **gộp dữ liệu**.

```js
const user = {
  name: 'duong',
  age: 24,
  sex: 'male',
  ability: ['coding']
};

// Shallow copy
const cloneUser = { ...user };

console.log(cloneUser === user); // ❌ false (object mới)
console.log(cloneUser.ability === user.ability); // ✅ true (cùng tham chiếu mảng)
```

🔍 **Giải thích:**

* `cloneUser` là **một object mới**, nên không trùng địa chỉ bộ nhớ với `user`.
* Tuy nhiên, `ability` là **mảng (object con)** nên chỉ được sao chép **tham chiếu**, không phải dữ liệu — vì vậy nó **vẫn trỏ cùng vùng nhớ**.

---

## 3. 🧮 Rest Parameter (`...rest`)

Dùng trong **định nghĩa hàm** để gom các đối số còn lại thành **một mảng**.

```js
const handle = (a, b, ...c) => {
  return c;
};

const value = handle(1, 2, 3, 4, 5, 6);

console.log(value); // [3, 4, 5, 6]
```

👉 `a = 1`, `b = 2`, và phần còn lại (`[3,4,5,6]`) được gom vào `c`.

---

## 4. 🔄 Kết hợp Rest Parameter và Destructuring

Ta có thể **phân rã** object **và thu gọn phần còn lại** bằng rest parameter.

```js
const handle = ({ a, b, ...c }) => {
  return c;
};

const value = handle({ a: 1, b: 2, c: 3, d: 4, e: 5 });

console.log(value);
```

### 💡 Kết quả:

```js
{ c: 3, d: 4, e: 5 }
```

🔍 **Giải thích:**

* `{ a, b, ...c }` tách ra hai thuộc tính `a` và `b`.
* Các thuộc tính **còn lại** được gom vào object `c`.

---

## 🧠 Tóm tắt nhanh

| Khái niệm          | Ký hiệu        | Dùng cho                             | Mục đích              |
| ------------------ | -------------- | ------------------------------------ | --------------------- |
| **Destructuring**  | `{}` hoặc `[]` | Object / Array                       | Phân rã giá trị nhanh |
| **Spread syntax**  | `...obj`       | Khi sao chép hoặc gộp                | Tạo bản sao nông      |
| **Rest parameter** | `...rest`      | Trong định nghĩa hàm / destructuring | Gom phần còn lại      |

---

📘 **Ghi nhớ:**

* Spread (`...`) và Rest (`...`) **giống nhau về cú pháp** nhưng **khác ngữ cảnh sử dụng**:

  * **Spread:** dùng để “trải” dữ liệu ra.
  * **Rest:** dùng để “gom” dữ liệu vào.

---