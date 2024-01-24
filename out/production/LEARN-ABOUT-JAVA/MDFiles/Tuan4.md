# [BUỔI 4] MỌI THỨ ĐỀU LÀ ĐỐI TƯỢNG

<!-- TOC -->
* [[BUỔI 4] MỌI THỨ ĐỀU LÀ ĐỐI TƯỢNG](#bui-4-mi-th-u-l-i-tng)
  * [1. Tính đóng gói trong java](#1-tnh-ng-gi-trong-java)
  * [2. Tính kế thừa trong java](#2-tnh-k-tha-trong-java)
    * [Cú pháp của kế thừa trong java](#c-php-ca-k-tha-trong-java)
    * [Các kiểu kế thừa trong java](#cc-kiu-k-tha-trong-java)
    * [2.1 Đơn kế thừa](#21-n-k-tha)
    * [2.2 Kế thừa nhiều cấp](#22-k-tha-nhiu-cp)
    * [2.3 Kế thừa thứ bậc](#23-k-tha-th-bc)
  * [3. Tính đa hình trong java](#3-tnh-a-hnh-trong-java)
    * [3.1 Nạp chồng phương thức](#31-np-chng-phng-thc)
    * [3.2 Ghi đè phương thức](#32-ghi--phng-thc)
<!-- TOC -->

## 1. Tính đóng gói trong java

Tính đóng gói hay tính bao đóng (Encapsulation) là một trong bốn tính chất cơ bản của lập trình hướng đối tượng trong Java.

Tính đóng gói là kỹ thuật ẩn giấu thông tin không liên quan và hiện thị ra thông liên quan. Mục đích chính của đóng gói trong java là giảm thiểu mức độ phức tạp phát triển phần mềm.

Tính đóng gói là kỹ thuật tạo một trường của lớp private và cung cấp khả năng truy cập trường này qua các phương thức public. Nếu một trường được khai báo là private, nó không thể được truy cập bởi bên ngoài lớp, do đó có thể che dấu các trường có lớp này. Vì lý do này, tính đóng gói được ám chỉ như việc dấu dữ liệu (data hiding).

**Để đạt được đóng gói trong Java chúng ta cần:**

>Khai báo các biến của một lớp là `private.`

>Cung cấp phương thức setter và getter là public để có thể sửa đổi và xem các giá trị biến.

VD:

```java
public class Student {
    private String name;
 
    public String getName() {
        return name;
    }
 
    public void setName(String name) {
        this.name = name;
    }
}
```

```java
public class Main {
 
    public static void main(String[] args) {
        Student s = new Student();
        s.setName("Vân");
        System.out.println(s.getName());
    }
 
}
```

Kết quả:
```java
Vân
```

**Lợi ích của đóng gói trong java**

>Có thể tạo lớp read-only hoặc write-only bằng việc cài đặt phương thức setter hoặc getter.

>Có thể kiểm soát đối với dữ liệu.

## 2. Tính kế thừa trong java

**Kế thừa** trong java là sự liên quan giữa hai class với nhau, trong đó có class cha (superclass) và class con (subclass). Khi kế thừa class con được hưởng tất cả các phương thức và thuộc tính của class cha. Tuy nhiên, nó chỉ được truy cập các thành viên public và protected của class cha. Nó không được phép truy cập đến thành viên private của class cha.

Tư tưởng của kế thừa trong java là có thể tạo ra một class mới được xây dựng trên các lớp đang tồn tại. Khi kế thừa từ một lớp đang tồn tại bạn có sử dụng lại các phương thức và thuộc tính của lớp cha, đồng thời có thể khai báo thêm các phương thức và thuộc tính khác.

### Cú pháp của kế thừa trong java

Sử dụng từ khóa extends để kế thừa.

```java
class Subclass-name extends Superclass-name {  
   //methods and fields
}
```

VD:

```java
public class Teacher {
    float score = 4;
}
```

```java
public class Student extends Teacher{

    float diem = 10;

    public static void main(String[] args) {
        Student van = new Student();
        System.out.println("Teacher says: You got " + van.score + " in the exam");
        System.out.println("Student says: No, I got " + van.diem);
    }
}
```

Kết quả:
```java
Teacher says: You got 4.0 in the exam
Student says: No, I got 10.0
```

### Các kiểu kế thừa trong java

Có 3 kiểu kế thừa trong java đó là đơn kế thừa, kế thừa nhiều cấp, kế thừa thứ bậc.

Khi một class được kế thừa từ nhiều class đươc gọi là đa kế thừa. Trong java, đa kế thừa chỉ được support thông qua interface.

![](https://viettuts.vn/images/java/cac-kieu-ke-thua.jpg)

>Chú ý: Đa kế thừa trong java không được support thông qua class.

### 2.1 Đơn kế thừa

Một lớp chỉ được kế thừa từ đúng một lớp khác. Hay nói cách khác, lớp con chỉ có duy nhất một lớp cha.

VD:

```java
class Animal {
    void eat() {
        System.out.println("eating...");
    }
}
```
```java
class Dog extends Animal {
    void bark() {
        System.out.println("barking...");
    }
    public static void main(String args[]) {
        Dog d = new Dog();
        d.bark();
        d.eat();
    }
}
```

Kết quả:
```java
barking...
eating...
```

### 2.2 Kế thừa nhiều cấp

Trong kiểu thừa kế này, một lớp dẫn xuất được tạo từ một lớp dẫn xuất khác.

```java
class Animal {
    void eat() {
        System.out.println("eating...");
    }
}
 
class Dog extends Animal {
    void bark() {
        System.out.println("barking...");
    }
}
 
class BabyDog extends Dog {
    void weep() {
        System.out.println("weeping...");
    }
}
 
public class TestInheritance2 {
    public static void main(String args[]) {
        BabyDog d = new BabyDog();
        d.weep();
        d.bark();
        d.eat();
    }
}
```
Kết quả:
```java
weeping...
barking...
eating...
```

### 2.3 Kế thừa thứ bậc

Đây là trường hợp sẽ có nhiều lớp con được kế thừa từ một lớp cha duy nhất.

```java
class Animal {
    void eat() {
        System.out.println("eating...");
    }
}
 
class Dog extends Animal {
    void bark() {
        System.out.println("barking...");
    }
}
 
class Cat extends Animal {
    void meow() {
        System.out.println("meowing...");
    }
}
 
public class TestInheritance3 {
    public static void main(String args[]) {
        Cat c = new Cat();
        c.meow();
        c.eat();
        // c.bark(); // compile error
    }
}
```

Kết quả:
```java
meowing...
eating...
```

## 3. Tính đa hình trong java

**Tính đa hình (polymorphism)** là một trong bốn tính chất cơ bản của lập trình hướng đối tượng trong Java.

**Tính đa hình** là khả năng một đối tượng có thể thực hiện một tác vụ theo nhiều cách khác nhau.

Trong Java, chúng ta sử dụng nạp chồng phương thức (method overloading) và ghi đè phương thức (method overriding) để có tính đa hình.


### 3.1 Nạp chồng phương thức

Nếu một lớp có nhiều phương thức cùng tên nhưng khác nhau về kiểu dữ liệu hoặc số lượng các tham số, thì đó là **nạp chồng phương thức (Method Overloading)**.

Sử dụng nạp chồng phương thức giúp tăng khả năng đọc hiểu chương trình.

Nạp chồng phương thức được sử dụng để thu được `tính đa hình lúc biên dịch (compile)`.

>Có 2 cách nạp chồng phương thức trong java:
>
>- Thay đổi số lượng các tham số
>
>- Thay đổi kiểu dữ liệu của các tham số

VD1: Thay đổi số lượng các tham số

```java
class Adder {
    static int add(int a, int b) {
        return a + b;
    }
 
    static int add(int a, int b, int c) {
        return a + b + c;
    }
}
 
class TestOverloading1 {
    public static void main(String[] args) {
        System.out.println(Adder.add(5, 5));
        System.out.println(Adder.add(5, 5, 5));
    }
}
```

Kết quả:
```java
10
15
```

VD2: Thay đổi kiểu dữ liệu của các tham số

```java
class Adder {
    static int add(int a, int b) {
        return a + b;
    }
    static double add(double a, double b) {
        return a + b;
    }
}
```
```java
class TestOverloading2 {
    public static void main(String[] args) {
        System.out.println(Adder.add(5, 5));
        System.out.println(Adder.add(4.3, 5.6));
    }
}
```
Kết quả:
```java
10
9.9
```
### 3.2 Ghi đè phương thức

**Ghi đè phương thức** trong java xảy ra nếu lớp con có phương thức giống lớp cha.

Nói cách khác, nếu lớp con cung cấp sự cài đặt cụ thể cho phương thức đã được cung cấp bởi một lớp cha của nó được gọi là ghi đè phương thức (method overriding) trong java.

Ghi đè phương thức được sử dụng để thu được `tính đa hình tại runtime`.

>Nguyên tắc ghi đè phương thức:
>
>- Phương thức phải có tên giống với lớp cha.
>- Phương thức phải có tham số giống với lớp cha.
>- Lớp con và lớp cha có mối quan hệ kế thừa.

VD:

```java
class Vehicle {
    void run() {
        System.out.println("Vehicle is running");
    }
}
```
```java
class Bike extends Vehicle {
    void run() {
        System.out.println("Bike is running safely");
    }
 
    public static void main(String args[]) {
        Bike obj = new Bike();
        obj.run();
    }
 
}
```

Kết quả:
```java
Bike is running safely
```

