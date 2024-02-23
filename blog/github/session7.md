

# Bài 7 Viết commits chuyên nghiệp


<img src="https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/list/1.png?raw=true" alt="Image 1" style="width:500px; height:50%;">

:::details <b>Nội dung chính</b>

<br>

<div class="scroll" style="width: 100%; overflow-x: auto; white-space: nowrap;">
  <div style="display: inline-block; margin-right: 15px;">
    <img src="https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/list/1.png?raw=true" alt="Image 1" style="width:500px; height:50%;object-fit: cover; margin:0px;">
  </div>
  <div style="display: inline-block; margin-right: 15px;">
    <img src="https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/list/2.png?raw=true" alt="Image 2" style="width:500px; height:50%;object-fit: cover; margin:0px;">
  </div>
  <div style="display: inline-block; margin-right: 15px;">
    <img src="https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/list/3.png?raw=true" alt="Image 3" style="width:500px; height:50%;object-fit: cover; margin:0px;">
  </div>
  <div style="display: inline-block; margin-right: 15px;">
    <img src="https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/list/4.png?raw=true" alt="Image 1" style="width:500px; height:50%;object-fit: cover; margin:0px;">
  </div>
  <div style="display: inline-block; margin-right: 15px;">
    <img src="https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/list/5.png?raw=true" alt="Image 1" style="width:500px; height:50%;object-fit: cover; margin:0px;">
  </div>
  <div style="display: inline-block; margin-right: 15px;">
    <img src="https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/list/6.png?raw=true" alt="Image 1" style="width:500px; height:50%;object-fit: cover; margin:0px;">
  </div>
  <div style="display: inline-block; margin-right: 15px;">
    <img src="https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/list/7.png?raw=true" alt="Image 1" style="width:500px; height:50%;object-fit: cover; margin:0px;">
  </div>
  <!-- Add more slides as needed -->
</div>
::: 


## Một câu chuyện tại công ty nọ

Một anh chàng kỹ sư code 2 tháng trời để cho ra một tính năng cự kì **vip pro**, và rồi anh ta commit nó lên GitHub những mãi 1 tuần vẫn chưa được Leader Merge code. 

Anh ta ngay lập tức đến gặp sếp mình thì được biết lí do là commit của anh như ***shit*** và được yêu cầu về viết lại commit khác !!!

Và rồi anh ta lên mạng tìm mọi cách để có thể cải thiện được việc đó, nhưng bạn có thấy rằng như vậy có muộn không ?

Chúng ta ở thế hệ đi sau, có rất nhiều người cạnh tranh với bạn... Nếu bạn còn không cải thiện bản thân thì sẽ đánh mất khá nhiều cơ hội đấy !!!

Hãy xem hình sau đây và xem nó có phản ánh đúng về bạn không nhé, nếu là bạn thì bài viết này là dành cho bạn đấy
![](https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/commits-bad.png?raw=true)

Khi đọc xong bài viết này, đây là kết quả mà bạn đạt được

![](https://github.com/dangtranhuu/images/blob/main/angurvad/github/sesstion7/commit-good.png?raw=true)


Hãy cùng cem bài viết sau đây để cải thiện commit của mình, giúp nó Clean và Pro hơn nhé !!!

## Cấu trúc một commit

Một Commit message sẽ gồm 3 phần

$$
<TYPE>:<DESCRIPTION>:[BODY]
$$

- Trong đó:
  - Type thể hiện lý do viết commits
  - Description là mô tả ngắn gọn về commits
  - Body và mô tả cụ thể về commits
  - Type, Description là bắt buộc, còn Body không có cũng được


<p align="center"> Ví dụ
<span style="color: red;">feat</span>: <span style="color: green;">add Facebook login feature</span>
</p>


## Type

Type là các kiểu commits phổ biến, bạn có thể tham khảo bảng sau đây:

| Tên            | Cách viết  | Mô tả                                                   |
|----------------|------------|---------------------------------------------------------|
| Fixes/bugs     | fix        | Sửa các lỗi được phát hiện trong mã nguồn.             |
| Features       | feat       | Thêm tính năng mới vào sản phẩm.                        |
| Refactoring    | refactor   | Cải thiện cấu trúc, sửa đổi mã nguồn mà không làm thay đổi tính năng bên ngoài của sản phẩm. |
| Documentation  | docs       | Cập nhật hoặc thêm mới tài liệu, hướng dẫn sử dụng cho mã nguồn. |
| Tests          | test       | Thêm, sửa đổi hoặc loại bỏ các bài kiểm tra, bài thử nghiệm cho mã nguồn. |
| Chore          | chore      | Cải thiện quy trình phát triển, cập nhật công cụ, thư viện hỗ trợ hoặc các thay đổi nhỏ không liên quan trực tiếp đến mã nguồn. |
| Build          | build       | Những thay đổi ảnh hưởng đến quá trình build          |
| CI             |   ci        | Thay đổi file cấu hình hoặc Sctipt CI          |
| Performance    | perf       | Cải thiện hiệu suất hoặc tối ưu hóa mã nguồn.          |
| Security       | security   | Cải thiện bảo mật của mã nguồn.                         |
| Style          | style      | Cải thiện định dạng, kiểu dáng, chuẩn mã nguồn.       |
| Reverts        | revert     | Quay lại một số thay đổi trước đó.                     |

- Type sẽ được viết bằng chữ in thường, trước dấu hai chấm


:::info Một số ví dụ:

- feat: .....
- fix: ....
- refactor: ...
:::


## Description

Là phần mô tả ngắn gọn về nội dung của commit

Không dài quá 50 ký tự, để tiện cho việc đọc trên GitHub hoặc các git tools

Sử dụng các câu mệnh lệnh ở thì hiênh tại
- Ví dụ: `change...` thay vì `changed...`

Không viết hoa chữ cái đầu tiên

Không sử dụng dấu chấm ở cuối câu



:::info Một số ví dụ:

- feat: add Facebook login feature.
- fix: resolve issue with incorrect password preventing login.
- refactor: optimize code for login processing.
- perf: improve main page loading speed.

--------------------
- feat: Thêm chức năng đăng nhập bằng Facebook.
- fix: Sửa lỗi không thể đăng nhập khi mật khẩu sai.
- refactor: Tối ưu hóa mã nguồn cho việc xử lý đăng nhập.
- perf: Cải thiện tốc độ tải trang chính.
:::

## Body

Là phần TÙY CHỌN, mô tả một cách chi tiết hơn nếu cần

Phần BODY cách `<type>: <description>` bởi một ký tự xuống dòng (blank line)

Nên dùng để giair thích câu hỏi **What (để làm gì?)** hoặc **Why (tại sao cần? )**, chứ không phải **How (làm thế nào?)**