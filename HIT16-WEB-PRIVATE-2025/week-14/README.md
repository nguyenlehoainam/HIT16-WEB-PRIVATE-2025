# HIT16-WEB-PRIVATE-2025 - WEEK 14

---

#### [Home](../index.html)

---

#### [I. Function](#i-function)

#### [II. Làm việc với mảng](#ii-làm-việc-với-mảng)

---

#### I. Function

**1. Function là gì?**

- Function hay hàm là một khối các câu lệnh được định nghĩa để thực hiện một nhiệm vụ hay một hành động cụ thể nào đó
- Hàm phục vụ những mục đích sau:
  - Tái sử dụng mã
  - Việc chia chương trình thành các đoạn mã nhỏ sẽ giúp đọc hiểu, bảo trì chương trình dễ dàng hơn
- **Cú pháp**:

```js
function tenHam(thamSo1, thamSo2, ...) {
    // Các dòng lệnh thực thi
    return giaTri; // (Tùy chọn) Trả về một giá trị
}

tenHam(thamSo1, thamSo2, ...);
```

- **Lưu ý:**

  - Tên hàm phải được bắt đầu bằng chữ cái (a-z,A-Z) hoặc ký tự `_`.
  - Tên hàm không được bắt đầu bằng số, các ký tự khác ký tự `_`.
  - Một hàm có thể gọi lại chính nó, hay còn gọi là đệ quy

- **Ví dụ**:

```js
function sumMoney(a, b) {
  return a + b;
}

const total = sumMoney(10, 20);
console.log(total);
```

```js
function sayHello() {
  console.log("Hello world");
}

sayHello();
```

```js
function factorial(n) {
  if (n == 0 || n == 1) return 1;
  else return n * factorial(n - 1);
}

let a, b, c;
a = factorial(1); // a gets the value 1
b = factorial(2); // b gets the value 2
c = factorial(3); // c gets the value 6
```

**2. Tham số (Parameters), đối số (arguments)**

**2.1. Tham số (parameters)**

- Tham số là các biến được định nghĩa (trong dấu ( ) ) trong khi khai báo hàm. Chúng đóng vai trò là giá trị đầu vào mà hàm yêu cầu để thực hiện một nhiệm vụ cụ thể nào đó
- **Ví dụ**
  ```js
  function greet(name) {
    console.log(`Xin chào, ${name}!`);
  }
  ```

**2.2. Đối số (arguments)**

- Đối số là giá trị thực tế được truyền vào tham số của hàm khi hàm được gọi.
- Mỗi đối số sẽ được gán vào tham số tương ứng trong định nghĩa hàm.
- **Ví dụ:**

  ```js
  greet("Nam");
  ```

**2.3. Lưu ý**

- Số lượng tham số và đối số phải khớp nhau

  ```js
  function multiply(a, b) {
    return a * b;
  }
  console.log(multiply(4, 5)); // Output: 20
  ```

- Nếu truyền không đủ đối số, các tham số còn thiếu sẽ gán giá trị mặc định là undifined.

  ```js
  function greet(name) {
    console.log(`Xin chào, ${name}!`);
  }
  greet(); // Output: Xin chào, undefined!
  ```

- Giá trị mặc định của tham số (Default Parameters):
  Trong JavaScript, chúng ta có thể cung cấp giá trị mặc định cho tham số để tránh lỗi khi không truyền đủ đối số.

  ```js
  function greet(name = "bạn") {
    console.log(`Xin chào, ${name}!`);
  }
  greet(); // Output: Xin chào, bạn!
  greet("Mai"); // Output: Xin chào, Mai!
  ```

- Số lượng đối số không xác định (Rest Parameters):
  Nếu chúng ta muốn một hàm nhận bất kỳ số lượng đối số nào, bạn có thể sử dụng rest parameters với dấu **`...`**

  ```js
  function sum(...numbers) {
    let total = 0;
    for (let i = 0; i < numbers.length; i++) {
      total += numbers[i];
    }
    return total;
  }

  console.log(sum(1, 2, 3, 4)); // Output: 10
  console.log(sum(10, 20)); // Output: 30
  ```

  ```js
  function printNumbers(...numbers) {
    for (const num of numbers) {
      console.log(num);
    }
  }

  printNumbers(5, 10, 15, 20);
  // Output:
  // 5
  // 10
  // 15
  // 20
  ```

- Trong JS, hàm được đối xử như một biến bình thường nên:
  - Có thể gán hàm cho biến.
  - Truyền hàm này vào hàm kia như một tham số (Callback).
  - Trả về một hàm từ một hàm khác (Higher-order function).

