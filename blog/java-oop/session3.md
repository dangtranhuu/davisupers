<!-- ---
layout: Post
title: Giới thiệu về lập trình hướng đối tượng trong Java
subtitle: Lập trình hướng đối tượng với Java
author: Theanishtar
date: 2023-06-09
useHeaderImage: false
headerImage: /img/in-post/2020-10-07/header.jpg
headerMask: rgba(30, 69, 110, 0.61)
permalinkPattern: /ebook/java/java-oop/:slug/
tags:
  - Java OOP
---

Hướng đối tượng là phương pháp lập trình phổ biến nhất hiện nay!!! Cùng mình tìm hiểu về OOP trog bài viết này nhé  -->
<!-- more -->

# Bài 3. Tính kế thừa

Lập trình hướng đối tượng gồm 4 tính chất chính: [Tính đóng gói](), [Tính đa hình](), [Tính kế thừa](), [Tính trừu tượng]().

## 1. Kế thừa (`Inheritance`)

Trong `Java` các `attributes` và `methods` có thể kế thừa từ `class` khác.

Ở đây,chúng tôi gọi đó là `Inheritance`,  gồm 2 loại : 

- `subclass` (con) : *là `class` được kế thừa từ `class` khác*
- `superclass` (cha) : là `class` thừa kế

Ta sử dụng từ khoá `extends` để kế thừa từ một `class` : 

```java
class Animals(){
    protected String name = "mèo"; //thuộc tính
    public run(){ //phương thước
        System.out.println("Con vật đang chạy");
    }
}
class Dog extends Aminals{
    private String spec = "chó"; //thuộc tính
    public static void main(String[] args){
        Dog myDog = new Dog(); //tạo một object từ class Dog kế thừa từ Animals
        myDog.run(); //gọi phương thức run() từ class Dog kế thừa từ Animals
        System.out.println(myDog.name + " " + myDog.spec);
    }
}
/* Con vật đang chạy 
   mèo chó  */
```

> ⚠️ Hãy để ý ở lớp `Animals` tôi đã sử dụng `protected` để khai báo ==> Vì nếu 
> 
> - Đặt `private` thì lớp `Dog` sẽ không truy cập được
> - Đặt `public` thì không bảo đảm tính **an toàn** và **đóng gói**

#### Ôi, tôi không muốn kế thừa của ai hết, tôi cần làm sao ?

<details>
<summary><b><img src="https://raw.githubusercontent.com/Zenfection/Image/master/2021/02/01-13-25-05-Questions%20And%20Answers.png"> Trả lời
</b></summary>

<br>

Sử dụng từ khoá `final` quốc dân thôi !!!

```java
final class Animals{
    //...
}
class Dog extends Animals{ // Dòng này sẽ lỗi ngay lập tức
    //...
}
```

> 💡 Nếu bạn cố gắng kế thừa lớp `Animals` thì sẽ lỗi ngay !!!

</details>

---

## 2. Đa hình (`Polymorphism`)

`Polymorphism` có nghĩa là "many forms", nhiều `class` liên quan với nhau **kế thừa** nhau

> 💡 Như bạn đã biết thì `Interitance` sẽ cho phép `attributes` và `methods` kế thừa từ `class` khác. Thì **đa hình** có nghĩa là vẫn `methods` đó nhưng cách thức thực hiện khác nhau.
> 
> <details>
> <summary><b><img src="https://raw.githubusercontent.com/Zenfection/Image/master/2021/02/02-11-21-10-Assignment.png"> Ví dụ đơn giản</b></summary>
> 
> <br>
> 
> 🔥 Hiểu đơn giản, cũng là hàm `dientich()` để tính **diện tích**, nhưng nếu bạn nhập thông số của **hình vuông** nó sẽ ra **diện tích hình vuông**, nhập thông số **hình chữ nhật** thì sẽ ra **diện tích hình chữ nhật**
> 
> </details>

