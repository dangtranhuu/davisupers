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

# Bài 5. Tính trừu tượng

Lập trình hướng đối tượng gồm 4 tính chất chính: [Tính đóng gói](), [Tính đa hình](), [Tính kế thừa](), [Tính trừu tượng]().

## 1. Abstract

`Data Abstact` (*trừu tượng dữ liệu*) có nghĩa là ẩn một số chi tiết nhất định và hiển thị những thứ cần thiết cho người dùng.

> 💡 Hiểu đơn giản thì bạn gọi một món ăn thì bạn không cần phải biết quy trình nấu ăn, công thức nấu... chỉ cần ăn thôi. 

Từ khoá `abstract` là một `non-access modifier` bạn đã học trong bài [Phạm vi truy cập](https://github.com/Zenfection/Java/blob/master/Java%20OOP/2.Modifier.md) , sử dụng cho `classes` và `methods` : 

- `Abstract class` : đây là một `class` không được sử dụng để tạo `Object` (*nó chỉ dùng để kế thừa*).
- `Abstact method` : có thể sử dụng trong `Abstract class` và không có phần `body` (*phần `body` được cung cấp bởi `subclass` hoặc kế thừa từ nó*).

```java
abstract class Animal {
    public abstract void animalSound();
    public void sleep() {
        System.out.println("Zzz");
    }
}
```

> ⚠️ Không thể tạo `Object` từ một lớp `Abstract` như sau : 
> 
> ```java
> Animal myObj = new Animal(); // sẽ lỗi
> ```

### Để truy cập vào `abstract class`, thì ta phải làm sao ?

<details>
<summary><b><img src="https://raw.githubusercontent.com/Zenfection/Image/master/2021/02/01-13-25-05-Questions%20And%20Answers.png"> Trả lời</b></summary>

<br>

Nó phải được kế thừa từ `class` khác. Hãy đổi lớp `Animal` mà ta sử udng5 

```java
//khai báo lớp abstract
abstract class Animal{
    public abstract void animalSound();
    public void sleep(){
        System.out.println("Zzz");
    }
}
//khai báo subclass (kế thừa từ lớp Animal)
class Cat extends Animal{
    public void animalSound(){
        System.out.println("Con mèo kêu : mèo méo meo");
    }
}

class Main{
    public static void main(String[] args){
        Cat myCat = new Cat();
        myCat.animalSound();
        myCat.sleep();
    }
}
/* Con mèo kêu : mèo méo meo
   Zzz  */
```

> 💡 Như bạn đã thấy, `abstract class` chỉ cho phép kế thừa nó, và ta sử dụng thôi, dễ mà !!!

</details>

> 🚀 Ta sử dụng tính `Abstract` (*trừu tượng*) để : 
> 
> - Bảo đảm tính **bảo mật** (*ẩn các chi tiết quan trọng và chỉ hiển thị thứ cần thiết*) 

---


## 2. Interface

`Interfect` là một bản thiết kế cho `abstract class`, được sử dụng để nhóm các `methods` với phần `body` trống : 

```java
//interface
interface Animal{
    public void animalSound();//không có body => gọi là interface methods =
    public void run();//không có body => gọi là interface method
}
```

> 🔥 Để truy cập vào `Interface Methods` ta phải dùng từ khoá `implements` (*thay vì sử dụng `extends`*) như sau : 

```java
interface Animal{
    public void animalSound();
    public void run();
}

class Cat implements Animal{
    public void animalSound(){
        System.out.println("Con mèo kêu : mèo méo meo");
    }
}

class Main{
    public static void main(String[] args){
        Cat myCat = new Cat();
        myCat.animalSound();
        myCat.sleep();
    }
}
/* Con mèo kêu mèo méo meo
   Zzz, khò khò  */
```

> 🧨 Tính chất của `Interface` : 
> 
> - Các `Interface methods` không có phần `body`, được cung cấp bởi lớp `implement`
> - Về việc dùng `Interface`, bạn phải ghi đè lại tất cả `methods`
> - Mặc định thì `Interface methods` là `abstract` và `public`
> - Mặc định thì `Interface attributes` là `public`, `static`, `final`
> 
> ⚠️ Các lưu ý sau : 
> 
> - Giống như `abstract class`, `interface` không sử dụng để tạo `Object`
> - Một `Interface` không thể chứa `constructor`

### Tại sao ta phải sử dụng `Interface` ?

<details>
<summary><b><img src="https://raw.githubusercontent.com/Zenfection/Image/master/2021/02/01-13-25-05-Questions%20And%20Answers.png"> Trả lời</b></summary>

<br>

- Để được sử bảo mật an toàn.
- `Java` không hỗ trợ `multiple inheritance` (*đa kế thừa*) - tức là một `class` có thể kế thừa từ một `subclass` ==> Tuy nhiên ta có thể làm được điều đó bằng cách sử dụng `Interface`

> 💭 Đơn giản hơn là khi bạn vào nhà hàng, người ta sẽ đưa cho bạn cái menu chọn món, chứ không ai lại dẫn bạn vào nhà bếp coi món nào để chọn ==> `Interface` là cái menu đó.

</details>

<br>

### Ở trên nói có thể dùng `Interface` để đa kế thừa, vậy dùng sao ?

<details>
<summary><b><img src="https://raw.githubusercontent.com/Zenfection/Image/master/2021/02/01-13-25-05-Questions%20And%20Answers.png"> Trả lời</b></summary>

<br>

Ta sử dụng từ khoá `implement` đến nhiều `Interface` cách nhau bởi dấu `;` như sau : 

```java
interface firstInterface(){
    public void myMethod1();
}
interface secondInterface(){
    public void myMethod2();
}

class Demo implements firstInterface, secondInterface {
    public void myMethod1(){
        System.out.println("bla bla bla");
    }
    public void myMethod2(){
        System.out.println("ble ble ble");
    }
}

class Main{
    public static void main(String[] args) {
        DemoClass myObj = new DemoClass();
        myObj.myMethod();
        myObj.myOtherMethod();
    }
}
/* bla bla bla
   ble ble ble */
```

</details>