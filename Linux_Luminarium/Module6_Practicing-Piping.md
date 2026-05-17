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

  * <img width="1015" height="752" alt="image" src="https://github.com/user-attachments/assets/9c4ec817-cdd8-491e-acd6-dbed8ac2050a" />

</details>


<details>
 <summary>🏴 <code>Redirecting errors</code></summary>

 * Cũng giống như đầu ra tiêu chuẩn (standard output), bạn cũng có thể điều hướng kênh lỗi (error channel) của các câu lệnh. Tại đây, chúng ta sẽ tìm hiểu về các con số File Descriptor (FD).

 * Một __File Descriptor (FD)__ là một con số mô tả một kênh giao tiếp trong Linux. Bạn thực chất đã và đang sử dụng chúng, mặc dù bạn không nhận ra điều đó. Chúng ta đã quen thuộc với ba loại:

  * FD 0: Standard Input (Đầu vào tiêu chuẩn)

  * FD 1: Standard Output (Đầu ra tiêu chuẩn)

  * FD 2: Standard Error (Lỗi tiêu chuẩn)

 * Khi bạn điều hướng luồng giao tiếp của quy trình, bạn thực hiện thông qua số FD, mặc dù một số số FD là ngầm định. Ví dụ, một ký tự `>` mà không có số đi kèm sẽ ngầm định là `1>`, điều này giúp điều hướng FD 1 (Đầu ra tiêu chuẩn). Do đó, hai câu lệnh sau đây là tương đương nhau:

   ```Bash
   hacker@dojo:~$ echo hi > asdf
   hacker@dojo:~$ echo hi 1> asdf
   ```
   
 * Việc điều hướng các thông báo lỗi khá dễ dàng từ thời điểm này. Nếu bạn có một câu lệnh có thể tạo ra dữ liệu thông qua kênh lỗi tiêu chuẩn (chẳng hạn như `/challenge/run`), bạn có thể làm như sau:

   ```Bash
   hacker@dojo:~$ /challenge/run 2> errors.log
   ```

 * Thao tác đó sẽ điều hướng lỗi tiêu chuẩn (FD 2) vào tệp `errors.log`. Hơn nữa, bạn có thể điều hướng nhiều file descriptor cùng một lúc! Ví dụ:

   ```Bash
   hacker@dojo:~$ some_command > output.log 2> errors.log
   ```
   
 * Câu lệnh đó sẽ điều hướng đầu ra vào tệp `output.log` và các lỗi vào tệp `errors.log`.

 * Hãy đưa điều này vào thực hành! Trong thử thách này, bạn sẽ cần điều hướng đầu ra của lệnh `/challenge/run` vào tệp `myflag` (giống như trước đây), và các "lỗi" (trong trường hợp của chúng ta là các hướng dẫn) vào tệp `instructions`.

 * Bạn sẽ nhận thấy rằng sẽ không có gì được in ra màn hình terminal cả, bởi vì bạn đã điều hướng mọi thứ! Bạn có thể tìm thấy các hướng dẫn/phản hồi trong tệp `instructions` và cờ (flag) trong tệp `myflag` khi bạn thực hiện việc này thành công!

 * <img width="872" height="529" alt="image" src="https://github.com/user-attachments/assets/ad3e60e6-b5eb-4752-9f8f-cf8e645f6088" />

</details>


<details>
 <summary>🏴 <code>Redirecting input</code></summary>

 * Giống như việc bạn có thể điều hướng đầu ra (output) từ các chương trình, bạn cũng có thể điều hướng đầu vào (input) vào các chương trình! Việc này được thực hiện bằng cách sử dụng ký tự `<`, ví dụ như sau:

   ```Bash
   hacker@dojo:~$ echo yo > message
   hacker@dojo:~$ cat message
   yo
   hacker@dojo:~$ rev < message
   oy
   ```
   
 * Bạn có thể làm nhiều điều thú vị với rất nhiều chương trình khác nhau bằng cách sử dụng điều hướng đầu vào!

 * Trong cấp độ này, chúng ta sẽ thực hành sử dụng lệnh `/challenge/run`. Lệnh này sẽ yêu cầu bạn điều hướng tệp `PWN` vào nó, đồng thời tệp `PWN` đó phải chứa giá trị `COLLEGE`. Để ghi giá trị đó vào tệp `PWN`, hãy nhớ lại thử thách trước đó về việc điều hướng đầu ra từ lệnh `echo`!

 * <img width="716" height="148" alt="image" src="https://github.com/user-attachments/assets/c9122899-079d-4251-8153-6625b3a59f41" />

</details>


