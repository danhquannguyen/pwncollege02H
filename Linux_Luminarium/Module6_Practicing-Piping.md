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


<details>
 <summary>🏴 <code>Procss substitution for input</code></summary>

 * Đôi khi bạn cần so sánh đầu ra (output) của hai lệnh thay vì so sánh hai tệp tin. Bạn có thể nghĩ đến việc lưu mỗi đầu ra vào một tệp trước:

   ```bash
   hacker@dojo:~$ command1 > file1
   hacker@dojo:~$ command2 > file2
   hacker@dojo:~$ diff file1 file2
   ```

 * Nhưng có một cách thanh lịch hơn! Linux tuân theo triết lý rằng "mọi thứ đều là tệp". Nghĩa là, hệ thống cố gắng cung cấp khả năng truy cập giống như tệp đối với hầu hết các tài nguyên, bao gồm cả đầu vào (input) và đầu ra của các chương trình đang chạy! Shell cũng tuân theo triết lý này, cho phép bạn — ví dụ — sử dụng bất kỳ tiện ích nào chấp nhận các đối số là tệp trên dòng lệnh và kết nối nó với đầu ra của các chương trình, như bạn đã học trong vài cấp độ vừa qua.

 * Thú vị là, chúng ta có thể tiến xa hơn, và kết nối đầu vào cũng như đầu ra của các chương trình vào các đối số của lệnh. Điều này được thực hiện bằng cách sử dụng Thay thế Tiến trình (Process Substitution). Để đọc từ một lệnh (thay thế tiến trình đầu vào), hãy sử dụng `<(lệnh)`. Khi bạn viết `<(lệnh)`, bash sẽ chạy lệnh đó và kết nối đầu ra của nó với một tệp tạm thời mà nó sẽ tạo ra. Tất nhiên, đây không phải là một tệp thực sự, nó được gọi là một named pipe (đường ống có tên), theo nghĩa là nó có một tên tệp:

   ```sh
   hacker@dojo:~$ echo <(echo hi)
   /dev/fd/63
   ```

 * `/dev/fd/63` từ đâu đến? bash đã thay thế `<(echo hi)` bằng đường dẫn của tệp named pipe được kết nối với đầu ra của lệnh! Trong khi lệnh đang chạy, việc đọc từ tệp này sẽ đọc dữ liệu từ đầu ra tiêu chuẩn (standard output) của lệnh đó. Thông thường, điều này được thực hiện bằng các lệnh nhận tệp đầu vào làm đối số:

   ```sh
   hacker@dojo:~$ cat <(echo hi)
   hi
   ```

 * Tất nhiên, bạn có thể chỉ định điều này nhiều lần:

   ```sh
   hacker@dojo:~$ echo <(echo pwn) <(echo college)
   /dev/fd/63 /dev/fd/64
   hacker@dojo:~$ cat <(echo pwn) <(echo college)
   pwn
   college
   ```
   
 * Bây giờ là thử thách dành cho bạn! Hãy nhớ lại những gì bạn đã học trong thử thách `diff` từ phần Comprehending Commands. Trong thử thách đó, bạn đã so sánh sự khác biệt (diff) giữa hai tệp. Bây giờ, bạn sẽ so sánh sự khác biệt giữa hai tập hợp đầu ra của lệnh: `/challenge/print_decoys`, lệnh này sẽ in ra một loạt các cờ giả (decoy flags), và `/challenge/print_decoys_and_flag`, lệnh này sẽ in ra chính những cái cờ giả đó cộng thêm lá cờ thật.

 * Hãy sử dụng Thay thế Tiến trình (__Process Substitution__) với lệnh `diff` để so sánh đầu ra của hai chương trình này và tìm ra lá cờ của bạn!

 * <img width="981" height="164" alt="image" src="https://github.com/user-attachments/assets/35178b75-bfcd-42b9-95f4-e30e3add5c00" />

</details>