```java
class HinhHoc{
    public void dienTich(){
        System.out.println("Tính diện tích hình học");
    }
}
class HinhVuong extends HinhHoc{ // class hình vuông kế thừa từ class hình học
    public int dienTich(int canh){ 
        System.out.println("Diện tích hình vuông là " + (canh*canh));
    }
}
class HinhChuNhat extends HinhHoc{ // class hình chữ nhật kế thừa từ class hình học
    public void dienTich(int dai,int rong){
        System.out.println("Diện tích hình chữ nhật là " + (dai*rong));
    }
}
```

> 🔥 Như bạn đã thấy thì hàm `dienTich()` được lớp `HinhVuong` và lớp `HinhChuNhat` kế thừa từ lớp `HinhHoc` nhưng dĩ nhiên chức năng của nó khác nhau như sau : 

```java
class Main{
    public static void main(String[] args){
        HinhHoc hinhHoc = new HinhHoc();
        HinhVuong hinhVuong = new HinhVuong();
        HinhChuNhat hinhChuNhat = new HinhChuNhat();
        hinhHoc.dienTich();
        hinhVuong.dienTich(5);
        hinhChuNhat.dienTich(3,5);
    }
}
/* Tính diện tích hình học
   Diện tích hình vuông là 25
   Diện tích hình chữ nhật là 15
*/
```

> 🚀 Sử dụng tốt **đa hình** và **kế thừa** sẽ khiến code của bạn có tính tái sử dụng cao (*chỉ cần viết 1 lần dùng cho các vấn đề tương tự*)

---

## 3. Các Class lồng nhau (`Inner Classes`)

Trong `Java`, ta có thể viết các `class` này lồng `class` khác để làm cho code dễ bảo trì và dễ hiểu hơn.

#### Vậy làm thế nào để tạo một `class` lồng với `class` khác ?

<details>
<summary><b><img src="https://raw.githubusercontent.com/Zenfection/Image/master/2021/02/01-13-25-05-Questions%20And%20Answers.png"> Trả lời</b></summary>

<br>

Hãy tạo một `Object` của `class` ngoài, sau đó tạo một `Object` của `class` trong, như sau : 

```java
class lopNgoai{
    int x = 10;
    class lopTrong{
        int y = 5;
    }
}
public class Main{
    public static void main(String[] args){
        lopNgoai myOuter = new lopNgoai();
        lopNgoai.lopTrong myInner = myOuter.new lopTrong();
        System.out.println(myInner.y + myOuter.x);
    }
}
// output : 15 (5 + 10)
```

> 💡 Như bạn đã thấy thì thì lớp `lopTrong` nằm trong lớp `lopNgoai`, vì thế chúng ta cũng có cách khai báo như trên.

</details>

<br>

#### Các `class` trong có thể truy cập lên `class` ngoài được không ?

<details>
<summary><b><img src="https://raw.githubusercontent.com/Zenfection/Image/master/2021/02/01-13-25-05-Questions%20And%20Answers.png"> Trả lời</b></summary>

<br>

Dĩ nhiên là được, vì đó là lợi thế của việc sử dụng `Inner Classes`, như sau : 

```java
class lopNgoai{
    int x = 10;
    class lopTrong{
        public int myInnerMethod(){
            return x;
        }
    }
}

public class Main{
    public static void main(String[] args){
        lopNgoai myOuter = new lopNgoai();
        lopNgoai.lopTrong myInner = myOuter.new lopTrong();
        System.out.println(myInner.myInnerMethod());
    }
}
// output : 10
```

</details>

<br>

> 💡 Bạn cũng có thể khai báo `class` bên trong là `static` để có thể sử dụng mà không cần tạo `Object`

<details>
<summary><b><img src="https://raw.githubusercontent.com/Zenfection/Image/master/2021/02/02-11-21-10-Assignment.png"> Cụ thể như sau:</b></summary>

```java
class lopNgoai{
    int x = 10;
    static class lopTrong{
        int y = 5;
    }
}

public class Main{
    public static void main(String[] args){
        lopNgoai.lopTrong myInner = new lopNgoai.lopTrong();
        System.out.println(myInner.y);
    }
}
// output : 5
```

</details>

> ⚠️  Sử dụng `static` sẽ làm cho `class` trong không thể truy cập `class` ngoài ==> `myInner.x` là sai và lỗi.