<details>
 <summary>🏴 <code>Grepping stored results</code></summary>
 
 * Bạn đã biết cách chạy các câu lệnh, cách điều hướng đầu ra của chúng (ví dụ: `>`), và cách tìm kiếm xuyên suốt tệp kết quả (ví dụ: `grep`). Hãy cùng kết hợp những kỹ năng này lại với nhau!
 
 * Để chuẩn bị cho các cấp độ phức tạp hơn, chúng tôi muốn bạn:

   1. Điều hướng đầu ra của `/challenge/run` vào tệp `/tmp/data.txt`.

   2. Việc này sẽ tạo ra một trăm nghìn dòng văn bản trong `/tmp/data.txt`, và một trong số đó chính là flag (cờ).

   3. Sử dụng `grep` trên tệp đó để tìm flag!
  
 * <img width="578" height="164" alt="image" src="https://github.com/user-attachments/assets/2b79aef8-c767-4c17-acd4-907c480a7c3e" />

</details>


<details>
 <summary>🏴 <code>Grepping live output</code></summary>

 * Hóa ra bạn có thể "loại bỏ bên trung gian" và tránh được việc phải lưu trữ kết quả vào một tệp như bạn đã làm ở cấp độ trước. Bạn có thể thực hiện việc này bằng cách sử dụng toán tử `|` (pipe - dấu đường ống).

 * Đầu ra tiêu chuẩn (standard output) từ câu lệnh bên trái của dấu đường ống sẽ được kết nối với (được dẫn vào) đầu vào tiêu chuẩn (standard input) của câu lệnh ở bên phải của dấu đường ống. Ví dụ:

   ```Bash
   hacker@dojo:~$ echo no-no | grep yes
   hacker@dojo:~$ echo yes-yes | grep yes
   yes-yes
   hacker@dojo:~$ echo yes-yes | grep no
   hacker@dojo:~$ echo no-no | grep no
   no-no
   ```

* Bây giờ hãy tự mình thử nghiệm! Lệnh `/challenge/run` sẽ xuất ra một trăm nghìn dòng văn bản, bao gồm cả flag. Hãy dùng `grep` để tìm flag đó!

* <img width="1013" height="519" alt="image" src="https://github.com/user-attachments/assets/290c1c81-7322-49f0-a0bd-456dc868fcc3" />

</details>


<details>
 <summary>🏴 <code>Grepping errors</code></summary>

 * Bạn đã biết cách điều hướng lỗi vào một tệp, và bạn cũng đã biết cách dẫn (pipe) đầu ra vào một chương trình khác, chẳng hạn như `grep`. Nhưng chuyện gì sẽ xảy ra nếu bạn muốn dùng `grep` để lọc trực tiếp qua các thông báo lỗi?

 * Toán tử `>` điều hướng một file descriptor (FD) nhất định vào một tệp, và bạn đã sử dụng `2>` để điều hướng FD 2, tức là đầu ra lỗi tiêu chuẩn (standard error). Toán tử `|` chỉ điều hướng đầu ra tiêu chuẩn (standard output) sang một chương trình khác, và không tồn tại dạng toán tử `2|`! Nó chỉ có thể điều hướng đầu ra tiêu chuẩn (file descriptor 1).

 * May mắn thay, ở đâu có shell (vỏ bọc dòng lệnh), ở đó có cách!

 * Shell có toán tử `>&`, toán tử này điều hướng một file descriptor sang một file descriptor khác. Điều này có nghĩa là chúng ta có thể thực hiện một quy trình hai bước để dùng `grep` lọc qua các lỗi: đầu tiên, chúng ta điều hướng lỗi tiêu chuẩn sang đầu ra tiêu chuẩn (`2>&1`), và sau đó dẫn (pipe) luồng kết hợp giữa stderr và stdout như bình thường (`|`)!

 * Hãy thử ngay bây giờ! Giống như cấp độ trước, cấp độ này sẽ làm bạn choáng ngợp với vô số đầu ra, nhưng lần này là trên kênh lỗi tiêu chuẩn. Hãy dùng `grep` xuyên qua đó để tìm flag!

 * <img width="993" height="513" alt="image" src="https://github.com/user-attachments/assets/070ab249-4c16-4f58-91d2-934b69e8ba22" />

</details>