<details>
 <summary>🏴 <code>Writing to multiple programs</code></summary>

 * Giờ đây bạn đã học được rằng thay thế tiến trình (process substitution) có thể khiến đầu ra của lệnh xuất hiện dưới dạng các tệp để đọc bằng cách dùng `<(lệnh)`. Nhưng bạn cũng có thể sử dụng thay thế tiến trình để ghi vào các lệnh!

 * Bạn có thể nhân bản dữ liệu vào hai tệp bằng lệnh `tee`:

   ```sh
   hacker@dojo:~$ echo HACK | tee THE > PLANET
   hacker@dojo:~$ cat THE
   HACK
   hacker@dojo:~$ cat PLANET
   HACK
   ```

 * Và bạn đã từng sử dụng `tee` để nhân bản dữ liệu vào một tệp và một lệnh:

   ```sh
   hacker@dojo:~$ echo HACK | tee THE | cat
   HACK
   hacker@dojo:~$ cat THE
   HACK
   ```
   
 * Nhưng còn việc nhân bản vào hai lệnh thì sao? Như lệnh `tee` đã nêu trong trang hướng dẫn (manpage), nó được thiết kế để ghi vào các tệp và đầu ra tiêu chuẩn (standard output):

   ```bash
   TEE(1)                          User Commands                            TEE(1)
   NAME
         tee - đọc từ đầu vào tiêu chuẩn và ghi vào đầu ra tiêu chuẩn và các tệp
   ```
   
 * Nhưng chờ đã! Bạn vừa học được rằng bash có thể khiến các lệnh trông giống như các tệp bằng cách sử dụng thay thế tiến trình! Để ghi vào một lệnh (thay thế tiến trình đầu ra), hãy sử dụng `>(lệnh)`. Nếu bạn viết một đối số là `>(rev)`, bash sẽ chạy lệnh `rev` (lệnh này đọc dữ liệu từ đầu vào tiêu chuẩn, đảo ngược thứ tự của nó và ghi vào đầu ra tiêu chuẩn!), nhưng kết nối đầu vào của nó với một tệp mang tên "đường ống có tên" (named pipe) tạm thời. Khi các lệnh khác ghi vào tệp này, dữ liệu sẽ đi vào đầu vào tiêu chuẩn của lệnh đó:

   ```sh
   hacker@dojo:~$ echo HACK | rev
   KCAH
   hacker@dojo:~$ echo HACK | tee >(rev)
   HACK
   KCAH
   ```

 * Ở ví dụ trên, chuỗi sự kiện sau đây đã diễn ra:

   * `bash` khởi chạy lệnh `rev`, kết nối một đường ống có tên (có lẽ là `/dev/fd/63`) vào đầu vào tiêu chuẩn của `rev`.

   * `bash` khởi chạy lệnh `tee`, kết nối một đường ống vào đầu vào tiêu chuẩn của nó, và thay thế đối số đầu tiên của `tee` bằng `/dev/fd/63`. Lệnh `tee` thậm chí chưa bao giờ nhìn thấy đối số `>(rev)`; shell đã thay thế nó trước khi khởi chạy `tee`.

   * `bash` sử dụng lệnh tích hợp (builtin) `echo` để in `HACK` vào đầu vào tiêu chuẩn của `tee`.

   * `tee` đọc `HACK`, ghi nó vào đầu ra tiêu chuẩn, sau đó ghi nó vào `/dev/fd/63` (nơi được kết nối với đầu vào tiêu chuẩn của `rev`).

   * `rev` đọc `HACK` từ đầu vào tiêu chuẩn của nó, đảo ngược nó và ghi `KCAH` ra đầu ra tiêu chuẩn.

 * Bây giờ đến lượt bạn! Trong thử thách này, chúng ta có các lệnh `/challenge/hack`, `/challenge/the`, và `/challenge/planet`. Hãy chạy lệnh `/challenge/hack`, và nhân bản đầu ra của nó để làm đầu vào cho cả hai lệnh `/challenge/the` và `/challenge/planet`! Hãy cuộn lại các thử thách trước đó là "Duplicating piped data with tee" và "Process substitution for input" nếu bạn cần ôn lại phương pháp này.

 * Thông tin bên lề (Trivia)!
 
 * Người học có óc quan sát sẽ nhận ra rằng các lệnh sau đây là tương đương:

   ```sh
   hacker@dojo:~$ echo hi | rev
   ih
   hacker@dojo:~$ echo hi > >(rev)
   ih
   ```
   
 * Có nhiều hơn một cách để dẫn đường ống dữ liệu! Tất nhiên, cách thứ hai khó đọc hơn nhiều và cũng khó mở rộng hơn. Ví dụ:

   ```sh
   hacker@dojo:~$ echo hi | rev | rev
   hi
   hacker@dojo:~$ echo hi > >(rev | rev)
   hi
   ```
   
 * Thật là ngớ ngẩn! Bài học ở đây là, mặc dù Thay thế Tiến trình là một công cụ mạnh mẽ trong hộp dụng cụ của bạn, nhưng nó là một công cụ rất chuyên biệt; đừng sử dụng nó cho mọi thứ!

 * <img width="878" height="180" alt="image" src="https://github.com/user-attachments/assets/c48b32d1-c16c-4a8a-91f9-be99d80867be" />