**3. Function Scope**

- Scope: Biến khai báo bên trong hàm thì không thể truy cập từ bên ngoài.
- Một hàm có thể truy cập đến mọi biến và mọi hàm khác trong cùng phạm vi mà nó được định nghĩa (Closure)

```js
// Các biến sau được định nghĩa trong phạm vi global scope
let num1 = 20,
  num2 = 3,
  name = "Khoa";

// Hàm này được định nghĩa trong phạm vi global scope
function multiply() {
  return num1 * num2;
}

multiply(); // Returns 60

// Một ví dụ hàm lồng nhau (Closure)
function getScore() {
  let num1 = 50,
    num2 = 50;

  function add() {
    return name + " scored " + (num1 + num2);
  }

  return add();
}

getScore(); // Returns "Khoa scored 100"
```

**2. Các loại function**

**2.1. Function Declarations**

- Đây là hàm được định nghĩa bằng từ khóa **`function`** và có tên hàm.
- Loại hàm này có thể gọi trước khi được định nghĩa nhờ **hoisting**
- **Cú pháp:**

```js
// Gọi hàm
console.log(tenHam(2, 3)); // Output: 5
function tenHam(thamSo1, thamSo2) {
  // Các lệnh thực thi
  return thamSo1 + thamSo2;
}
```

- Phiên bản sau hoisting:

```js
function tenHam(thamSo1, thamSo2) {
  // Các lệnh thực thi
  return thamSo1 + thamSo2;
}
console.log(tenHam(2, 3)); // Output: 5
```

**2.2. Function Expressions**

- Hàm được gán vào một biến
- Hàm này không thể được gọi trước khi khai báo vì phần nội dung hàm không được đưa lên đầu khi hoisting
- **Cú pháp:**

```js
console.log(tenHam(2, 3)); // Output: Uncaught ReferenceError: tenHam is not defined
const tenHam = function (thamSo1, thamSo2) {
  return thamSo1 + thamSo2;
};
```

- Phiên bản sau hoisting:

```js
const tenHam;
console.log(tenHam(2, 3)); // Output: Uncaught ReferenceError: tenHam is not defined
tenHam = function (thamSo1, thamSo2) {
  return thamSo1 + thamSo2;
};
```

**2.3. Arrow functions**

- Là loại hàm hay được sử dụng nhất sau này.
- **Arrow Function** là một cú pháp mới để viết các hàm trong Javascript.
- Nó giúp tiết kiệm thời gian phát triển và đơn giản hóa phạm vi function
- **Cú pháp:**

```js
const tenHam1 = (thamSo1, thamSo2) => {
  return thamSo1 + thamSo2;
};

console.log(tenHam(2, 3)); // Output: 5
// hoặc
const tenHam = (thamSo1, thamSo2) => thamSo1 + thamSo2;
console.log(tenHam1(2, 3)); // Output: 5
```

- **Ví dụ:**

```js
const multiply = (x, y) => {
  return x * y;
};

const phraseSplitterEs6 = (phrase) => phrase.split(" ");
console.log(phraseSplitterEs6("Love Codelearn")); // ["Love", "Codelearn"]

const hello = () => {
  console.log("Hello World");
};

hello();
```

**2.3. Anonymous Function**
Hàm không có tên, thường được dùng như callback hoặc gán cho một biến

```js
button.addEventListener("click", function () {});
button.addEventListener("click", () => {});
```

**3. Callback Function**

- Do hàm cũng là một kiểu biến nên có thể được khai báo làm tham số (parameter) cho một hàm khác.
- Khi đó, hàm được truyền vào làm đối số gọi sẽ là callback function.

```js
// tham số là param
function myFunction(param) {
  param("Khang");
}
// myCallback chính là hàm callback
function myCallback(name) {
  console.log(`Hello ${name}`);
}
// mình đang truyền hàm myCallback vào hàm myFunction
myFunction(myCallback);
```

#### II. Làm việc với mảng

- Cú pháp chung: 
```js
tenMang.tenPhuongThuc(callback(currentValue, index, array))
```
- Thường thì currentValue sẽ được đặt tên là số ít của tên mảng.
  Cho một mảng sau:
- Trong phần này phải nắm rõ được cú pháp, mục đích và kết quả trả về của các phương thức.

