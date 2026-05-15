  # Comprehending Comman
* Module này sẽ cho bạn tiếp xúc với một số lệnh Linux hữu ích, những lệnh này sẽ phục vụ tốt cho bạn trong phần còn lại của cuộc hành trình tại đây! Đây CÒN LÂU mới là một danh sách đầy đủ (tường tận), và chúng tôi sẽ tiếp tục mở rộng module này, nhưng ngần này là đủ để giúp bạn bắt đầu.

* Vì vậy, không chần chừ thêm nữa, hãy cùng học một số lệnh nào!

<details>
  <summary>🏴 <code>cat: not the pet, but the command!</code></summary>

  * Một trong những lệnh Linux quan trọng nhất là `cat`. `cat` thường được sử dụng nhất để đọc nội dung các tệp (reading out files), giống như thế này:

    ```sh
    hacker@dojo:~$ cat /challenge/DESCRIPTION.md
    Một trong những lệnh Linux quan trọng nhất là `cat`.
    `cat` thường được sử dụng nhất để đọc các tệp, giống như thế này:
    ```

  * `cat` sẽ nối (concatenate - do đó mới có cái tên này) nhiều tệp lại với nhau nếu được cung cấp nhiều đối số. Ví dụ:

    ```sh
    hacker@dojo:~$ cat myfile
    This is my file!
    hacker@dojo:~$ cat yourfile
    This is your file!
    hacker@dojo:~$ cat myfile yourfile
    This is my file!
    This is your file!
    hacker@dojo:~$ cat myfile yourfile myfile
    This is my file!
    This is your file!
    This is my file!
    ```

  * Cuối cùng, nếu bạn hoàn toàn không đưa ra đối số nào, `cat` sẽ đọc từ đầu vào của terminal và xuất nó ra. Chúng ta sẽ khám phá điều đó trong các thử thách sau...  

  * Trong thử thách này, tôi sẽ sao chép cờ (flag) vào tệp `flag` nằm trong thư mục nhà (home directory) của bạn (nơi shell của bạn bắt đầu). Hãy đi đọc nó bằng `cat`!

  * <img width="565" height="105" alt="image" src="https://github.com/user-attachments/assets/7f8ebd40-3bfe-41ae-8148-75761cdd3979" />

</details>


<details>
  <summary>🏴 <code>catting absolute paths</code></summary>

  * Trong cấp độ trước, bạn đã thực hiện lệnh `cat flag` để đọc cờ từ thư mục nhà của bạn! Tất nhiên, bạn có thể chỉ định các đối số của `cat` dưới dạng các đường dẫn tuyệt đối:

    ```sh
    hacker@dojo:~$ cat /challenge/DESCRIPTION.md
    Trong cấp độ trước, bạn đã thực hiện `cat flag` để đọc cờ từ thư mục nhà của bạn!
    Tất nhiên, bạn có thể chỉ định các đối số của `cat`'s dưới dạng các đường dẫn tuyệt đối:
    ...
    ```
    
  * Trong thử thách này, tôi sẽ không sao chép nó vào thư mục nhà của bạn, nhưng tôi sẽ làm cho nó có thể đọc được. Bạn có thể đọc nó bằng lệnh `cat` tại đường dẫn tuyệt đối của nó: `/flag`.

  * SỰ THẬT THÚ VỊ (FUN FACT): `/flag` là nơi mà cờ _luôn luôn_ nằm ở đó trong pwn.college, nhưng không giống như trong thử thách này, bạn thường không thể trực tiếp truy cập vào tệp đó.

  * <img width="553" height="96" alt="image" src="https://github.com/user-attachments/assets/3c3aa22a-1cd9-45ac-bc87-a0aebfb4a173" />

</details>

<details>
  <summary>🏴 <code>more catting practice</code></summary>

  * Bạn có thể chỉ định mọi loại đường dẫn như là các đối số cho các lệnh, và chúng ta sẽ thực hành thêm một chút với `cat`. Trong cấp độ này, tôi sẽ đặt cờ (flag) vào một thư mục điên rồ (kỳ quái) nào đó, và tôi sẽ không cho phép bạn thay đổi các thư mục bằng lệnh `cd`, vì vậy không có chuyện dùng `cat flag` cho bạn đâu. Bạn phải lấy được cờ bằng đường dẫn tuyệt đối, cho dù nó ở bất cứ đâu.

  * <img width="633" height="148" alt="image" src="https://github.com/user-attachments/assets/1bf39ef9-ed32-41d4-87db-c73943495cc8" />

