# [BUỔI 7] - INTERFACE VÀ TRỪU TƯỢNG 

## 1. Interface
Interface là một kiểu dữ liệu tham chiếu trong Java. Nó là tập hợp các phương thức abstract (trừu tượng). Khi một lớp kế thừa interface, thì nó sẽ kế thừa những phương thức abstract của interface đó.

### Một số đặc điểm của interface:

- Các phương thức trong interface đều là các phương thức trừu tượng.
- Interface là một kỹ thuật để thu được tính trừu tượng hoàn toàn và đa kế thừa trong Java.
- Interface luôn luôn có modifier là: **public interface**, cho dù bạn có khai báo rõ hay không.
- Nếu có các trường (field) thì chúng đều là: **public static final**, cho dù bạn có khai báo rõ hay không.
- Các method của nó đều là method trừu tượng, nghĩa là không có thân hàm, và đều có modifier là: **public abstract**, cho dù bạn có khai báo hay không.
- Interface không có hàm khởi tạo (constructor).
- Một interface không phải là một lớp. Viết một interface giống như viết một lớp, nhưng chúng có 2 định nghĩa khác nhau. Một lớp mô tả các thuộc tính và hành vi của một đối tượng. Một interface chứa các hành vi mà một class triển khai.
- Trừ khi một lớp triển khai interface là lớp trừu tượng abstract, còn lại tất cả các phương thức của interface cần được định nghĩa trong class.
### Cú pháp khai báo và sử dụng Interface

```java
interface <tên interface> {

        // Khai báo các thành phần bên trong interface

}
```

#### Ví dụ

Shape.java
```java
public interface Shape {
     
    String color = "red";
     
    void draw();
     
}
```

Rectangle.java
```java
public class Rectangle implements Shape {
 
    @Override
    public void draw() {
        System.out.println("Draw " + color + " rectangle");
    }
     
}
```

Circle.java
```java
public class Circle implements Shape {
 
    @Override
    public void draw() {
        System.out.println("Draw " + color + " circle");
    }
     
}
```

ShapeApp.java
```java
public class ShapeApp {
    public static void main(String[] args) {
        Shape rect = new Rectangle();
        rect.draw();
        System.out.println("---");
        Shape circle = new Circle();
        circle.draw();      
    }
}
```
#### Một số quy tắc khi triển khai interface:
Khi triển khai interface, có vài quy tắc sau:
- Một lớp có thể triển khai một hoặc nhiều interface tại một thời điểm.
- Một lớp chỉ có thể kế thừa một lớp khác, nhưng được triển khai nhiều interface.
- Một interface có thể kế thừa từ một interface khác, tương tự cách một lớp có thể kế thừa lớp khác.
## 2. Lớp trừu tượng

Một lớp được khai báo với từ khóa abstract là lớp trừu tượng (abstract class).

Lớp trừu tượng có thể có các phương thức abstract hoặc non-abtract.

Lớp trừu tượng có thể khai báo 0, 1 hoặc nhiều method trừu tượng bên trong.

Không thể khởi tạo 1 đối tượng trực tiếp từ một class trừu tượng.

Một lớp kế thừa từ lớp trừu tượng (subclass – lớp con) không cần phải implement non-abstract methods, nhưng những method nào có abstract thì bắt buộc phải override. Trừ khi subclass cũng là abstract.
#### Cú pháp

Để tạo lớp trừu tượng ta dùng từ khóa abstract trước từ khóa class.

> [PhamViTruyCap] abstract class [TenLop] {

}

### Phương thức trừu tượng trong Java
- Một phương thức được khai báo là abstract và không có trình triển khai thì đó là phương thức trừu tượng (abstract method).
- Nếu bạn muốn một lớp chứa một phương thức cụ thể nhưng bạn muốn triển khai thực sự phương thức đó để được quyết định bởi các lớp con, thì bạn có thể khai báo phương thức đó trong lớp cha ở dạng abstract.
- Từ khóa abstract được sử dụng để khai báo một phương thức dạng abstract. Phương thức abstract sẽ không có định nghĩa, được theo sau bởi dấu chấm phẩy, không có dấu ngoặc nhọn theo sau.

#### Cú pháp

> [PhamViTruyCap] abstract void [TenPhuongThuc] ();

### Ví dụ:

