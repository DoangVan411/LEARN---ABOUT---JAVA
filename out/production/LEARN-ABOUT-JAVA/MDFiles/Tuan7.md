# [BUỔI 7] - INTERFACE VÀ TRỪU TƯỢNG 

## Interface
Interface là một kiểu dữ liệu tham chiếu trong Java. Nó là tập hợp các phương thức abstract (trừu tượng). Khi một lớp kế thừa interface, thì nó sẽ kế thừa những phương thức abstract của interface đó.

### Một số đặc điểm của interface:

- Không thể khởi tạo, nên không có phương thức khởi tạo.

- Tất cả các phương thức trong interface luôn ở dạng public abstract mà không cần khai báo.

- Các thuộc tính trong interface luôn ở dạng public static final mà không cần khai báo, yêu cầu phải có giá trị.

### Cú pháp khai báo và sử dụng Interface

```java
interface <tên interface> {

        // Khai báo các thành phần bên trong interface

}
```

## Lớp trừu tượng

Lớp trừu tượng là lớp được khai báo mà không thể tạo ra đối tượng từ lớp đó. Ta sẽ tạo những lớp con kế thừa lớp trừu tượng.

Mục đích lớp trừu tượng là tạo ra lớp chung cho những lớp có liên quan với nhau kế thừa.

>Khi phát triển chương trình, ta chỉ có thể tạo các đối tượng từ lớp con kế thừa lớp trừu tượng; không thể cho tạo đối tượng từ lớp trừu tượng được.

### Cú pháp

Để tạo lớp trừu tượng ta dùng từ khóa abstract trước từ khóa class.

```java
public abstract class Person {
	
	public String name;
	private int age;
	public float height;
	
	public Person(String name, int age, float height) {
		this.name = name;
		this.age = age;
		this.height = height;
	}
	
	public void setAge(int age) {
		if (age>=0 && age<=100 ) {
			this.age = age;
		}
	}
	
	public void setAge(byte age) {
		if (age>=0 && age<=100 ) {
			this.age = age;
		}
	}
	
	public void setAge(short age) {
		if (age>=0 && age<=100 ) {
			this.age = age;
		}
	}
	
	public void setAge(long age) {
		if (age>=0 && age<=100 ) {
			this.age = (int) age;
		}
	}
	
	public int getAge() {
		return this.age;
	}
	
	
	public void getInfo() {
		System.out.println("Name:"+this.name);
		System.out.println("Age:"+this.age);
		System.out.println("Height:"+this.height);
	}
	
}

```

## Tính trừu tượng trong lập trình hướng đối tượng

Tính trừu tượng trong lập trình hướng đối tượng là chỉ nêu ra vấn đề mà không hiển thị cụ thể, chỉ hiện thị tính năng thiết yếu đối với đối tượng người dùng mà không nói quy trình hoạt động. Ví dụ: như tạo ra tính năng gửi tin nhắn, ta chỉ cần hiểu là người dùng viết tin rồi nhấn gửi đi. Còn quy trình xử lý tin nhắn gửi như thế nào thì ta chưa đề cập đến.

Như vậy, tính trừu tượng là che giấu thông tin thực hiện từ người dùng, họ chỉ biết tính năng được cung cấp: Chỉ biết thông tin đối tượng thay vì cách nó sử dụng như thế nào. Nó có những ưu điểm sau:

+ Cho phép lập trình viên bỏ qua những phức tạp trong đối tượng mà chỉ đưa ra những khái niệm phương thức và thuộc tính cần thiết. Ta sẽ dựa những khái niệm đó để viết ra, nâng cấp và bảo trì.

+ Nó giúp ta tập trung cái cốt lõi đối tượng. Giúp người dùng không quên bản chất đối tượng đó làm gì.