</details>


<details>
  <summary>🏴 <code>grepping for a needle in a haystack</code></summary>

  * Đôi khi, các tệp mà bạn có thể xuất ra bằng lệnh `cat` lại quá lớn. Thật may mắn, chúng ta có lệnh `grep` để tìm kiếm các nội dung mà chúng ta cần! Chúng ta sẽ học nó trong thử thách này.

  * Có rất nhiều cách để sử dụng `grep`, và chúng ta sẽ học một cách tại đây:

    ```sh
    hacker@dojo:~$ grep SEARCH_STRING /path/to/file
    ```
    
  * Được gọi theo cách này, `grep` sẽ tìm kiếm trong tệp các dòng văn bản có chứa `SEARCH_STRING` (chuỗi tìm kiếm) và in chúng ra màn hình console.

  * Trong thử thách này, tôi đã đặt một trăm nghìn dòng văn bản vào tệp `/challenge/data.txt`. Hãy dùng `grep` với nó để tìm cờ (flag)!

  * GỢI Ý: Cờ luôn luôn bắt đầu bằng đoạn văn bản `pwn.college`.

  * <img width="754" height="84" alt="image" src="https://github.com/user-attachments/assets/ff45ab83-0d80-478d-940b-fe6edf6bdf71" />

</details>

<details>
  <summary>🏴 <code>comparing files</code></summary>

  * Khi tìm kiếm các thay đổi giữa các tệp tương tự nhau, việc chỉ kiểm tra bằng mắt (eyeballing) có thể không phải là cách tiếp cận hiệu quả nhất! Đây là lúc lệnh `diff` trở nên vô giá.

  * `diff` so sánh hai tệp từng dòng một và cho bạn thấy chính xác những gì khác biệt giữa chúng. Ví dụ:
    ```sh
    hacker@dojo:~$ cat file1
    hello
    world
    hacker@dojo:~$ cat file2
    hello
    universe
    hacker@dojo:~$ diff file1 file2
    2c2
    < world
    ---
    > universe
    ```
    
  * Đầu ra cho chúng ta biết rằng dòng thứ 2 đã thay đổi (`2c2`), với từ `world` trong tệp đầu tiên (`<`) được thay thế bằng từ `universe` trong tệp thứ hai (`>`).

  * Đôi khi, khi các dòng mới được thêm vào, bạn sẽ thấy một kết quả giống như thế này:
    ```sh
    hacker@dojo:~$ cat old
    pwn
    hacker@dojo:~$ cat new
    pwn
    college
    hacker@dojo:~$ diff old new
    1a2
    > college
    ```

  * Điều này cho chúng ta biết rằng sau dòng 1 trong tệp đầu tiên, tệp thứ hai có thêm một dòng bổ sung (`1a2` có nghĩa là "sau dòng 1 của file1, thêm dòng 2 của file2").

  * Bây giờ là phần thử thách dành cho bạn! Có hai tệp nằm trong thư mục `/challenge`:

    * `/challenge/decoys_only.txt` chứa 100 cờ giả (fake flags).

    * `/challenge/decoys_and_real.txt` chứa tất cả 100 cờ giả đó cộng thêm một cờ thật.

  * Hãy sử dụng lệnh `diff` để tìm ra điểm khác biệt giữa các tệp này và lấy cờ (flag) của bạn!

  * <img width="713" height="127" alt="image" src="https://github.com/user-attachments/assets/ca1d244a-3082-42b6-b4a7-a9004e2cc527" />

</details>


