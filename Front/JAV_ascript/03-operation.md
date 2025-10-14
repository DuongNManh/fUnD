# 🧠 Toán tử Logic trong JavaScript

Trong JavaScript, các **toán tử logic** hoạt động dựa trên **giá trị Truthy và Falsy**.  
Hiểu rõ cách chúng hoạt động giúp bạn viết code ngắn gọn, chính xác và tránh lỗi logic.

---

## ⚖️ Truthy và Falsy

### 🔹 Giá trị Falsy (coi là `false` khi chuyển sang boolean)

| Giá trị | Ghi chú |
|----------|----------|
| `false` | Giá trị boolean sai |
| `0`, `-0`, `0n` | Số 0 (kể cả BigInt 0n) |
| `""` | Chuỗi rỗng |
| `null` | Không có giá trị |
| `undefined` | Chưa được gán giá trị |
| `NaN` | Not-a-Number |

> 👉 Ngoài các giá trị trên, **mọi thứ khác đều là Truthy**, tức là `true` khi chuyển sang boolean.

### 🔹 Ví dụ trực quan

| Biểu thức | Kết quả | Ghi chú |
|------------|----------|----------|
| `Boolean(123)` | ✅ `true` | Số khác 0 là Truthy |
| `Boolean('Hi')` | ✅ `true` | Chuỗi có nội dung |
| `Boolean('')` | ❌ `false` | Chuỗi rỗng |
| `Boolean(null)` | ❌ `false` | null là Falsy |
| `Boolean([])` | ✅ `true` | Mảng rỗng vẫn Truthy |
| `Boolean({})` | ✅ `true` | Object luôn Truthy |

---

## ⚙️ Toán tử `&&` (AND)

Toán tử `&&` **dừng lại khi gặp Falsy**, hoặc **trả về giá trị cuối cùng** nếu không có Falsy nào.

```js
const a = true
const b = ''
const c = 'Hi'

const d = a && b && c // => ''
````

🧩 Ví dụ:

```js
let check = 10
const handle = () => [1, 2, 3].map(i => i * 2)

let value = []

// Cách 1:
if (check > 9) {
    value = handle()
}

// Cách 2 (viết ngắn hơn):
value = check > 9 && handle() // => [2, 4, 6]

// Nếu check = 8:
value = check > 9 && handle() // => false
```

### 🔹 Bảng minh hoạ `&&`

|    A    |    B    |   A && B  |
| :-----: | :-----: | :-------: |
|  `true` |  `true` |  ✅ `true` |
|  `true` | `false` | ❌ `false` |
| `false` |  `true` | ❌ `false` |
| `false` | `false` | ❌ `false` |

---

## ⚙️ Toán tử `||` (OR)

Toán tử `||` **dừng lại khi gặp Truthy**, hoặc **trả về giá trị cuối cùng** nếu tất cả là Falsy.

```js
const a = null
const b = 12
const c = 'Hi'

const d = a || b || c // => 12
```

### 🔹 Bảng minh hoạ `||` (trong bảng là `OR`)

|    A    |    B    |   A `OR` B  |
| :-----: | :-----: | :-------:  |
|  `true` |  `true` |  ✅ `true` |
|  `true` | `false` |  ✅ `true` |
| `false` |  `true` |  ✅ `true` |
| `false` | `false` | ❌ `false` |

---

## ⚙️ Toán tử phủ định `!`

Đảo ngược giá trị Truthy/Falsy.

```js
const a = null
const b = 12
const c = 'Hi'

const d = !(a || b || c) // => false (vì a || b || c => true)
```

---

## ⚙️ Toán tử 3 ngôi `? :`

Cú pháp rút gọn cho `if...else`.

```js
let fname = 'Alex'

fname === 'Alex' ? console.log(true) : console.log(false)
```

---

## ⚙️ Optional Chaining `?.`

Giúp **truy cập an toàn** các thuộc tính lồng nhau mà **không gây lỗi** khi gặp `undefined` hoặc `null`.

```js
let user = {} // user không có thuộc tính address

alert(user.address.street) // ❌ Error!
```

✅ Cách xử lý:

```js
alert(user?.address?.street) // => undefined
```

> Gặp `undefined` hoặc `null` sẽ **dừng truy cập ngay lập tức** và trả về `undefined`.

---

## ⚙️ Nullish Coalescing `??`

Chỉ kiểm tra **undefined** hoặc **null** (không như `||` kiểm tra tất cả Falsy).

```js
let user

alert(user ?? 'Anonymous') // => 'Anonymous'
```

### 🔹 So sánh `||` (trong bảng là `OR`) và `??`

| Toán tử             | Điều kiện kích hoạt                                   | Ví dụ              | Kết quả     |
| ------------------- | ----------------------------------------------------- | ------------------ | ----------- |
| `OR`                | Trả về giá trị đầu tiên **Truthy**                    | `0 OR 'default'`   | `'default'` |
| `??`                | Trả về giá trị đầu tiên **không phải null/undefined** | `0 ?? 'default'`   | `0`         |

## ⚙️ Template String (Chuỗi nội suy)

Dùng ký tự `` ` `` (backtick) để nhúng biến hoặc biểu thức vào chuỗi.

```js
let a = 'text 1'

// Cách cũ:
let b = 'string text ' + a + ' string text'

// Cách mới:
let c = `string text ${a} string text`
```

Bạn cũng có thể thực hiện phép tính bên trong:

```js
let x = 5
let y = 10
console.log(`Tổng là: ${x + y}`) // Tổng là: 15
```

---

## 🧾 Tổng kết nhanh

| Toán tử   | Ý nghĩa            | Dừng tại         | Trả về                           |
| --------- | ------------------ | ---------------- | -------------------------------- |
| `&&`      | AND                | Gặp Falsy        | Giá trị Falsy đầu tiên hoặc cuối |
| `OR`      | OR                 | Gặp Truthy       | Giá trị Truthy đầu tiên hoặc cuối|
| `!`       | NOT                | -                | Đảo boolean                      |
| `??`      | Nullish Coalescing | null / undefined | Giá trị đầu tiên không nullish   |
| `?.`      | Optional Chaining  | undefined / null | undefined nếu gặp nullish        |
| `` ` ` `` | Template String    | -                | Chuỗi có thể chứa biến           |

---

> ✨ **Mẹo nhớ nhanh:**
>
> * `&&` = *phải đúng hết*
> * `||` = *chỉ cần 1 đúng*
> * `??` = *chỉ quan tâm null hoặc undefined*
> * `?.` = *truy cập an toàn thuộc tính*
> * `` ` ` `` = *chuỗi có biến*