</details>


<details>
 <summary>🏴 <code>Split-piping stderr and stdout</code></summary>

 * Bây giờ, hãy cùng kết hợp những kiến thức của bạn lại với nhau. Bạn phải làm chủ nhiệm vụ điều hướng (piping) tối thượng: chuyển hướng đầu ra tiêu chuẩn (stdout) sang một chương trình và đầu ra lỗi tiêu chuẩn (stderr) sang một chương trình khác.

 * Thử thách ở đây, dĩ nhiên, là toán tử `|` chỉ liên kết stdout của lệnh bên trái với đầu vào tiêu chuẩn (stdin) của lệnh bên phải. Tất nhiên, bạn đã từng sử dụng `2>&1` để chuyển hướng stderr vào stdout và từ đó dẫn stderr đi qua ống dẫn, nhưng điều này lại làm trộn lẫn stderr và stdout với nhau. Làm thế nào để giữ chúng không bị trộn lẫn?

 * Bạn sẽ cần kết hợp kiến thức của mình về `>()`, `2>`, và `|`. Cách thực hiện như thế nào là một nhiệm vụ mà tôi sẽ để lại cho bạn.

 * Trong thử thách này, bạn có:

   * `/challenge/hack`: lệnh này tạo ra dữ liệu trên cả stdout và stderr.

   * `/challenge/the`: bạn phải chuyển hướng stderr của lệnh `hack` sang chương trình này.

   * `/challenge/planet`: bạn phải chuyển hướng stdout của lệnh `hack` sang chương trình này.

 * Hãy đi lấy cờ (flag) về nào!

 * BONUS: Để tăng thêm một chút độ khó, hãy tìm một giải pháp mà không sử dụng toán tử `|`.

 * <img width="864" height="110" alt="image" src="https://github.com/user-attachments/assets/7a72d03c-5957-4447-9836-c113e6b99e49" />

 * <img width="893" height="115" alt="image" src="https://github.com/user-attachments/assets/8ff4c6c8-83da-4e6b-9f4a-2371433fbd87" />


</details>