<details>
  <summary>🏴 <code>listing files</code></summary>

  * Cho đến nay, chúng tôi đã cho bạn biết cần tương tác với những tệp nào. Nhưng các thư mục có thể chứa rất nhiều tệp (và các thư mục khác) bên trong chúng, và chúng tôi sẽ không phải lúc nào cũng ở đây để cho bạn biết tên của chúng. Bạn sẽ cần phải học cách liệt kê nội dung của chúng bằng cách sử dụng lệnh `ls`!

  * `ls` sẽ liệt kê các tệp trong tất cả các thư mục được cung cấp cho nó dưới dạng các đối số, và trong thư mục hiện tại nếu không có đối số nào được cung cấp. Hãy quan sát:

    ```sh
    hacker@dojo:~$ ls /challenge
    run
    hacker@dojo:~$ ls
    Desktop    Downloads  Pictures  Templates
    Documents  Music      Public    Videos
    hacker@dojo:~$ ls /home/hacker
    Desktop    Downloads  Pictures  Templates
    Documents  Music      Public    Videos
    hacker@dojo:~$
    ```
    

  * Trong thử thách này, chúng tôi đã đặt cho chương trình `/challenge/run` một cái tên ngẫu nhiên nào đó! Hãy liệt kê các tệp trong thư mục `/challenge` để tìm nó.

  * <img width="564" height="148" alt="image" src="https://github.com/user-attachments/assets/f435e9d1-4889-4837-88ff-ece4c424af07" />

</details>

<details>
  <summary>🏴 <code>touching files</code></summary>

  * Tất nhiên, bạn cũng có thể tạo các tệp! Có một vài cách để làm điều này, nhưng chúng ta sẽ xem xét một lệnh đơn giản ở đây. Bạn có thể tạo một tệp mới, trống rỗng bằng cách "chạm" (touching) vào nó bằng lệnh `touch`:

    ```sh
    hacker@dojo:~$ cd /tmp
    hacker@dojo:/tmp$ ls
    hacker@dojo:/tmp$ touch pwnfile
    hacker@dojo:/tmp$ ls
    pwnfile
    hacker@dojo:/tmp$
    ```

  * Nó đơn giản như vậy đấy! Trong cấp độ này, vui lòng tạo hai tệp: `/tmp/pwn` và `/tmp/college`, sau đó chạy chương trình `/challenge/run` để lấy cờ của bạn!

  * <img width="501" height="160" alt="image" src="https://github.com/user-attachments/assets/9eb81338-0593-471a-b80c-c0f0e9048060" />

</details>

<details>
  <summary>🏴 <code>removing files</code></summary>

  * Các tệp luôn ở xung quanh bạn. Giống như những vỏ kẹo, rồi cuối cùng sẽ có quá nhiều tệp. Trong cấp độ này, chúng ta sẽ học cách dọn dẹp!

  * Trong Linux, bạn loại bỏ (xóa) các tệp bằng lệnh `rm`, giống như thế này:

    ```sh
    hacker@dojo:~$ touch PWN
    hacker@dojo:~$ touch COLLEGE
    hacker@dojo:~$ ls
    COLLEGE     PWN
    hacker@dojo:~$ rm PWN
    hacker@dojo:~$ ls
    COLLEGE
    hacker@dojo:~$
    ```

  * Hãy cùng thực hành. Thử thách này sẽ tạo một tệp `delete_me` trong thư mục nhà (home directory) của bạn! Hãy xóa nó, sau đó chạy lệnh `/challenge/check`, lệnh này sẽ đảm bảo rằng bạn đã xóa nó và sau đó cấp cho bạn cờ (flag)!
  
  * <img width="543" height="137" alt="image" src="https://github.com/user-attachments/assets/442bdf88-94f9-4344-a5d8-ec8eace55d24" />

</details>

<details>
  <summary>🏴 <code>moving files</code></summary>

  * Bạn cũng có thể di chuyển các tệp qua lại bằng lệnh `mv`. Cách sử dụng rất đơn giản:

    ```sh
    hacker@dojo:~$ ls
    my-file
    hacker@dojo:~$ cat my-file
    PWN!
    hacker@dojo:~$ mv my-file your-file
    hacker@dojo:~$ ls
    your-file
    hacker@dojo:~$ cat your-file
    PWN!
    hacker@dojo:~$
    ```

  * Thử thách này muốn bạn di chuyển tệp `/flag` vào `/tmp/hack-the-planet` (hãy làm đi!). Khi bạn hoàn thành, hãy chạy lệnh `/challenge/check`, lệnh này sẽ kiểm tra mọi thứ và cấp cờ (flag) cho bạn.

  * <img width="681" height="162" alt="image" src="https://github.com/user-attachments/assets/91411741-ee76-4566-8333-124a47fbd527" />