<details>
 <summary>🏴 <code>Filtering with grep -v</code></summary>

 * Lệnh `grep` có một tùy chọn rất hữu ích: `-v` (khớp ngược - invert match). Trong khi lệnh `grep` thông thường hiển thị các dòng __KHỚP__ với một mẫu (pattern), thì `grep -v` sẽ hiển thị các dòng __KHÔNG KHỚP__ với mẫu đó:

   ```Bash
   hacker@dojo:~$ cat data.txt
   hello hackers!
   hello world!
   hacker@dojo:~$ cat data.txt | grep -v world
   hello hackers!
   hacker@dojo:~$
   ```
   
 * Đôi khi, cách duy nhất để lọc ra đúng dữ liệu bạn muốn là lọc **BỎ** những dữ liệu bạn __KHÔNG__ muốn. Trong thử thách này, `/challenge/run` sẽ xuất flag ra đầu ra tiêu chuẩn (stdout), nhưng nó cũng sẽ xuất ra hơn 1000 flag giả (có chứa từ `DECOY` đâu đó trong nội dung flag) trộn lẫn với flag thật. Bạn sẽ cần phải lọc __BỎ__ các flag giả trong khi vẫn giữ lại flag thật!

 * Hãy sử dụng `grep -v` để lọc bỏ tất cả các dòng chứa từ "DECOY" và tìm ra flag thật!

 * <img width="589" height="100" alt="image" src="https://github.com/user-attachments/assets/754493e5-f966-4640-81db-a94a575ef7c4" />

</details>

<details>
 <summary>🏴 <code>Filtering with sed</code></summary>

 * `grep` không phải là cách duy nhất để khớp các mẫu (patterns). Đôi khi dữ liệu thật và dữ liệu rác bị trộn lẫn trên cùng một dòng, và chúng ta muốn lọc bỏ phần rác đó đi. Để làm điều đó, chúng ta có `sed`.

 * `sed` cung cấp một cách dễ dàng để thay thế các mẫu trong văn bản bằng một từ khác. Cú pháp để khớp và thay thế rất đơn giản:

* `sed "s/oldword/newword/g"`

  * `s/`: substitute (thay thế).

  * `oldword`: từ cần được thay thế.

  * `newword`: từ dùng để thay thế cho `oldword`.

  * `/g`: global (toàn cục - tìm kiếm và thay thế tất cả các lần xuất hiện của mẫu đó).

 * Trong thử thách này, `/challenge/run` sẽ in ra flag, nhưng giữa mỗi ký tự sẽ có chuỗi "FAKEFLAG". Nhiệm vụ của bạn là lọc bỏ dữ liệu rác khỏi flag. Chúc may mắn!

 * <img width="874" height="114" alt="image" src="https://github.com/user-attachments/assets/0b987929-5753-4d51-9973-adde9c48f5c9" />

</details>


<details>
 <summary>🏴 <code>Duplicating piped data with tee</code></summary>

 * Khi bạn dẫn dữ liệu (pipe) từ câu lệnh này sang câu lệnh khác, tất nhiên bạn sẽ không còn nhìn thấy dữ liệu đó trên màn hình của mình nữa. Điều này không phải lúc nào cũng là mong muốn: ví dụ, bạn có thể muốn xem dữ liệu khi nó đang luân chuyển giữa các câu lệnh để gỡ lỗi (debug) cho những kết quả ngoài ý muốn (ví dụ: "tại sao câu lệnh thứ hai đó lại không hoạt động nhỉ???").

 * May mắn thay, đã có một giải pháp! Lệnh `tee`, được đặt tên theo "mối nối chữ T" (T-splitter) trong hệ thống ống nước, sẽ nhân bản dữ liệu đang chảy qua các đường ống của bạn vào bất kỳ số lượng tệp nào được cung cấp trên dòng lệnh. Ví dụ:

   ```Bash
   hacker@dojo:~$ echo hi | tee pwn college
   hi
   hacker@dojo:~$ cat pwn
   hi
   hacker@dojo:~$ cat college
   hi
   hacker@dojo:~$
   ```

 * Như bạn có thể thấy, bằng cách cung cấp hai tệp cho `tee`, chúng ta đã có được ba bản sao của dữ liệu được dẫn vào: một bản đến đầu ra tiêu chuẩn (stdout), một bản đến tệp `pwn`, và một bản đến tệp `college`. Bạn có thể hình dung cách mình sử dụng điều này để gỡ lỗi khi mọi thứ trở nên hỗn loạn:

   ```Bash
   hacker@dojo:~$ command_1 | command_2
   Câu lệnh 2 đã thất bại!
   hacker@dojo:~$ command_1 | tee cmd1_output | command_2
   Câu lệnh 2 đã thất bại!
   hacker@dojo:~$ cat cmd1_output
   Câu lệnh 1 đã thất bại: phải truyền thêm tham số --succeed!
   hacker@dojo:~$ command_1 --succeed | command_2
   Các câu lệnh đã thành công!
   ```

  * Bây giờ, hãy tự mình thử nghiệm! Trong tiến trình này, `/challenge/pwn` phải được dẫn (pipe) vào `/challenge/college`, nhưng bạn sẽ cần phải chặn dữ liệu lại để xem `pwn` đang yêu cầu gì ở bạn!

  * <img width="1006" height="340" alt="image" src="https://github.com/user-attachments/assets/515cfd44-f67f-4920-a792-a240adf2fce7" />

</details>

