# Hướng Dẫn Học Java Cơ Bản & OOP Toàn Tập

> Tài liệu tổng hợp Java — từ cú pháp cơ bản đến lập trình hướng đối tượng (OOP), kèm ví dụ code và bài tập thực hành.

---

## Mục lục

**PHẦN I — JAVA CƠ BẢN**
1. [Cấu trúc một chương trình Java](#1-cấu-trúc-một-chương-trình-java)
2. [Biến và kiểu dữ liệu](#2-biến-và-kiểu-dữ-liệu)
3. [Toán tử](#3-toán-tử)
4. [Câu lệnh điều kiện](#4-câu-lệnh-điều-kiện)
5. [Vòng lặp](#5-vòng-lặp)
6. [Mảng (Array)](#6-mảng-array)
7. [Chuỗi (String)](#7-chuỗi-string)
8. [Method (hàm)](#8-method-hàm)
9. [Nhập/xuất dữ liệu (Scanner)](#9-nhậpxuất-dữ-liệu-scanner)
10. [Ép kiểu (Casting) & Wrapper Class](#10-ép-kiểu-casting--wrapper-class)
11. [ArrayList & Collection cơ bản](#11-arraylist--collection-cơ-bản)
12. [Comment & quy tắc đặt tên](#12-comment--quy-tắc-đặt-tên)

**PHẦN II — LẬP TRÌNH HƯỚNG ĐỐI TƯỢNG (OOP)**
13. [Tổng quan về OOP](#13-tổng-quan-về-oop)
14. [Class và Object](#14-class-và-object)
15. [Constructor](#15-constructor)
16. [Từ khóa `this` và `static`](#16-từ-khóa-this-và-static)
17. [Tính đóng gói (Encapsulation)](#17-tính-đóng-gói-encapsulation)
18. [Tính kế thừa (Inheritance)](#18-tính-kế-thừa-inheritance)
19. [Tính đa hình (Polymorphism)](#19-tính-đa-hình-polymorphism)
20. [Tính trừu tượng (Abstraction)](#20-tính-trừu-tượng-abstraction)
21. [Interface vs Abstract Class](#21-interface-vs-abstract-class)
22. [Access Modifiers](#22-access-modifiers)
23. [Package](#23-package)
24. [Exception Handling trong OOP](#24-exception-handling-trong-oop)
25. [Generics](#25-generics)
26. [Object class & các phương thức quan trọng](#26-object-class--các-phương-thức-quan-trọng)
27. [Nguyên lý SOLID](#27-nguyên-lý-solid)
28. [Design Patterns cơ bản](#28-design-patterns-cơ-bản)
29. [Lỗi thường gặp](#29-lỗi-thường-gặp)
30. [Lộ trình luyện tập](#30-lộ-trình-luyện-tập)

---

# PHẦN I — JAVA CƠ BẢN

## 1. Cấu trúc một chương trình Java

```java
// Tên file phải trùng tên class public: HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Xin chào, Java!");
    }
}
```

**Giải thích:**
- `public class HelloWorld`: khai báo class — mọi thứ trong Java đều nằm trong class.
- `public static void main(String[] args)`: điểm bắt đầu chương trình (entry point) — JVM luôn tìm method này để chạy đầu tiên.
- `System.out.println(...)`: in ra màn hình kèm xuống dòng; `System.out.print(...)` in không xuống dòng.

**Biên dịch & chạy (dòng lệnh):**
```bash
javac HelloWorld.java   # biên dịch ra HelloWorld.class (bytecode)
java HelloWorld          # chạy trên JVM
```

---

## 2. Biến và kiểu dữ liệu

### 2.1 Khai báo biến

```java
int age = 20;
String name = "An";
```

Cú pháp: `<kiểu dữ liệu> <tên biến> = <giá trị>;`

### 2.2 Kiểu dữ liệu nguyên thủy (Primitive Types)

| Kiểu | Kích thước | Miền giá trị | Ví dụ |
|---|---|---|---|
| `byte` | 1 byte | -128 → 127 | `byte b = 100;` |
| `short` | 2 byte | -32,768 → 32,767 | `short s = 1000;` |
| `int` | 4 byte | ~-2.1 tỷ → 2.1 tỷ | `int x = 100000;` |
| `long` | 8 byte | rất lớn | `long l = 100000L;` (hậu tố `L`) |
| `float` | 4 byte | số thực, độ chính xác đơn | `float f = 3.14f;` (hậu tố `f`) |
| `double` | 8 byte | số thực, độ chính xác kép (mặc định) | `double d = 3.14;` |
| `char` | 2 byte | 1 ký tự Unicode | `char c = 'A';` |
| `boolean` | 1 bit | `true` / `false` | `boolean flag = true;` |

### 2.3 Kiểu tham chiếu (Reference Types)

Ngoài 8 kiểu nguyên thủy trên, mọi kiểu còn lại đều là **reference type**: `String`, mảng, class tự định nghĩa, `ArrayList`, ... — biến chứa **địa chỉ tham chiếu** tới object trên heap, không chứa trực tiếp giá trị.

```java
int x = 5;              // biến primitive — lưu trực tiếp giá trị 5
String s = "hello";     // biến reference — lưu địa chỉ trỏ tới object String
```

### 2.4 Hằng số

```java
final double PI = 3.14159; // final -> không thể gán lại giá trị
```

### 2.5 Phạm vi biến (Scope)

- **Biến local**: khai báo trong method/block `{ }`, chỉ tồn tại trong phạm vi đó.
- **Biến instance**: khai báo trong class, ngoài method — thuộc về từng object.
- **Biến static**: thuộc về class, dùng chung cho mọi object (xem phần OOP).

---

## 3. Toán tử

| Loại | Toán tử | Ví dụ |
|---|---|---|
| Số học | `+ - * / %` | `a % b` → lấy phần dư |
| Gán | `= += -= *= /= %=` | `x += 5;` tương đương `x = x + 5;` |
| So sánh | `== != > < >= <=` | `a == b` |
| Logic | `&& \|\| !` | `a > 0 && b > 0` |
| Tăng/giảm | `++ --` | `i++` (hậu tố), `++i` (tiền tố) |
| Ba ngôi | `? :` | `int max = (a > b) ? a : b;` |
| Bitwise | `& \| ^ ~ << >> >>>` | thao tác bit, ít dùng khi mới học |

**Lưu ý:**
- `/` giữa hai số nguyên là **phép chia lấy nguyên** (`7 / 2 = 3`), muốn chia thực phải ép kiểu: `7.0 / 2 = 3.5`.
- So sánh `String` **không** dùng `==` (so sánh địa chỉ tham chiếu) mà phải dùng `.equals()` (so sánh nội dung) — lỗi cực kỳ phổ biến với người mới học.

```java
String a = "hello";
String b = "hello";
String c = new String("hello");

a == b;         // true (cùng nằm trong String pool)
a == c;         // false (c là object mới trên heap)
a.equals(c);    // true (so sánh nội dung) — LUÔN dùng cách này
```

---

## 4. Câu lệnh điều kiện

### 4.1 `if / else if / else`

```java
int score = 75;
if (score >= 90) {
    System.out.println("Giỏi");
} else if (score >= 70) {
    System.out.println("Khá");
} else {
    System.out.println("Trung bình");
}
```

### 4.2 `switch`

```java
int day = 3;
switch (day) {
    case 1 -> System.out.println("Thứ Hai");
    case 2 -> System.out.println("Thứ Ba");
    case 3 -> System.out.println("Thứ Tư");
    default -> System.out.println("Không xác định");
}
```

*(Cú pháp `->` là switch expression từ Java 14+, gọn hơn cú pháp `case x: ... break;` truyền thống — nếu dùng cú pháp cũ, luôn nhớ `break` để tránh "rơi xuyên" các case.)*

---

## 5. Vòng lặp

```java
// for — biết trước số lần lặp
for (int i = 0; i < 5; i++) {
    System.out.println("i = " + i);
}

// while — lặp khi điều kiện còn đúng
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}

// do-while — chạy ít nhất 1 lần trước khi kiểm tra điều kiện
int j = 0;
do {
    System.out.println(j);
    j++;
} while (j < 5);

// for-each — duyệt qua tập hợp/mảng
int[] nums = {1, 2, 3, 4, 5};
for (int n : nums) {
    System.out.println(n);
}
```

`break` thoát khỏi vòng lặp ngay lập tức; `continue` bỏ qua phần còn lại của lần lặp hiện tại, tiếp tục vòng kế tiếp.

---

## 6. Mảng (Array)

```java
int[] scores = new int[5];         // mảng 5 phần tử, mặc định = 0
int[] arr = {10, 20, 30, 40, 50};  // khởi tạo trực tiếp

scores[0] = 90;                    // gán giá trị theo index (bắt đầu từ 0)
System.out.println(arr[2]);        // 30
System.out.println(arr.length);    // 5 — length là field, KHÔNG có dấu ()

// Mảng 2 chiều
int[][] matrix = new int[3][3];
matrix[0][0] = 1;

int[][] grid = {
    {1, 2, 3},
    {4, 5, 6}
};
```

**Lưu ý:** truy cập index ngoài phạm vi (`arr[10]` khi mảng chỉ có 5 phần tử) gây `ArrayIndexOutOfBoundsException` khi chạy — lỗi rất hay gặp, cần kiểm tra `index < arr.length` trước khi truy cập.

---

## 7. Chuỗi (String)

`String` trong Java là **bất biến (immutable)** — mọi thao tác "chỉnh sửa" thực chất tạo ra object `String` mới.

```java
String s = "Hello Java";

s.length();               // 10 — độ dài chuỗi
s.charAt(0);               // 'H' — ký tự tại vị trí index
s.substring(0, 5);         // "Hello"
s.toUpperCase();            // "HELLO JAVA"
s.toLowerCase();            // "hello java"
s.trim();                   // xóa khoảng trắng đầu/cuối
s.replace("Java", "World"); // "Hello World"
s.split(" ");                // ["Hello", "Java"]
s.contains("Java");          // true
s.indexOf("Java");           // 6
s.equals("Hello Java");      // so sánh nội dung — true

// Nối chuỗi
String greeting = "Hello" + " " + "Java";     // dùng +
StringBuilder sb = new StringBuilder();        // dùng StringBuilder khi nối nhiều lần trong vòng lặp — hiệu năng tốt hơn nhiều
sb.append("Hello").append(" ").append("Java");
String result = sb.toString();
```

**Vì sao ưu tiên `StringBuilder` trong vòng lặp?** Do `String` immutable, mỗi lần `+=` sẽ tạo object mới trên heap, gây tốn bộ nhớ và chậm khi lặp nhiều lần. `StringBuilder` là mutable, chỉnh sửa trên cùng một object.

---

## 8. Method (hàm)

```java
public class Calculator {
    // Cú pháp: <phạm vi> <kiểu trả về> <tên method>(<tham số>) { ... }
    public static int add(int a, int b) {
        return a + b;
    }

    public static void printMessage(String msg) { // void: không trả về gì
        System.out.println(msg);
    }

    public static void main(String[] args) {
        int result = add(3, 4);      // gọi method — result = 7
        printMessage("Kết quả: " + result);
    }
}
```

- **Tham số (parameter)**: biến khai báo trong định nghĩa method (`a`, `b`).
- **Đối số (argument)**: giá trị thực tế truyền vào khi gọi method (`3`, `4`).
- Java truyền tham số theo **pass-by-value**: với kiểu primitive, method nhận **bản sao** giá trị; với kiểu reference (object), method nhận bản sao của **địa chỉ tham chiếu** — nên có thể thay đổi nội dung object gốc qua method, nhưng không thể làm biến gốc trỏ sang object khác.

---

## 9. Nhập/xuất dữ liệu (Scanner)

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Nhập tên: ");
        String name = sc.nextLine();

        System.out.print("Nhập tuổi: ");
        int age = sc.nextInt();

        System.out.println("Xin chào " + name + ", bạn " + age + " tuổi.");

        sc.close(); // nên đóng Scanner khi dùng xong
    }
}
```

Các method thường dùng: `nextInt()`, `nextDouble()`, `nextLine()` (đọc cả dòng), `next()` (đọc 1 từ tới khoảng trắng). **Lưu ý kinh điển:** gọi `nextInt()` rồi gọi `nextLine()` ngay sau sẽ đọc phải ký tự xuống dòng còn sót lại — cần thêm một `sc.nextLine()` "vô hiệu" để loại bỏ nếu muốn đọc chuỗi tiếp theo.

---

## 10. Ép kiểu (Casting) & Wrapper Class

```java
// Widening (tự động — kiểu nhỏ sang kiểu lớn, không mất dữ liệu)
int i = 100;
double d = i; // 100.0

// Narrowing (tường minh — kiểu lớn sang kiểu nhỏ, có thể mất dữ liệu)
double x = 9.78;
int y = (int) x; // 9 — mất phần thập phân
```

### Wrapper Class & Autoboxing

Mỗi kiểu primitive có một class "bọc" tương ứng để dùng được trong các Collection (vốn chỉ chứa object, không chứa primitive):

| Primitive | Wrapper Class |
|---|---|
| `int` | `Integer` |
| `double` | `Double` |
| `char` | `Character` |
| `boolean` | `Boolean` |
| `long` | `Long` |

```java
int primitive = 10;
Integer wrapped = primitive;     // Autoboxing — tự động bọc thành object
int backToPrimitive = wrapped;   // Unboxing — tự động lấy lại giá trị primitive

Integer a = 127, b = 127;
a == b;        // true — do Integer cache giá trị -128..127
Integer c = 200, e = 200;
c == e;        // false — ngoài vùng cache, là 2 object khác nhau
c.equals(e);   // true — LUÔN dùng .equals() khi so sánh Wrapper Class
```

---

## 11. ArrayList & Collection cơ bản

Khác với mảng (kích thước cố định), `ArrayList` có thể **tự động thay đổi kích thước**.

```java
import java.util.ArrayList;
import java.util.List;

List<String> names = new ArrayList<>();
names.add("An");
names.add("Bình");
names.add(0, "Chi");      // chèn tại vị trí index

names.get(1);             // "An"
names.set(1, "Đức");      // sửa giá trị tại index
names.remove("Bình");     // xóa theo giá trị
names.remove(0);           // xóa theo index
names.size();               // số phần tử
names.contains("Chi");      // true
names.isEmpty();            // false

for (String n : names) {
    System.out.println(n);
}
```

**Lưu ý:** `ArrayList<T>` chỉ chứa **kiểu reference** (dùng `ArrayList<Integer>` chứ không phải `ArrayList<int>`) — vì Generics của Java không hỗ trợ trực tiếp kiểu primitive, phải nhờ autoboxing với Wrapper Class.

---

## 12. Comment & quy tắc đặt tên

```java
// Comment một dòng

/* Comment
   nhiều dòng */

/**
 * Javadoc — dùng để sinh tài liệu tự động
 * @param a số thứ nhất
 * @return tổng hai số
 */
public int add(int a, int b) { return a + b; }
```

### Quy ước đặt tên (Java Naming Convention)

| Đối tượng | Quy tắc | Ví dụ |
|---|---|---|
| Class | PascalCase | `StudentManager` |
| Method / biến | camelCase | `calculateTotal`, `studentName` |
| Hằng số (`final static`) | UPPER_SNAKE_CASE | `MAX_SIZE` |
| Package | chữ thường toàn bộ | `com.ptit.app` |

---

# PHẦN II — LẬP TRÌNH HƯỚNG ĐỐI TƯỢNG (OOP)

## 13. Tổng quan về OOP

OOP (Object-Oriented Programming) là mô hình lập trình tổ chức code xoay quanh **đối tượng (object)** thay vì hàm và logic thuần túy. Java là ngôn ngữ OOP thuần túy (gần như mọi thứ đều nằm trong class).

### 4 tính chất cốt lõi (Pillars)

| Tính chất | Ý nghĩa ngắn gọn |
|---|---|
| **Encapsulation** (Đóng gói) | Giấu dữ liệu nội bộ, chỉ cho truy cập qua interface công khai |
| **Inheritance** (Kế thừa) | Class con tái sử dụng thuộc tính/phương thức của class cha |
| **Polymorphism** (Đa hình) | Một hành động, nhiều cách thực thi tùy đối tượng |
| **Abstraction** (Trừu tượng) | Chỉ hiển thị đặc điểm cần thiết, ẩn chi tiết cài đặt |

### Vì sao học OOP quan trọng?

- Là nền tảng bắt buộc để học Spring Boot, thiết kế hệ thống backend, design patterns.
- Giúp code dễ bảo trì, mở rộng, tái sử dụng — cực kỳ quan trọng khi làm việc nhóm hoặc dự án lớn.
- Là kiến thức phỏng vấn backend/Java gần như luôn xuất hiện.

---

## 14. Class và Object

**Class** là bản thiết kế (blueprint). **Object** là thực thể được tạo ra từ class đó (instance).

```java
public class Student {
    // Thuộc tính (fields / attributes)
    String name;
    int age;
    double gpa;

    // Phương thức (methods / behavior)
    void study() {
        System.out.println(name + " đang học bài.");
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student(); // tạo object
        s1.name = "An";
        s1.age = 20;
        s1.study(); // An đang học bài.
    }
}
```

- `new` cấp phát vùng nhớ trên **heap** cho object, biến `s1` chứa **reference** trỏ tới vùng nhớ đó (không phải bản thân object).
- Mỗi object có state (dữ liệu) riêng nhưng dùng chung code method của class.

---

## 15. Constructor

Constructor là phương thức đặc biệt được gọi khi tạo object bằng `new`, dùng để khởi tạo trạng thái ban đầu.

```java
public class Student {
    String name;
    int age;

    // Constructor mặc định (no-arg)
    public Student() {
        this.name = "Unknown";
    }

    // Constructor có tham số
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

**Đặc điểm:**
- Tên constructor trùng tên class, không có kiểu trả về (kể cả `void`).
- Nếu không viết constructor nào, Java tự sinh constructor mặc định rỗng.
- **Nếu bạn tự viết bất kỳ constructor có tham số nào, Java sẽ không còn tự sinh constructor mặc định nữa** — đây là lỗi rất hay gặp.
- **Constructor overloading**: có thể có nhiều constructor với danh sách tham số khác nhau.
- **Constructor chaining**: dùng `this(...)` để gọi constructor khác trong cùng class, hoặc `super(...)` để gọi constructor lớp cha (phải là dòng đầu tiên).

```java
public class Student {
    String name;
    int age;

    public Student(String name) {
        this(name, 18); // gọi constructor khác — phải ở dòng đầu tiên
    }

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

---

## 16. Từ khóa `this` và `static`

### `this`
- Tham chiếu tới object hiện tại.
- Dùng để phân biệt field và tham số trùng tên, hoặc gọi constructor khác.

### `static`
- Thuộc về **class**, không thuộc về từng object — chỉ tồn tại **một bản duy nhất** dùng chung.

```java
public class Counter {
    static int totalObjects = 0; // biến static — dùng chung
    int id;                      // biến instance — riêng từng object

    public Counter() {
        totalObjects++;
        id = totalObjects;
    }

    static void printTotal() { // static method
        System.out.println("Tổng số object: " + totalObjects);
    }
}
```

**Lưu ý quan trọng:**
- Static method **không thể** truy cập trực tiếp biến/method instance (vì không gắn với object cụ thể nào).
- Static method **không thể** dùng `this` hoặc `super`.
- `main()` là static vì JVM gọi nó mà chưa có object nào được tạo.

---

## 17. Tính đóng gói (Encapsulation)

Nguyên tắc: **field nên là `private`**, truy cập qua **getter/setter public**, giúp kiểm soát dữ liệu (validate, bảo vệ tính toàn vẹn).

```java
public class BankAccount {
    private double balance;

    public double getBalance() {
        return balance;
    }

    public void deposit(double amount) {
        if (amount <= 0) {
            throw new IllegalArgumentException("Số tiền phải dương");
        }
        balance += amount;
    }

    public void withdraw(double amount) {
        if (amount > balance) {
            throw new IllegalStateException("Số dư không đủ");
        }
        balance -= amount;
    }
}
```

Nếu `balance` là `public`, bất kỳ đâu trong chương trình cũng có thể gán `account.balance = -1000000;` — phá vỡ logic nghiệp vụ. Encapsulation ngăn điều này bằng cách bắt buộc mọi thay đổi phải đi qua method có kiểm tra.

---

## 18. Tính kế thừa (Inheritance)

Class con (`subclass`) kế thừa field/method từ class cha (`superclass`) bằng `extends`. Java chỉ hỗ trợ **đơn kế thừa** (một class chỉ extends một class cha).

```java
public class Animal {
    protected String name;

    public Animal(String name) {
        this.name = name;
    }

    public void eat() {
        System.out.println(name + " đang ăn.");
    }
}

public class Dog extends Animal {
    public Dog(String name) {
        super(name); // bắt buộc gọi constructor cha đầu tiên
    }

    public void bark() {
        System.out.println(name + " sủa: Gâu gâu!");
    }
}
```

**Quy tắc quan trọng:**
- `super(...)` gọi constructor lớp cha, phải là **dòng lệnh đầu tiên** trong constructor con.
- Nếu không gọi `super(...)` tường minh, Java tự chèn `super()` (constructor không tham số) — nếu class cha không có constructor không tham số → **lỗi compile**.
- `super.method()` gọi method của lớp cha (dùng khi override nhưng vẫn muốn tận dụng logic cha).
- Từ khóa `final` trên class ngăn class đó bị kế thừa (`final class String`); trên method ngăn method đó bị override.

### Composition vs Inheritance
Nguyên tắc kinh điển: **"Favor composition over inheritance"** — ưu tiên "has-a" (chứa object khác làm field) hơn "is-a" (kế thừa) khi quan hệ không thực sự tự nhiên, để tránh phân cấp class cồng kềnh, khó bảo trì.

---

## 19. Tính đa hình (Polymorphism)

### 7.1 Runtime Polymorphism — Method Overriding

Class con định nghĩa lại method đã có ở class cha, JVM quyết định gọi phiên bản nào **tại runtime** dựa trên kiểu thực sự của object (dynamic binding).

```java
public class Animal {
    public void makeSound() {
        System.out.println("Animal phát ra âm thanh");
    }
}

public class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meo meo!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Cat(); // kiểu khai báo: Animal, kiểu thực: Cat
        a.makeSound();        // In ra "Meo meo!" — gọi theo kiểu thực tế
    }
}
```

**Quy tắc override:**
- Cùng tên method, cùng tham số (signature).
- Kiểu trả về giống hoặc là kiểu con (covariant return type).
- Không được thu hẹp phạm vi truy cập (cha `protected` → con không được `private`).
- Luôn dùng `@Override` để compiler kiểm tra giúp, tránh lỗi gõ sai tên.

### 7.2 Compile-time Polymorphism — Method Overloading

Nhiều method **cùng tên**, khác **số lượng/kiểu tham số**, được phân biệt tại compile time.

```java
public class Calculator {
    int add(int a, int b) { return a + b; }
    double add(double a, double b) { return a + b; }
    int add(int a, int b, int c) { return a + b + c; }
}
```

### 7.3 Upcasting và Downcasting

```java
Animal a = new Cat();        // upcasting — luôn an toàn, tự động
Cat c = (Cat) a;             // downcasting — cần ép kiểu tường minh
if (a instanceof Cat cat) {  // instanceof pattern (Java 16+) — an toàn hơn
    cat.meow();
}
```

---

## 20. Tính trừu tượng (Abstraction)

Abstract class dùng khi muốn định nghĩa "khung sườn" chung, có thể có method đã cài đặt sẵn lẫn method bắt buộc lớp con phải tự cài đặt.

```java
public abstract class Shape {
    protected String color;

    public Shape(String color) {
        this.color = color;
    }

    // Method trừu tượng — không có thân, bắt buộc lớp con override
    public abstract double calculateArea();

    // Method thường — có thể dùng chung
    public void printColor() {
        System.out.println("Màu: " + color);
    }
}

public class Circle extends Shape {
    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}
```

**Đặc điểm:**
- **Không thể** dùng `new Shape(...)` để tạo object trực tiếp từ abstract class.
- Class chứa ít nhất một abstract method **bắt buộc** phải khai báo `abstract`.
- Abstract class **có thể** có constructor (được gọi qua `super()` từ lớp con), field, method đã cài đặt đầy đủ.

---

## 21. Interface vs Abstract Class

Interface định nghĩa **hợp đồng (contract)** — "làm được gì" mà không quan tâm "làm như thế nào".

```java
public interface Flyable {
    void fly(); // mặc định là public abstract

    // Từ Java 8: default method — có thân, không bắt buộc override
    default void land() {
        System.out.println("Đang hạ cánh...");
    }

    // Từ Java 8: static method
    static Flyable createDefault() {
        return () -> System.out.println("Bay mặc định"); // lambda
    }
}

public class Bird implements Flyable {
    @Override
    public void fly() {
        System.out.println("Chim đang bay bằng cánh");
    }
}
```

### Bảng so sánh

| Tiêu chí | Abstract Class | Interface |
|---|---|---|
| Kế thừa/thực thi | `extends` (đơn kế thừa) | `implements` (đa kế thừa — 1 class implements nhiều interface) |
| Constructor | Có | Không |
| Field | Có thể mọi loại | Mặc định `public static final` (hằng số) |
| Method thường | Có | Chỉ qua `default`/`static` (Java 8+) |
| Khi nào dùng | Các class có quan hệ "is-a" gần, chia sẻ code chung | Định nghĩa năng lực (capability) cho các class không liên quan huyết thống |

**Quy tắc chọn:** Nếu chỉ cần định nghĩa "class này làm được gì" → interface. Nếu cần chia sẻ code/state chung giữa các class có quan hệ họ hàng rõ ràng → abstract class. Nhiều dự án thực tế kết hợp cả hai.

---

## 22. Access Modifiers

| Modifier | Cùng class | Cùng package | Class con khác package | Khác package |
|---|:---:|:---:|:---:|:---:|
| `private` | ✅ | ❌ | ❌ | ❌ |
| (default/package-private) | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

Nguyên tắc: **luôn chọn phạm vi truy cập hẹp nhất có thể** ("principle of least privilege") — field nên `private`, chỉ mở rộng khi thực sự cần.

---

## 23. Package

Package tổ chức class theo thư mục logic, tránh trùng tên, hỗ trợ access control.

```java
package com.ptit.studentmanagement.model;

import java.util.List;
import java.util.ArrayList;

public class Student { ... }
```

Quy ước đặt tên: chữ thường, theo domain ngược (`com.company.project.module`). Cấu trúc thư mục phải khớp với package (`com/ptit/studentmanagement/model/Student.java`).

---

## 24. Exception Handling trong OOP

Exception cũng là object, tuân theo phân cấp kế thừa từ `Throwable`.

```
Throwable
├── Error (lỗi hệ thống nghiêm trọng, không nên catch)
└── Exception
    ├── RuntimeException (unchecked — không bắt buộc try/catch)
    │   ├── NullPointerException
    │   ├── ArrayIndexOutOfBoundsException
    │   └── IllegalArgumentException
    └── Checked Exception (bắt buộc try/catch hoặc throws)
        ├── IOException
        └── SQLException
```

### Tự định nghĩa Exception (áp dụng inheritance)

```java
public class InsufficientFundsException extends RuntimeException {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

// Sử dụng
public void withdraw(double amount) {
    if (amount > balance) {
        throw new InsufficientFundsException("Số dư không đủ để rút " + amount);
    }
}
```

```java
try {
    account.withdraw(1000000);
} catch (InsufficientFundsException e) {
    System.out.println("Lỗi: " + e.getMessage());
} finally {
    System.out.println("Luôn chạy dù có exception hay không");
}
```

---

## 25. Generics

Generics cho phép viết code hoạt động với nhiều kiểu dữ liệu mà vẫn đảm bảo type-safety tại compile time.

```java
public class Box<T> {
    private T content;

    public void set(T content) { this.content = content; }
    public T get() { return content; }
}

Box<String> stringBox = new Box<>();
stringBox.set("Hello");

Box<Integer> intBox = new Box<>();
intBox.set(123);
```

```java
// Generic method
public static <T> T findMax(List<T> list, Comparator<T> comparator) {
    T max = list.get(0);
    for (T item : list) {
        if (comparator.compare(item, max) > 0) max = item;
    }
    return max;
}

// Bounded type parameter
public static <T extends Comparable<T>> T findMax(List<T> list) {
    T max = list.get(0);
    for (T item : list) {
        if (item.compareTo(max) > 0) max = item;
    }
    return max;
}
```

---

## 26. Object class & các phương thức quan trọng

Mọi class trong Java ngầm định `extends Object`. Các method nên override đúng cách:

```java
public class Student {
    private String id;
    private String name;

    @Override
    public String toString() {
        return "Student{id='" + id + "', name='" + name + "'}";
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof Student)) return false;
        Student other = (Student) o;
        return id.equals(other.id);
    }

    @Override
    public int hashCode() {
        return id.hashCode();
    }
}
```

**Quy tắc bắt buộc:** nếu override `equals()`, **phải** override `hashCode()` theo — nếu không, object sẽ hoạt động sai trong `HashMap`, `HashSet` (hai object `equals()` nhau nhưng khác `hashCode()` sẽ bị coi là khác nhau khi lưu trong tập hợp dựa trên hash).

---

## 27. Nguyên lý SOLID

Bộ nguyên tắc thiết kế OOP giúp code linh hoạt, dễ mở rộng — rất hay được hỏi khi phỏng vấn:

| Nguyên tắc | Ý nghĩa |
|---|---|
| **S** — Single Responsibility | Một class chỉ nên có một lý do để thay đổi (một trách nhiệm) |
| **O** — Open/Closed | Mở để mở rộng, đóng để sửa đổi (thêm tính năng bằng kế thừa/interface, không sửa code cũ) |
| **L** — Liskov Substitution | Class con phải thay thế được class cha mà không phá vỡ chương trình |
| **I** — Interface Segregation | Nhiều interface nhỏ, chuyên biệt tốt hơn một interface lớn ôm đồm |
| **D** — Dependency Inversion | Phụ thuộc vào abstraction (interface), không phụ thuộc vào implementation cụ thể |

---

## 28. Design Patterns cơ bản

### Singleton — đảm bảo chỉ có một instance duy nhất

```java
public class DatabaseConnection {
    private static DatabaseConnection instance;

    private DatabaseConnection() {} // constructor private

    public static DatabaseConnection getInstance() {
        if (instance == null) {
            instance = new DatabaseConnection();
        }
        return instance;
    }
}
```

### Factory — tạo object mà không lộ logic khởi tạo

```java
public interface Notification {
    void notifyUser();
}

public class EmailNotification implements Notification {
    public void notifyUser() { System.out.println("Gửi email"); }
}

public class NotificationFactory {
    public static Notification create(String type) {
        return switch (type) {
            case "EMAIL" -> new EmailNotification();
            default -> throw new IllegalArgumentException("Không hỗ trợ: " + type);
        };
    }
}
```

### Strategy — thay đổi thuật toán linh hoạt tại runtime

```java
public interface PaymentStrategy {
    void pay(double amount);
}

public class CreditCardPayment implements PaymentStrategy {
    public void pay(double amount) { System.out.println("Trả " + amount + " bằng thẻ tín dụng"); }
}

public class Order {
    private PaymentStrategy strategy;
    public void setStrategy(PaymentStrategy strategy) { this.strategy = strategy; }
    public void checkout(double amount) { strategy.pay(amount); }
}
```

*(Đây chỉ là 3 pattern nền tảng — khi vững OOP, nên học tiếp Builder, Observer, Decorator, Adapter.)*

---

## 29. Lỗi thường gặp

- **Quên gọi `super()`** khi class cha không có constructor mặc định → lỗi compile.
- **Override nhưng quên `@Override`** → gõ sai tên method thành overload mới, logic đa hình không hoạt động như mong đợi.
- **Override `equals()` mà quên `hashCode()`** → object "biến mất" khi dùng trong `HashSet`/`HashMap`.
- **Lạm dụng kế thừa** cho quan hệ không phải "is-a" thực sự → nên dùng composition.
- **Field không `private`** → phá vỡ encapsulation, khó kiểm soát trạng thái object.
- **Gọi method non-static từ static context** (ví dụ trong `main`) mà chưa tạo object → lỗi compile.
- **Nhầm lẫn overloading và overriding**: overloading xảy ra compile-time, cùng class hoặc class không có quan hệ kế thừa; overriding xảy ra runtime, giữa lớp cha–con.

---

## 30. Lộ trình luyện tập

1. **Tuần 1:** Class, Object, Constructor, `this`/`static` — viết class `Student`, `Product`, `BankAccount` với đầy đủ constructor overload.
2. **Tuần 2:** Encapsulation + Inheritance — xây hệ phân cấp `Animal → Dog/Cat/Bird`, thêm validate trong setter.
3. **Tuần 3:** Polymorphism + Abstraction — thiết kế hệ `Shape` (abstract) với `Circle`, `Rectangle`, `Triangle`, tính diện tích/chu vi qua đa hình.
4. **Tuần 4:** Interface + Exception tự định nghĩa — mô phỏng hệ thống quản lý đơn hàng có `PaymentStrategy`, custom exception khi lỗi thanh toán.
5. **Tuần 5:** Generics + Object methods — viết một `Box<T>` generic, override `equals`/`hashCode`/`toString` đúng chuẩn, thử dùng trong `HashSet`.
6. **Tuần 6:** SOLID + 3 design pattern trên — refactor lại project ở tuần 4 theo SOLID.
7. **Dự án tổng hợp:** Xây dựng một hệ thống quản lý nhỏ (quản lý sinh viên / quản lý thư viện / quản lý cửa hàng) áp dụng đầy đủ 4 tính chất OOP + ít nhất 1 design pattern — đây là bài tập kinh điển để tổng hợp kiến thức trước khi học Spring Boot.

---

## Tài liệu tham khảo thêm

- Oracle Java Tutorials — phần "Object-Oriented Programming Concepts"
- Sách *Head First Java* (chương OOP) — trực quan, dễ hiểu cho người mới
- Sách *Effective Java* (Joshua Bloch) — best practices nâng cao sau khi đã nắm chắc nền tảng
- Sách *Design Patterns* (Gang of Four) — khi đã vững OOP cơ bản

---

*File này được tạo để tự học — có thể chỉnh sửa, bổ sung ví dụ code của riêng bạn khi luyện tập.*
