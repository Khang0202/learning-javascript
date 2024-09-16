
# KHAI BÁO BIẾN

<details>
<summary><b>VAR
</b></summary><br/>
  
**1. Toàn cục (global scope) nếu được khai báo bên ngoài bất kỳ hàm (funtion) nào**
```js
var testVarGlobal = "Hello, World!";
```

**2. Chỉ có phạm vi hàm (function scope) nếu được khai báo bên trong một hàm**
```js
function testVarFunctionScope() {
  var testVarScopeMessage = "Hello, World!";
  console.log(testVarScopeMessage);
}
//gọi hàm
testVarFunctionScope();

// gọi thử bên ngoài hàm
console.warn(testVarScopeMessage); //ReferenceError (không thể truy cập trước khi khai báo)
```

**3. Block scope**
- **Var không có block scope (phạm vi khối)**
- **Các biến var khai báo bên trong một khối như if, for, hay while vẫn có thể truy cập được bên ngoài khối.**
  ```js
  if (true) {
    //gán giá trị biến var
    var testVarBlockScope = 1;
  }

  // sử dụng bên ngoài khối
  console.log(testVarBlockScope); // 1
  ```

**4. Hoisting**
- **Biến var được hoisting (nâng lên đầu) trong quá trình thực thi**
- **Có thể sử dụng biến var trước khi nó được khai báo**
- **Giá trị của nó sẽ là undefined cho đến khi gán giá trị**
  ```js
  // dùng trước khi khai báo
  testVarHoisting = 123;
  // kiểm tra trước khi khai báo
  console.log(testVarHoisting); // 123
  // khai báo biến
  var testVarHoisting = "Hello, World!, testVarHoisting";
  // kiểm tra sau khi khai báo
  console.log(testVarHoisting); // Hello, World!, testVarHoisting
  ```

**5. Có thể thay đổi giá trị (Reassignable)**
  ```js
  var testVar = 123;
  testVar = 234;
  testVar = 456;
  testVar = 789;
  ```
</details>

<details>
<summary><b>LET
</b></summary><br/>
  
**1. Phạm vi khối (block scope), chỉ tồn tại và có thể truy cập bên trong khối mà nó được khai báo**
```js
if (true) {
  let z = 30;
}
```

**2. Hoisting nhưng chúng không được khởi tạo cho đến khi trình biên dịch thực thi dòng khai báo**
```js
console.log(a); // ReferenceError (không thể truy cập trước khi khai báo)
let a = 5;
```

**3. Có thể thay đổi giá trị (Reassignable)**
  ```js
  let y = 20;
  y = 30;
  y = 40;
  ```
</details>

<details>
<summary><b>CONST
</b></summary><br/>
  
**1. Phạm vi khối (block scope), chỉ tồn tại và có thể truy cập bên trong khối mà nó được khai báo**
```js
if (true) {
  const z = 30;
}
```

**2. Hoisting nhưng chúng không được khởi tạo cho đến khi trình biên dịch thực thi dòng khai báo**
```js
console.log(a); // ReferenceError (không thể truy cập trước khi khai báo)
const a = 5;
```

**3. Không thể thay đổi giá trị (Non-reassignable)**
- Biến khai báo bằng const không thể thay đổi giá trị sau khi đã được gán. Điều này làm cho const thích hợp cho các giá trị cố định hoặc không thay đổi.
  ```js
  const b = 40;
  console.log(b); // 40
  b = 50; // Error: Assignment to constant variable.
  ```
  
- **Chú ý**: Đối với các đối tượng (object) hoặc mảng (array), bạn không thể thay đổi biến const nhưng có thể thay đổi nội dung của đối tượng hoặc mảng.
  ```js
  const arr = [1, 2, 3];
  arr.push(4); // Thay đổi nội dung mảng vẫn được phép
  console.log(arr); // [1, 2, 3, 4]
  ```
</details>

<details>
<summary><b>Tóm tắt sự khác biệt
</b></summary><br/>

| **Đặc điểm**         | `var`                         | `let`                         | `const`                       |
| ---------------- | --------------------------- | --------------------------- | --------------------------- |
| **Phạm vi (Scope)** | Toàn cục hoặc hàm (không có block scope) | Block scope | Block scope |
| **Hoisting** | Có (khởi tạo với undefined) | Có (không khởi tạo, gây lỗi nếu truy cập trước khi khai báo) | Có (không khởi tạo, gây lỗi nếu truy cập trước khi khai báo) |
| **Gán lại giá trị** | Có thể | Có thể | Không thể (nhưng có thể thay đổi nội dung của đối tượng hoặc mảng) |
| **Tính năng đặc biệt** | Không đồng bộ với block scope | Đồng bộ với block scope | Đồng bộ với block scope và không cho phép gán lại |
</details>