Shape.java
```java
public abstract class Shape {
    private String color = "red";

    public Shape() {

    }

    public abstract void draw();

    public String getColor() {
        return color;
    }
}
```
Rectangle.java
```java
public class Rectangle extends Shape {
 
    @Override
    public void draw() {
        System.out.println("Draw " + super.getColor() + " rectangle");
    }
     
}
```
Circle.java
```java
public class Circle extends Shape {
 
    @Override
    public void draw() {
        System.out.println("Draw " + super.getColor() + " circle");
    }
     
}
```
ShapeApp.java
```java
public class ShapeApp {
    public static void main(String[] args) {
        Shape rect = new Rectangle();
        rect.draw();
        System.out.println("---");
        Shape circle = new Circle();
        circle.draw();      
    }
}
```
Kết quả:
```java
Draw red rectangle
---
Draw red circle
```

### *Một số lưu ý:
- **Lớp con bắt buộc phải cài đặt (implement) tất cả các phương thức trừu tượng của lớp cha**

Bạn nhận được thông báo lỗi nếu lớp con không cài đặt (implement) tất cả các phương thức trừu tượng của lớp cha: The type Triangle must implement the inherited abstract method Shape.draw().

- **Không thể khởi tạo trực tiếp một lớp trừu tượng**

Bạn nhận được thông báo lỗi khi cố tình khởi tạo một lớp trừu tượng: Cannot instantiate the type Shape.
## 3. Tính trừu tượng trong lập trình hướng đối tượng

Tính trừu tượng trong lập trình hướng đối tượng là chỉ nêu ra vấn đề mà không hiển thị cụ thể, chỉ hiện thị tính năng thiết yếu đối với đối tượng người dùng mà không nói quy trình hoạt động. Ví dụ: như tạo ra tính năng gửi tin nhắn, ta chỉ cần hiểu là người dùng viết tin rồi nhấn gửi đi. Còn quy trình xử lý tin nhắn gửi như thế nào thì ta chưa đề cập đến.

Như vậy, tính trừu tượng là che giấu thông tin thực hiện từ người dùng, họ chỉ biết tính năng được cung cấp: Chỉ biết thông tin đối tượng thay vì cách nó sử dụng như thế nào. Nó có những ưu điểm sau:

+ Cho phép lập trình viên bỏ qua những phức tạp trong đối tượng mà chỉ đưa ra những khái niệm phương thức và thuộc tính cần thiết. Ta sẽ dựa những khái niệm đó để viết ra, nâng cấp và bảo trì.

+ Nó giúp ta tập trung cái cốt lõi đối tượng. Giúp người dùng không quên bản chất đối tượng đó làm gì.

## 4. Khi nào dùng abstract class, khi nào dùng Interface?
Sử dụng Abstract class khi chúng ta chỉ có thể hoàn thành một vài chức năng (method/ function) chuẩn của hệ thống, một vài chức năng còn lại các lớp extends phải hoàn thành. Những tính năng đã hoàn thành này vẫn sử dụng như bình thường, đây là những tính năng chung.

Sử dụng Interface khi bạn muốn tạo dựng một bộ khung chuẩn gồm các chức năng (method/ function) mà tất cả module/ project cần phải có. Các module phải implements tất cả chức năng đã được định nghĩa.

## 5. Sự khác nhau giữa Abstract class và Interface

|   Lớp trừu tượng (abstract class)  | Interface                                                                                                                |
|-----|--------------------------------------------------------------------------------------------------------------------------|
|   Thể hiện tính trừu tượng < 100%  | 	Thể hiện tính trừu tượng 100% (Java < 8).                                                                               |
|   Lớp trừu tượng có thể có các phương thức abstract và non-abstract  | Phiên bản Java < 8, Interface chỉ có thể có phương thức abstract. Phiên bản Java 8, có thể thêm default và static methods. Phiên bản Java 9, có thể thêm private methods. |
|  Lớp trừu tượng không hỗ trợ đa kế thừa   |       	Interface hỗ trợ đa kế thừa                                                                                                                   |
|   Lớp trừu tượng có thể có các biến final, non-final, static và non-static  |           	Interface chỉ có các biến static final                                                                                                               |
|   Lớp trừu tượng có thể có phương thức static, phương thức main và constructor  |           Interface không thể có phương thức static, main hoặc constructor.                                                                                                               |
|  Từ khóa abstract được sử dụng để khai báo lớp trừu tượng   |     Từ khóa interface được sử dụng để khai báo Interface                                                                                                                     |
|   Lớp trừu tượng có thể cung cấp trình triển khai của Interface  |           Interface không cung cấp trình triển khai cụ thể của lớp abstract                                                                                                               |

Nói về Abtract Class và Interface, đôi khi bạn sẽ gặp một số cách gọi: Khi một class extend một class/ abtract class thì có nghĩa là ta đang thể hiện mối quan hệ is-a (là), còn khi implement một interface, thì ta đang thể hiện mối quan hệ has-a (có, hay thực hiện).