</details>


<details>
  <summary>🏴 <code>copying files</code></summary>

  * Nhưng nếu bạn muốn giữ lại tệp gốc thì sao? Bạn có thể làm như vậy bằng lệnh `cp`. Cách sử dụng cũng giống như với lệnh `mv`, nhưng nó sẽ giữ lại tệp nguồn.

  * Thử thách này muốn bạn sao chép tệp `/flag` vào `/tmp/hack-the-planet` (hãy làm đi)! Khi bạn hoàn thành, hãy chạy lệnh `/challenge/check`, lệnh này sẽ kiểm tra mọi thứ và cấp cờ (flag) cho bạn.

  * <img width="668" height="169" alt="image" src="https://github.com/user-attachments/assets/5209a02c-7600-42b0-b412-a74e4691bf37" />

</details>


<details>
  <summary>🏴 <code>hidden files</code></summary>

  * Thật thú vị là theo mặc định, `ls` không liệt kê tất cả các tệp tin. Linux có một quy ước trong đó các tệp tin bắt đầu bằng dấu `.` sẽ không hiển thị theo mặc định khi dùng ls cũng như trong một vài ngữ cảnh khác. Để xem chúng bằng lệnh `ls`, bạn cần gọi `ls` với cờ `-a`, giống như thế này:

    ```sh
    hacker@dojo:~$ touch pwn
    hacker@dojo:~$ touch .college
    hacker@dojo:~$ ls
    pwn
    hacker@dojo:~$ ls -a
    .college	pwn
    hacker@dojo:~$
    ```
  * Bây giờ, đến lượt bạn! Hãy đi tìm flag, thứ đang được giấu dưới dạng một tệp tin có dấu chấm ở phía trước trong thư mục `/`.

  * <img width="770" height="155" alt="image" src="https://github.com/user-attachments/assets/93d068f9-6c6a-410e-8d03-1ce0aa3c46e8" />

</details>


<details>
  <summary>🏴 <code>An Epic Filesystem Quest</code></summary>

  * Với kiến thức của bạn về `cd`, `ls`, và `cat`, chúng ta đã sẵn sàng để chơi một trò chơi nhỏ!
    
  * Chúng ta sẽ bắt đầu trò chơi này tại thư mục `/`. Thông thường:

    ```sh
    hacker@dojo:~$ cd /
    hacker@dojo:~$ ls
    bin   challenge  etc   home  lib32  libx32  mnt  proc  run   srv  tmp  var
    boot  dev        flag  lib   lib64  media   opt  root  sbin  sys  usr
    ```
    
  * Nội dung ở đó thật là nhiều! Một ngày nào đó, bạn sẽ khá quen thuộc với chúng, nhưng ngay bây giờ, bạn có thể đã nhận ra tệp tin `flag` và thư mục `challenge`.

  * Trong thử thách này, tôi đã giấu flag đi! Tại đây, bạn sẽ sử dụng `ls` và `cat` để đi theo các dấu vết (manh mối) của tôi và tìm ra nó! Trò chơi sẽ hoạt động như sau:
  
    1. Manh mối đầu tiên của bạn nằm ở thư mục `/`. Hãy đi thẳng đến đó.
    2. Nhìn xung quanh bằng lệnh `ls`. Sẽ có một tệp tin tên là HINT hoặc CLUE hoặc thứ gì đó tương tự như vậy!
    3. `cat` tệp tin đó để đọc manh mối!
    4. Tùy thuộc vào những gì manh mối chỉ dẫn, hãy đi đến thư mục tiếp theo (hoặc không cần!).
    5. Đi theo các manh mối để tìm đến flag!
  
  * Chúc may mắn!

  * <img width="1046" height="636" alt="image" src="https://github.com/user-attachments/assets/e64662e5-7157-4340-8890-cd8dadb140bf" />

  * <img width="1032" height="757" alt="image" src="https://github.com/user-attachments/assets/0f8dd8f9-e1ad-4578-bafa-889aa618cc76" />

</details>
