# [BUỔI 3] CÁCH JAVA LƯU TRỮ DỮ LIỆU

<!-- TOC -->
* [[BUỔI 3] CÁCH JAVA LƯU TRỮ DỮ LIỆU](#bui-3-cch-java-lu-tr-d-liu)
  * [1. Cách Java lưu trữ dữ liệu](#1-cch-java-lu-tr-d-liu)
    * [Tổng quan các kiểu dữ liệu](#tng-quan-cc-kiu-d-liu)
    * [1.1 Kiểu dữ liệu nguyên thủy](#11-kiu-d-liu-nguyn-thy)
    * [1.2 Kiểu dữ liệu tham chiếu](#12-kiu-d-liu-tham-chiu)
    * [1.3 Lớp Object trong Java](#13-lp-object-trong-java)
    * [1.4 Lớp Wrapper trong Java](#14-lp-wrapper-trong-java)
      * [Autoboxing và Unboxing trong Java](#autoboxing-v-unboxing-trong-java)
        * [Autoboxing](#autoboxing)
        * [Unboxing](#unboxing)
  * [2. Các phương thức khởi tạo trong Java (từ khóa super và this)](#2-cc-phng-thc-khi-to-trong-java--t-kha-super-v-this-)
    * [2.1 Constructor](#21-constructor)
      * [Hàm khởi tạo (constructor) là gì?](#hm-khi-to--constructor--l-g)
      * [2.1.1 Hàm khởi tạo không có tham số (no-argument constructor)](#211-hm-khi-to-khng-c-tham-s--no-argument-constructor-)
      * [2.1.2 Hàm khởi tạo có tham số (parameterized constructor)](#212-hm-khi-to-c-tham-s--parameterized-constructor-)
      * [2.1.3 Hàm khởi tạo mặc định (default constructor)](#213-hm-khi-to-mc-nh--default-constructor-)
    * [2.2 Từ khóa super](#22-t-kha-super)
      * [2.2.1 Gọi trực tiếp constructor của lớp cha gần nhất.](#221-gi-trc-tip-constructor-ca-lp-cha-gn-nht)
      * [2.2.2 Gọi trực tiếp biến của lớp cha gần nhất](#222-gi-trc-tip-bin-ca-lp-cha-gn-nht)
      * [2.2.3 Gọi trực tiếp phương thức của lớp cha gần nhất](#223-gi-trc-tip-phng-thc-ca-lp-cha-gn-nht)
    * [2.3 Từ khóa this](#23-t-kha-this)
  * [3. Garbage collectors trong Java](#3-garbage-collectors-trong-java)
    * [Garbage collectors là gì?](#garbage-collectors-l-g)
    * [Cách hoạt động của Garbage collectors](#cch-hot-ng-ca-garbage-collectors)
  * [4. Pass by value trong Java](#4-pass-by-value-trong-java)
<!-- TOC -->

## 1. Cách Java lưu trữ dữ liệu

### Tổng quan các kiểu dữ liệu

Java có 2 loại kiểu dữ liệu:
+ Các kiểu dữ liệu nguyên thủy (Primitive Data Types)
+ Các kiểu dữ liệu đối tượng (Non-Primitive Data Types)

### 1.1 Kiểu dữ liệu nguyên thủy

Có 8 kiểu dữ liệu nguyên thủy (Primitive Data type) đó là: boolean, byte, char, short, int, long, float, double.

![](https://user-images.githubusercontent.com/29374426/123082975-cc497780-d449-11eb-8315-b4e53f2257fe.png)

>Đặc điểm của các biến có kiểu nguyên thủy là vùng nhớ của chúng được cấp phát ở phần stack. Do vậy việc truy xuất vào một biến kiểu nguyên thủy rất nhanh.

### 1.2 Kiểu dữ liệu tham chiếu

Trong Java có 3 kiểu dữ liệu tham chiếu

|  Kiểu dữ liệu   |   Mô tả  |
|-----|-----|
|  Mảng (Array)   |Tập hợp các dữ liệu cùng kiểu.     |
|Lớp (Class)|Là sự cài đặt mô tả về một đối tượng trong bài toán.|
|Giao diện (Interface)|Là một lớp thuần trừu tượng được tạo ra cho phép cài đặt đa thừa kế trong Java.|

Đặc điểm của các biến kiểu tham chiếu là nó chứa `địa chỉ` của đối tượng mà nó trỏ đến.

>Vùng nhớ của biến tham chiếu được cấp phát ở vùng nhớ stack còn vùng nhớ của đối tượng được cấp phát ở vùng nhớ heap. Việc truy xất vào vùng nhớ heap chậm hơn truy xất vào vùng nhớ stack tuy nhiên java có cơ chế cho phép truy cập vào vùng nhớ heap với tốc độ xấp xỉ bằng tốc độ truy cập vào vùng nhớ stack.

### 1.3 Lớp Object trong Java

Mặc định lớp Object là lớp cha của tất cả các lớp trong java. Nói cách khác nó là một lớp cao nhất trong java.

![](https://viettuts.vn/images/java/lop-object-trong-java.jpg)

Sử dụng lớp Object là hữu ích nếu bạn muốn tham chiếu bất kỳ đối tượng nào mà bạn chưa biết kiểu dữ liệu của đối tượng đó. Chú ý rằng biến tham chiếu của lớp cha có thể tham chiếu đến đối tượng của lớp con được gọi là upcasting.

Ví dụ: giả sử phương thức getObject() trả về một đối tượng nhưng nó có thể là bất kỳ kiểu nào như Employee,Student, ... chúng ta có thể sử dụng biến tham chiếu của lớp Object để tham chiếu tới đối tượng đó.

```Java
Object obj = getObject();
```

### 1.4 Lớp Wrapper trong Java

Lớp Wrapper trong Java là loại lớp cung cấp một cơ chế để chuyển đổi loại dữ liệu nguyên thủy thành đối tượng và ngược lại. 

Khi một lớp Wrapper được tạo ra, một tệp mới sẽ được tạo ra và ở đó, chúng ta sẽ lưu trữ các kiểu dữ liệu nguyên thủy. Đối tượng của lớp Wrapper bọc hoặc giữ kiểu dữ liệu nguyên thủy tương ứng của nó.

Quá trình chuyển đổi các kiểu dữ liệu nguyên thủy thành một đối tượng gọi là boxing. Trong khi sử dụng một lớp wrapper, bạn chỉ cần truyền giá trị của kiểu dữ liệu nguyên thủy cho phương thức khởi tạo của lớp Wrapper.

#### Autoboxing và Unboxing trong Java

##### Autoboxing

Quá trình tự động chuyển đổi các kiểu dữ liệu nguyên thủy thành các đối tượng lớp Wrapper tương ứng được gọi là Autoboxing trong Java. Đây là Autoboxing vì điều này được thực hiện tự động bởi trình biên dịch Java. Ví dụ: char thành Character, int thành Integer, long thành Long, double thành Double, float thành Float, boolean thành Boolean, byte thành Byte và short thành Short.

Ví dụ:

```Java
public class BoxingSample {
    public static void main(String args[]) {
        int num = 1;
        Integer obj1 = new Integer(num);// Boxing
        Integer obj2 = 2;             // Boxing
    }
}
```

##### Unboxing

Java Unboxing là quá trình ngược lại của Autoboxing. Quá trình chuyển đổi đối tượng lớp wrapper thành kiểu dữ liệu nguyên thủy tương ứng của nó được gọi là Java Unboxing.

```Java
public class UnboxingSample {
    public static void main(String args[]) {
        Integer obj = new Integer(1);
        int num = obj ; // unboxing
    }
}
```

## 2. Các phương thức khởi tạo trong Java (từ khóa super và this)

### 2.1 Constructor

#### Hàm khởi tạo (constructor) là gì?
Hàm khởi tạo (constructor) trong Java là một hàm có tên giống với tên lớp. Hàm này được gọi khi khởi tạo đối tượng. Hàm khởi tạo không có kiểu trả về.

Ví dụ:

```java
class Main {
    private String name;

    //constructor
    Main() {
        System.out.println("Constructor Called:");
        name = "Gochocit.com";
    }

    public static void main(String[] args) {
        //hàm khởi tạo được gọi khi khởi tạo đối tượng
        Main obj = new Main();
        System.out.println("The name is " + obj.name);
    }
}
```

Kết quả

```java
Constructor Called:
The name is Gochocit.com
```
Lớp Main có một hàm khởi tạo là Main(). Hàm này khởi tạo giá trị cho thuộc tính name. Khởi tạo đối tượng với hàm khởi tạo:

```java
Main obj = new Main();
```

Khi đó, đối tượng sẽ được phát vùng nhớ trên bộ nhớ heap để lưu trữ dữ liệu của đối tượng đó.

Trong Java, hàm khởi tạo có thể được chia thành 3 loại:

1. Hàm khởi tạo không có tham số (no-argument constructor)

2. Hàm khởi tạo có tham số (parameterized constructor)

3. Hàm khởi tạo mặc định (default constructor)

#### 2.1.1 Hàm khởi tạo không có tham số (no-argument constructor)

Cú pháp:
```java
class <Tênlớp>{
     accessmodifier <Tênlớp>(){
         //thân hàm khởi tạo không có tham số
     }
}
```
Ví dụ:

```java
class Company {
    String name;

    //public constructor
    public Company() {
        name = "Gochocit.com";
    }
}

class Main {
  public static void main(String[] args) {
    // object is created in another class
    Company obj = new Company();
    System.out.println("Company name = " + obj.name);
  }
}
```

#### 2.1.2 Hàm khởi tạo có tham số (parameterized constructor)

Hàm khởi tạo trong Java có thể có 1 hoặc nhiều tham số.

```java
class Company {
    String name;

    //public constructor
    public Company(String cName) {
        name = cName;
        System.out.println("Company name is " + name);
    }
}

class Main {
  public static void main(String[] args) {
      Company com1 = new Company("Google");
      Company com2 = new Company("Apple");
      Company com3 = new Company("Facebook");
  }
}
```

#### 2.1.3 Hàm khởi tạo mặc định (default constructor)

Nếu trong lớp không có hàm khởi tạo này, trình biên dịch Java sẽ tự động tạo ra một hàm khởi tạo không có tham số. Hàm khởi tạo này gọi là hàm khởi tạo mặc định (default constructor).

```java
class Main {
  int a;
  boolean b;

  public static void main(String[] args) {

    // A default constructor is called
    Main obj = new Main();

    System.out.println("Default Value:");
    System.out.println("a = " + obj.a);
    System.out.println("b = " + obj.b);
  }
}
```

Trong ví dụ trên, lớp Main không có hàm khởi tạo nào được định nghĩa. Trình biên dịch Java sẽ tự động tạo ra hàm default constructor. Hàm này sẽ tự động khởi tạo các thuộc tính với các giá trị mặc định.

| Kiểu dữ liệu | Giá trị mặc định    |
|--------------|---------------------|
| boolean      | false               |
| byte         | 0                   |
| short        | 0                   |
| int          | 0                   |
| long         | 0L                  |
| char         | \u0000              |
| float        | 0.0f                |
| double       | 0.0d                |
| object       | tham chiếu đến null |

### 2.2 Từ khóa super

Từ khóa super trong java là một biến tham chiếu được sử dụng để tham chiếu trực tiếp đến `đối tượng của lớp cha gần nhất`.

Bất cứ khi nào bạn tạo ra instance (thể hiện) của lớp con, một instance của lớp cha được tạo ra ngầm định, nghĩa là được tham chiếu bởi biến super.

Từ khóa super có 3 cách sử dụng sau:

- Gọi trực tiếp hàm dựng (**constructor**) của lớp cha gần nhất.
- Gọi trực tiếp thuộc tính (**field**) của lớp cha gần nhất.
- Gọi trực tiếp phương thức (**method**) của lớp cha gần nhất.

#### 2.2.1 Gọi trực tiếp constructor của lớp cha gần nhất.

Ví dụ:

Parent.java:

```java
public class Parent {
     
    private String website;
     
    public Parent() {
        System.out.println("This is parent");
        print();
    }
     
    public Parent(String website) {
        this.website = website;
        System.out.println("This is parent");
        print();
    }
     
    public void print() {
        System.out.println("Website = " + website);
    }
}
```

Child.java

```java
public class Child extends Parent {

    public Child() {
        System.out.println("This is child");
    }

    public Child(String website) {
        super(website);
        System.out.println("This is child");
    }

    public static void main(String[] args) {
        Child child1 = new Child();
        System.out.println("---");
        Child child2 = new Child("gpcoder.com");
    }
}
```

Kết quả:
```java
This is parent
Website = null
This is child
---
This is parent
Website = gpcoder.com
This is child
```

#### 2.2.2 Gọi trực tiếp biến của lớp cha gần nhất

Ví dụ:

Parent.java
```java
public class Parent {
     
    public String website = "gpcoder.com";
    public String subject = "OOP";
     
    public Parent() {
         
    }
}
```

Child.java
```java
public class Child extends Parent {
     
    public String website = "https://gpcoder.com";
     
    public Child() {
         
    }
     
    public void printParent() {
        System.out.println("Short link: " + super.website);
        System.out.println("Subject " + subject);
    }
     
    public void printChild() {
        System.out.println("Full link: " + website);
        System.out.println("Subject " + subject);
    }
     
    public static void main(String[] args) {
        Child child = new Child();
        child.printParent();
        System.out.println("---");
        child.printChild();
    }
}
```
Kết quả:

```java
Short link: gpcoder.com
Subject OOP
---
Full link: https://gpcoder.com
Subject OOP
```
#### 2.2.3 Gọi trực tiếp phương thức của lớp cha gần nhất

Ví dụ:

Parent.java

```java
public class Parent {
     
    private String website;
     
    public Parent(String website) {
        this.website = website;
    }
     
    public void print() {
        System.out.println("Website = " + website);
    }
     
    public void welcome() {
        System.out.println("Welcome to gpcoder.com");
    }
}
```

Child.java

```java
public class Child extends Parent {
     
    public Child(String website) {
        super(website);
    }
 
    public void printChild1() {
        print();
    }
 
    public void printChild2() {
        super.print();
        welcome();
    }
     
    public void print() {
        System.out.println("Subject = OOP");    
    }
     
    public static void main(String[] args) {
        Child child = new Child("gpcoder.com");
        child.printChild1();
        System.out.println("---");
        child.printChild2();
    }
}
```
Kết quả:
```java
Subject = OOP
---
Website = gpcoder.com
Welcome to gpcoder.com
```
### 2.3 Từ khóa this

Từ khóa this trong java là một biến tham chiếu được sử dụng để tham chiếu tới đối tượng của lớp hiện tại.

Trong java, Từ khóa this có 6 cách sử dụng như sau:
Từ khóa this có thể được dùng để tham chiếu tới biến instance của lớp hiện tại.
- this() có thể được dùng để gọi Constructor của lớp hiện tại.
- Từ khóa this có thể được dùng để gọi phương thức của lớp hiện tại. 
- Từ khóa this có thể được truyền như một tham số trong phương thức. 
- Từ khóa this có thể được truyền như một tham số trong phương Constructor. 
- Từ khóa this có thể được dùng để trả về instance của lớp hiện tại

## 3. Garbage collectors trong Java

Trong Java, rác (garbage) có nghĩa là một đối đối tượng không được tham chiếu đến nữa và bộ thu gom rác (Garbage collector) có nhiệm vụ hủy các đối tượng đó để giải phóng bộ nhớ.     

### Garbage collectors là gì?

Garbage Collectors được định nghĩa như là một quá trình tự động thực thi nhiệm vụ quản lý bộ nhớ. Code Java được dịch sang bytecode rồi chạy trên máy ảo Java hay viết tắt là JVM. Trong quá trình chạy chương trình, các đối tượng được tạo ở vùng nhớ heap, một phần bộ nhớ dành cho chương trình. Sau cùng, sẽ có một vài đối tượng mà chương trình không cần dùng đến. Các đối tượng này sẽ được garbage collector truy tìm và xóa bỏ để thu hồi lại dung lượng bộ nhớ.

### Cách hoạt động của Garbage collectors

- B1: Các Object không được tham chiếu sẽ được đánh dấu sẵn sàng để được dọn rác. 
- B2: Trình thu gom rác sẽ tiến hành xóa các Object đó. 
- B3: Vùng nhớ của các Object còn lại sẽ được nén lại và nằm liền kề nhau trong bộ nhớ Heap. Quá trình này sẽ giúp việc cấp phát bộ nhớ cho Object mới dễ dàng hơn.

Ở vùng nhớ Heap được chia làm 3 vùng nhớ nhỏ hơn, tạm gọi là Young generation, Old generation và Permanent generation.

Young generation: được chia thành nhiều vùng nhớ nhỏ hơn là Eden(khởi tạo) và Survivor(sống sót). Các Object vừa được khởi tạo sẽ nằm ở vùng Eden, sau chu kì quét đầu tiên nếu Object đó còn tồn tại thì sẽ được chuyển sang vùng Survivor. Tại đây các Object được Garbage Collectors theo dõi liên tục, nếu  như qua nhiều chu kì quét mà Object vẫn còn được sử dụng thì lúc này Object sẽ được chuyển sang vùng nhớ thứ thứ hai.

Old generation: là nơi chứa những Object tòn tại đủ "lâu", còn "lâu" như thế nào thì lại tùy thuộc vào thuật toán của từng bộ Garbage Collectors.

Permanent generation: không chứa Object mà đây là nơi để chứa các metadata của JVM như các class và method của ứng dụng. Do đó nếu các class và method không còn được sử dụng nữa thì Garbage Collectors sẽ coi chúng là "rác" và dọn dẹp nó.

## 4. Pass by value trong Java

Trong Java chỉ có truyền tham trị, không truyền tham trị tham chiếu. Điều này có nghĩa là một bản sao của biến được tạo ra và phương thức nhận bản sao đó. Các nhiệm vụ được thực hiện trong phương thức không ảnh hưởng đến đối tượng gọi.

Ví dụ chúng ta gọi một phương thức và truyền một giá trị cho phương thức đó, việc thay đổi giá trị chỉ có hiệu lực trong phương thức được gọi, không có hiệu lực bên ngoài phương thức.

```java
public class hehe{
    public static void main(String[] args) {
        int num = 4;
        lt(num);
        System.out.println(num); //Output: 4
    }
    public void lt(int num)
    {
        num = num*num;
    }
}
```

