# Hello Hacker

<details>
  <summary>🎥 <code>The Command Line</code></summary>
  
  * Hello Students
  Các bạn có thể đã từng nhìn tháy:
     ```sh
     # echo Hello Hacker!
     Hello Hacker!
     ```
  Nhưng điều gì thực sự xảy ra đằng sau?

  * **Command line ?** (Dòng lệnh)

  Dòng lệnh(còn được gọi là "shell") là một giao diện mạnh mẽ với một máy tính. Ý tưởng cơ bản:
  1. Bạn gõ một lệnh.
  2. Hệ thống thực thi nó và xuất ra các kết quả.

  Thông thường, một lệnh sẽ chứa một chương tình và các tham số cho chương trình đó, được phân tách bằng khoảng trắng.
     
  ```sh
  yans@asdf ~ cat flag
  pwn_college{1337}
  yans@asdf ~ $ █
  ```

  Điều gì đã xảy ra?
  1. Tôi đã bảo shell chạy chương trình `cat` với đối số `flag`.
  2. Shell đã tìm thấy tệp chương trình `cat` và khởi chạy nó thành một tiến trình `cat` với một đối số `flag`.
  3. `cat` là một chương trình xuất ra các tệp. Nó đọc đối số `flag` và biết phải xuất ra tệp `flag`, tệp này chứa "pwn-college{1337}".
  4. 

  * **Command Parameters / Arguments** (Các tham số lệnh/ các đối số)

  Các tham số lệnh cũng được gọi là các "đối số". Một vài ví dụ

  Lệnh `echo` nhận nhiều đối số và chỉ đơn giản là in chúng ngược lại ra _terminal!_
     
  ```sh
  yans@asdf:~$ echo Hello Hackers!
  Hello Hackers!
  yans@asdf:~$
  ```

  Một đối số làm thay đổi chức năng của các lệnh. Những đối số này(thường) được đặt trước bằng một ký tự `-`(dấu gạch ngang). Ví dụ, đối số `-n` cho lệnh `echo` khiến lệnh echo không bắt đầu một dòng mới trước khi kết thúc.
    
  ```sh
  yans@asdf:~$ echo -n Hello Hackers!
  Hello Hackers!yans@asdf:~$
  ```

  Các đối số dài hơn (thường) được đặt trước bằng `--` (hai dấu gạch ngang). Ví dụ, lệnh `date` hiển thị thời gian hiện tại, nhưng có các chế độ hoạt động khác (trong trường hợp này, chuyển đổi múi giờ sang UTC):
     
  ```sh
  yans@asdf:~$ date
  Sun Aug 25 09:53:32 PM MST 2024
  yans@asdf:~$ date --utc
  Mon Aug 26 04:53:34 AM UTC 2024
  yans@asdf:~$
  ```
  
</details>
