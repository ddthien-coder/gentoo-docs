---
title: Biến trong java
---
Trong java, biến là vùng nhớ, có 3 loại biến
```
1. Biến local
2. Biến instance(biến toàn cục)
3. Biến static
```

## Khai báo biến trong java

```Cú Pháp
DataType varName [= value]
--> DataType kiểu dữ liệu biến,varName tên biến
```

```Quy tắc đặt tên biến
 * Chỉ được bắt đầu bằng một ký tự(chữ), hoặc dấu gạch dưới(_), hoặc ký tự dollar($)
  ** Tên biến không được chứa khoảng trắng
  *** Bắt đầu bằng ký tự thứ 2, có thể dùng chữ hoặc (_) hoặc ($)
  **** Có phân biệt chữ hoa, chữ thường
```

### Ví dụ

```
public class Bien {
    public static float PI = 3.14f;   // Đây là biến static
    int n;                            // Đây là biến instance

    public Bien () {
        char c = 'c';                 // Đây là biến local
    }
}
```

### Biến local trong java

```
 * Biến local được khai báo trong các phương thức, hàm contructor hoặc block
 ** Biến local được tạo bên trong các phương thức, hàm contructor, block và sẽ huỷ khi kết thúc
 *** Không được sử dụng "access modifier"(private, protected, public) khi khai báo biến local
 **** Các biến local được lưu trên vùng nhớ của bộ nhớ
 ***** Cần khởi tạo giá trị mặc định cho biến local trước khi có có thể sử dụng
```
```ví dụ
public class Bien {

    public void sayHello() {
        int n = 10;                     // Đây là biến local
        System.out.println("Gia tri cua n la: " + n);
    }

    public static void main(String[] args) {
        Bien bienLocal = new Bien();
        bienLocal.sayHello();
    }
}
```

``` Nếu không khởi tạo biến local
public class Bien {

    public void sayHello() {
        int n;                 // Đây là biến local
        System.out.println("Gia tri cua n la: " + n);
    }

    public static void main(String[] args) {
        Bien bienLocal = new Bien();
        bienLocal.sayHello();
    }
}
KQ: Exception in thread "main" java.lang.Error: Unresolved compilation problem:
    The local variable n may not have been initialized
    Lỗi biên dịch
```



### Biến biến instance (biến toàn cục) trong java

```
1. Biến instance được khai báo trong một lớp class, bên ngoài các phương thức, constructor và block
2. Được lưu trong bộ nhớ heap
3. Biến instance được tạo khi một đối tượng được tạo và sử dụng từ khoá "new"
và sẽ bị huỷ khi đối tượng bị huỷ
4. Biến instance có thể được sử dụng bởi các phương thức, constructor, block, ... Nhưng nó phải được sử dụng thông qua một đối tượng cụ thể.
5. Được  sử dụng "access modifier" khi khai báo biến instance
6. Biến instance có giá trị mặc định phụ thuộc vào kiểu dữ liệu của nó. Ví dụ nếu là kiểu int, short, byte thì giá trị mặc định là 0, kiểu double thì là 0.0d, ... Vì vậy, sẽ không cần khởi tạo giá trị cho biến instance trước khi sử dụng.
7. Bên trong class mà  khai báo biến instance,  có thể gọi nó trực tiếp bằng tên khi sử dụng ở khắp nới bên trong class đó.
```
```ví dụ
public class Sinhvien {
    // biến instance "ten" kiểu String, có giá trị mặc định là null
    public String ten;

    // biến instance "tuoi" kiểu Integer, có giá trị mặc định là 0
    private int tuoi;

    // sử dụng biến ten trong một constructor
    public Sinhvien(String ten) {
        this.ten = ten;
    }

    // sử dụng biến tuoi trong phương thức setTuoi
    public void setTuoi(int tuoi) {
        this.tuoi = tuoi;
    }

    public void showStudent() {
        System.out.println("Ten  : " + ten);
        System.out.println("Tuoi : " + tuoi);
    }

    public static void main(String args[]) {
        Sinhvien sv = new Sinhvien("Nguyen Van A");
        sv.setTuoi(21);
        sv.showStudent();
    }
}
```

### Biến static trong java

```
1. Biến static được khai báo trong một class với từ khóa "static", phía bên ngoài các phương thức, constructor và block.
2. Sẽ chỉ có duy nhất một bản sao của các biến static được tạo ra, dù  tạo bao nhiêu đối tượng từ lớp tương ứng.
Biến static được lưu trữ trong bộ nhớ static riêng.
3. Biến static được tạo khi chương trình bắt đầu chạy và chỉ bị hủy khi chương trình dừng.
4. Giá trị mặc định của biến static phụ thuộc vào kiểu dữ liệu bạn khai báo tương tự biến instance.
5. Biến static được truy cập thông qua tên của class chứa nó, với cú pháp: TenClass.tenBien.
6. Trong class, các phương thức sử dụng biến static bằng cách gọi tên của nó khi phương thức đó cũng được khai báo với từ khóa "static".

```
``` ví dụ
public class Sinhvien {
    // biến static 'ten'
    public static String ten = "Nguyen Van A";

    // biến static 'tuoi'
    public static int tuoi = 21;

    public static void main(String args[]) {
        // Sử dụng biến static bằng cách gọi trực tiếp
        System.out.println("Ten : " + ten);

        // Sử dụng biến static bằng cách gọi thông qua tên class
        System.out.println("Ten : " + Sinhvien.tuoi);
    }
}
```