```js
const courses = [
  { id: 1, name: "Javascript", coin: 200 },
  { id: 2, name: "HTML, CSS", coin: 0 },
  { id: 3, name: "PHP", coin: 100 },
  { id: 4, name: "Angular", coin: 0 },
];
```

**1. `forEach`**

**Cú pháp:**

```js
array.forEach(callback(currentValue, index, array));
```

```js
// course la cac phần tử trong mảng courses
courses.forEach((course, index) => {
  console.log(index, course);
});
```

- Tham số đầu tiên là phần tử của mảng
- Tham số thứ hai là index của phần tử trong mảng

**2. `every`**

- every: tất cả -> tất cả phải thỏa mãn một điều kiện
- Kiểm tra tất cả phần tử của một mảng phải thỏa mãn một điều kiện nào đó
- Thỏa mãn điều kiện sẽ trả về true, còn lại trả về false
- Kiểm tra lần lượt theo thứ tự trong mảng, chỉ cần 1 phần tử trong mảng sai điều kiện thì sẽ dừng lại và trả về kết quả
- **Cú pháp:**

```js
array.every(callback(currentValue, index, array));
```

```js
const isFree = courses.every((course, index) => {
  return course.coin === 0;
  // if (course.coint === 0 ) return true
  // return false;
});
console.log(isFree);
```

**3. `some`**

- some -> Một vài -> Chỉ cần một vài thỏa mãn (cụ thể là 1 phần tử) thỏa mãn
- Duyệt mảng như every và forEach tuy nhiên chỉ cần có một phần tử trong mảng thỏa mãn điều kiện, vòng lặp sẽ ngay lập tức dừng lại
- **Cú pháp:**

```js
array.some(callback(currentValue, index, array));
```

```js
let isFree = courses.some((course, index) => {
  return course.coin === 0;
});

console.log(isFree);
```

**4. `find`**

- Dùng để tìm kiếm trong mảng
- Nếu có sẽ trả về chính phần tử đó, nếu không có sẽ trả về `undefined`
- Nó lặp qua từng phần tử, kiểm tra với điều kiện nếu thỏa mãn thì vòng lặp sẽ dừng, trả về đối tượng đầu tiên tìm được
- **Cú pháp:**

```js
array.find(callback(currentValue, index, array));
```

```js
let course = courses.find((course, index) => {
  return course.name === "Angular";
});

console.log(course);
```

**5. `filter`**

- Tương tự như `find` nhưng sẽ trả về một mảng chứa tất cả các phần tử thỏa mãn điều kiện
- **Cú pháp:**

```js
array.filter(callback(currentValue, index, array));
```

```js
let course = courses.filter((course, index) => {
  return course.coin >= 100;
});

console.log(course);
```

**6. `map`**

- Được sử dụng khi muốn thay đổi các phần tử, giá trị trong mảng và sẽ trả về một mảng mới từ mảng gốc, không làm thay đổi mảng gốc
- **Cú pháp:**

```js
array.map(callback(currentValue, index, array));
```

```js
let courses2 = courses.map((course, index) => {
  // 1. Tạo một biến mới là một Object hoàn toàn khác (không bị trùng tham chiếu)
  const newCourse = {
    ...course, // Copy lại toàn bộ các thuộc tính cũ (id, name, coin)
    coin: course.coin * 2,
  };
  return newCourse;
});
console.log(courses2);
```

- Không nên sử dụng newCourse = course trong map

**7. `reduce`**

- reduce -> thu gọn -> thu gọn mảng lại thành một giá trị.
- Tích lũy các phần tử của mảng thành một giá trị duy nhất (số, chuỗi, đối tượng, v.v.).

- **Cú pháp:**

  ```js
  array.reduce(callback(accumulator, currentValue, index, array), initialValue);
  ```
  - `accumulator`: Giá trị tích lũy từ lần gọi trước.
  - `currentValue`: Giá trị hiện tại của phần tử.
  - `initialValue` (tuỳ chọn): Giá trị khởi tạo của accumulator. Nếu không được cung cấp, phần tử đầu tiên của mảng sẽ được dùng.

```js
const coinSum = courses.reduce((accumulator, course) => {
  return accumulator + course.coin;
}, 0); // 0 là giá trị khởi tạo
console.log(coinSum); // Kết quả: 300
```

- Dù initialValue là tùy chọn, nhưng hãy luôn cung cấp nó trừ khi có lý do cực kỳ đặc biệt. Vì giúp:
  - Kiểm soát được kiểu dữ liệu trả về (Số, Chuỗi, Mảng, Object).
  - Tránh lỗi crash không mong muốn.
