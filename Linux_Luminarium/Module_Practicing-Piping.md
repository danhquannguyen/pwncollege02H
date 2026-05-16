# Practicing Piping

* Bạn có thể đã nhận thấy rằng một số lệnh xuất dữ liệu ra terminal của bạn khi bạn chạy chúng. Cho đến nay, điều này đã in ra cho bạn rất nhiều cờ (flags), nhưng giống như nhiều thứ khác, công nghệ này còn đi sâu hơn thế rất nhiều. Các cơ chế đằng sau việc xử lý đầu vào (input) và đầu ra (output) trên dòng lệnh (command line) đóng góp vào sức mạnh của dòng lệnh.

* Module này sẽ dạy cho bạn về việc __chuyển hướng đầu vào và đầu ra__ (input and output redirection). Nói một cách đơn giản, mọi tiến trình (process) trong Linux đều có ba kênh giao tiếp tiêu chuẩn, ban đầu:

  * **Đầu vào Tiêu chuẩn** (Standard Input) là kênh mà thông qua đó tiến trình nhận đầu vào. Ví dụ, shell của bạn sử dụng Đầu vào Tiêu chuẩn để đọc các lệnh mà bạn nhập vào.

  * **Đầu ra Tiêu chuẩn** (Standard Output) là kênh mà thông qua đó các tiến trình xuất ra dữ liệu bình thường, chẳng hạn như cờ (flag) khi nó được in ra cho bạn trong các thử thách trước hoặc đầu ra của các tiện ích như ls.

  * **Lỗi Tiêu chuẩn** (Standard Error) là kênh mà thông qua đó các tiến trình xuất ra các chi tiết lỗi. Ví dụ, nếu bạn gõ sai một lệnh, shell sẽ xuất ra, thông qua Lỗi tiêu chuẩn, thông báo rằng lệnh này không tồn tại.

* Bởi vì ba kênh này được sử dụng rất thường xuyên trong Linux, chúng được biết đến bằng những cái tên ngắn gọn hơn: `stdin`, `stdout`, `stderr`. Module này sẽ dạy cho bạn cách chuyển hướng (redirect), xâu chuỗi (chain), chặn (block), và các cách khác để can thiệp (mess with) vào các kênh này. Chúc may mắn!

<details>
  <summary>🏴 <code>Redirecting output</code></summary>  

  * Đầu tiên, hãy cùng xem xét việc chuyển hướng `stdout` (đầu ra tiêu chuẩn) vào các tệp. Bạn có thể thực hiện điều này bằng ký tự `>`, giống như thế này:

    ```sh
    hacker@dojo:~$ echo hi > asdf
    ```
  
  * Lệnh này sẽ chuyển hướng đầu ra của lệnh `echo hi` (kết quả sẽ là `hi`) vào tệp `asdf`. Sau đó, bạn có thể sử dụng một chương trình chẳng hạn như `cat` để xuất ra nội dung của tệp này:

    ```sh
    hacker@dojo:~$ cat asdf
    hi
    ```

  * Trong thử thách này, bạn phải sử dụng tính năng chuyển hướng đầu ra này để ghi từ `PWN` (tất cả đều viết hoa) vào tệp có tên là `COLLEGE` (tất cả đều viết hoa).

  * <img width="681" height="132" alt="image" src="https://github.com/user-attachments/assets/2678044e-d824-4040-8b82-143210bf44f6" />

</details>

<details>
  <summary>🏴 <code>Redirecting more input</code></summary>

  * Ngoài việc chuyển hướng đầu ra của lệnh `echo`, tất nhiên, bạn cũng có thể chuyển hướng đầu ra của bất kỳ lệnh nào. Trong cấp độ này, chương trình `/challenge/run` sẽ một lần nữa cấp cho bạn một cờ (flag), nhưng chỉ khi bạn chuyển hướng đầu ra của nó vào tệp `myflag`. Tất nhiên, cờ của bạn cuối cùng sẽ nằm gọn trong tệp `myflag`!

  * Bạn sẽ nhận thấy rằng `/challenge/run` vẫn sẽ vui vẻ in ra terminal của bạn, mặc dù bạn đã chuyển hướng `stdout` (đầu ra tiêu chuẩn). Đó là bởi vì nó truyền đạt các hướng dẫn và phản hồi của mình thông qua __standard error__ (lỗi tiêu chuẩn), và chỉ in ra cờ thông qua __standard out__ (đầu ra tiêu chuẩn)!

  * <img width="789" height="412" alt="image" src="https://github.com/user-attachments/assets/704dbd37-4ecf-470f-8573-c6330d3e387f" />

</details>

<details>
  <summary>🏴 <code>Appending output</code></summary>

  * Một trường hợp sử dụng phổ biến của việc chuyển hướng đầu ra là lưu lại một số kết quả của lệnh để phân tích sau. Thường thì, bạn muốn thực hiện điều này một cách tổng hợp (in aggregate): chạy một loạt các lệnh, lưu đầu ra của chúng, và `grep` (lọc/tìm kiếm) qua chúng sau này. Trong trường hợp này, bạn có thể muốn tất cả đầu ra đó tiếp tục được nối thêm (appending) vào cùng một tệp, nhưng `>` sẽ tạo ra một tệp đầu ra mới mỗi lần, xóa đi các nội dung cũ.

  * Bạn có thể chuyển hướng đầu vào (lưu ý của người dịch: bản gốc viết là "redirect input" nhưng đây có thể là lỗi đánh máy của tác giả, ngữ cảnh ở đây chính xác phải là chuyển hướng đầu ra - "redirect output") ở chế độ nối thêm (append mode) bằng cách sử dụng `>>` thay vì `>`, giống như thế này:

    ```sh
    hacker@dojo:~$ echo pwn > outfile
    hacker@dojo:~$ echo college >> outfile
    hacker@dojo:~$ cat outfile
    pwn
    college
    hacker@dojo:$
    ```
    
  * Để thực hành, hãy chạy `/challenge/run` với việc chuyển hướng đầu ra ở chế độ nối thêm vào tệp `/home/hacker/the-flag`. Bài thực hành này sẽ ghi nửa đầu của cờ (flag) vào tệp, và nửa sau vào `stdout` (đầu ra tiêu chuẩn) nếu `stdout` được chuyển hướng vào tệp. Nếu bạn chuyển hướng đúng cách ở chế độ nối thêm, nửa sau sẽ được nối vào nửa đầu, nhưng nếu bạn chuyển hướng ở chế độ cắt cụt (truncation mode, tức là dùng `>`), nửa sau sẽ ghi đè (overwrite) lên nửa đầu và bạn sẽ không nhận được cờ!

  * Hãy thử ngay đi nào!

  * 
</details>