<details>
 <summary>🏴 <code>Named pipes</code></summary>

 * Dưới đây là bản dịch sát nghĩa và chi tiết toàn bộ nội dung văn bản của bạn:

 * Bạn đã học về các đường ống (pipes) sử dụng `|`, và bạn đã thấy rằng quá trình thay thế tiến trình (process substitution) tạo ra các đường ống có tên tạm thời (named pipes) (như `/dev/fd/63`). Bạn cũng có thể tự tạo ra các đường ống có tên cố định (persistent named pipes) tồn tại lâu dài trên hệ thống tệp! Chúng được gọi là FIFO, viết tắt của First (byte) In, First (byte) Out (Byte vào đầu tiên, Byte ra đầu tiên).

 * Bạn tạo một FIFO bằng cách sử dụng lệnh `mkfifo`:

   ```Bash
   hacker@dojo:~$ mkfifo my_pipe
   hacker@dojo:~$ ls -l my_pipe
   prw-r--r-- 1 hacker hacker 0 Jan 1 12:00 my_pipe
   hacker@dojo:~$ ls -l some_file
   -rw-r--r-- 1 hacker hacker 0 Jan 1 12:00 some_file
   hacker@dojo:~$
   ```
   
 * Hãy chú ý chữ `p` ở đầu phần các quyền (permissions) - điều đó chỉ ra rằng nó là một đường ống! Điều này khác biệt rõ rệt so với dấu `-` nằm ở đầu của các tệp bình thường, chẳng hạn như `some_file` trong ví dụ trên.

 * Khác với các đường ống có tên tự động từ thay thế tiến trình:

   * Bạn kiểm soát được vị trí nơi các FIFO được tạo ra.

   * Chúng tồn tại cố định cho đến khi bạn xóa chúng.

   * Bất kỳ tiến trình nào cũng có thể ghi vào chúng thông qua đường dẫn (ví dụ: `echo hi > my_pipe`).

   * Bạn có thể nhìn thấy chúng bằng lệnh `ls` và kiểm tra chúng giống như các tệp.

 * Một vấn đề với các FIFO là chúng sẽ "chặn" (block) bất kỳ hoạt động nào trên chúng cho đến khi cả phía đọc (read side) và phía ghi (write side) của đường ống đều sẵn sàng. Ví dụ, hãy xem xét trường hợp này:

   ```Bash
   hacker@dojo:~$ mkfifo myfifo
   hacker@dojo:~$ echo pwn > myfifo
   ```
   
 * Để phục vụ lệnh `echo pwn > myfifo`, bash sẽ mở tệp `myfifo` ở chế độ ghi (write mode). Tuy nhiên, thao tác này sẽ bị treo (hang) cho đến khi có một thứ gì đó cũng mở tệp này ở chế độ đọc (read mode) (từ đó hoàn thành đường ống). Việc đó có thể được thực hiện ở một bảng điều khiển (console) khác:

   ```Bash
   hacker@dojo:~$ cat myfifo
   pwn 
   hacker@dojo:~$
   ```
   
 * Chuyện gì đã xảy ra ở đây? Khi chúng ta chạy lệnh `cat myfifo`, đường ống đã có cả hai phía kết nối sẵn sàng, và được bỏ chặn (unblocked), cho phép lệnh `echo pwn > myfifo` chạy, từ đó gửi chuỗi `pwn` vào đường ống, nơi nó được lệnh `cat` đọc.

 * Tất nhiên, điều này phần nào cũng có thể được thực hiện bởi các tệp bình thường: bạn đã học cách dùng lệnh `echo` để đưa nội dung vào chúng và dùng lệnh `cat` để xuất nội dung ra. Tại sao lại dùng FIFO thay thế? Dưới đây là những điểm khác biệt chính:

   * **Không lưu trữ trên ổ đĩa** (No disk storage): FIFO truyền dữ liệu trực tiếp giữa các tiến trình trong bộ nhớ - không có gì được lưu vào ổ đĩa.

   * **Dữ liệu tạm thời** (Ephemeral data): Một khi dữ liệu được đọc khỏi một FIFO, nó sẽ biến mất (không giống như các tệp nơi dữ liệu được lưu trữ lâu dài).

   * **Tự động đồng bộ hóa** (Automatic synchronization): Phía ghi sẽ bị chặn cho đến khi phía đọc sẵn sàng, và ngược lại. Điều này thực sự hữu ích! Nó cung cấp sự đồng bộ hóa tự động. Hãy xem xét ví dụ ở trên: với một FIFO, không quan trọng lệnh `cat myfifo` hay `echo pwn > myfifo` được thực thi trước; mỗi lệnh sẽ chỉ đợi lệnh kia. Với các tệp bình thường, bạn cần đảm bảo thực thi lệnh ghi trước lệnh đọc.

   * **Luồng dữ liệu phức tạp** (Complex data flows): FIFO rất hữu ích trong việc tạo điều kiện cho các luồng dữ liệu phức tạp, kết hợp và chia tách dữ liệu theo những cách linh hoạt, v.v. Ví dụ, FIFO hỗ trợ nhiều bên đọc và bên ghi.

 * Thử thách này sẽ là một bài giới thiệu đơn giản về FIFO. Bạn sẽ cần tạo một tệp `/tmp/flag_fifo` và chuyển hướng đầu ra tiêu chuẩn (stdout) của `/challenge/run` vào đó. Nếu bạn thành công, `/challenge/run` sẽ ghi lá cờ (flag) vào FIFO! Hãy đi làm việc đó đi!

 * GỢI Ý: Hành vi chặn (blocking) của FIFO làm cho việc giải quyết thử thách này trong một terminal (thiết bị đầu cuối) duy nhất trở nên khó khăn. Bạn có thể sẽ muốn sử dụng chế độ Desktop hoặc VSCode cho thử thách này để bạn có thể khởi chạy hai terminal.

 * <img width="1082" height="1239" alt="image" src="https://github.com/user-attachments/assets/1f3325d7-a5e1-44bf-8886-4c2461729318" />



</details>
