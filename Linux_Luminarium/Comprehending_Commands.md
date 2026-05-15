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


<details>
  <summary>🏴 <code>making directories</code></summary>

  * Chúng ta có thể tạo các tệp. Còn các thư mục thì sao? Bạn tạo (make) các thư mục bằng cách sử dụng lệnh  `mkdir`. Sau đó, bạn có thể đặt các tệp vào trong đó!
  
  * Hãy xem :

    ```sh
    hacker@dojo:~$ cd /tmp
    hacker@dojo:/tmp$ ls
    hacker@dojo:/tmp$ ls
    hacker@dojo:/tmp$ mkdir my_directory
    hacker@dojo:/tmp$ ls
    my_directory
    hacker@dojo:/tmp$ cd my_directory
    hacker@dojo:/tmp/my_directory$ touch my_file
    hacker@dojo:/tmp/my_directory$ ls
    my_file
    hacker@dojo:/tmp/my_directory$ ls /tmp/my_directory/my_file
    /tmp/my_directory/my_file
    hacker@dojo:/tmp/my_directory$

  * Bây giờ, hãy tiến tới và tạo một thư mục `/tmp/pwn` và tạo một tệp `college` ở trong đó! Sau đó chạy chương trình `/challenge/run`, lệnh này sẽ kiểm tra giải pháp của bạn và cấp cho bạn cờ (flag)!

  * <img width="544" height="168" alt="image" src="https://github.com/user-attachments/assets/be26d0d5-5a82-44b0-932c-db4b742b4106" />

</details>

<details>
  <summary>🏴 <code>finding files</code></summary>

  * Vậy là bây giờ chúng ta đã biết cách liệt kê, đọc và tạo các tệp. Nhưng làm thế nào để chúng ta tìm thấy chúng? Chúng ta sử dụng lệnh `find`!

  * Lệnh `find` nhận các đối số tùy chọn mô tả các tiêu chí tìm kiếm và vị trí tìm kiếm. Nếu bạn không chỉ định tiêu chí tìm kiếm, `find` sẽ khớp với mọi tệp. Nếu bạn không chỉ định vị trí tìm kiếm, `find` sẽ sử dụng thư mục làm việc hiện tại (`.`). Ví dụ:

    ```sh
    hacker@dojo:~$ mkdir my_directory
    hacker@dojo:~$ mkdir my_directory/my_subdirectory
    hacker@dojo:~$ touch my_directory/my_file
    hacker@dojo:~$ touch my_directory/my_subdirectory/my_subfile
    hacker@dojo:~$ find
    .
    ./my_directory
    ./my_directory/my_subdirectory
    ./my_directory/my_subdirectory/my_subfile
    ./my_directory/my_file
    hacker@dojo:~$
    ```
    
  * Và khi chỉ định vị trí tìm kiếm:  

    ```sh
    hacker@dojo:~$ find my_directory/my_subdirectory
    my_directory/my_subdirectory
    my_directory/my_subdirectory/my_subfile
    hacker@dojo:~$
    ```
    
  * Và, tất nhiên, chúng ta có thể chỉ định các tiêu chí! Ví dụ, ở đây, chúng ta lọc theo tên:  

    ```sh
    hacker@dojo:~$ find -name my_subfile
    ./my_directory/my_subdirectory/my_subfile
    hacker@dojo:~$ find -name my_subdirectory
    ./my_directory/my_subdirectory
    hacker@dojo:~$
    ```
    
  * Bạn có thể tìm kiếm trên toàn bộ hệ thống tệp nếu bạn muốn!

    ```sh
    hacker@dojo:~$ find / -name hacker
    /home/hacker
    hacker@dojo:~$
    ```

  * Bây giờ đến lượt bạn. Tôi đã giấu cờ (flag) trong một thư mục ngẫu nhiên trên hệ thống tệp. Nó vẫn được gọi là `flag`. Hãy đi tìm nó!

  * Một vài lưu ý. Đầu tiên, có những tệp khác cũng được đặt tên là `flag` trên hệ thống tệp. Đừng hoảng sợ nếu tệp đầu tiên bạn thử không chứa cờ thực sự trong đó. Thứ hai, có rất nhiều nơi trong hệ thống tệp không thể truy cập được đối với một người dùng bình thường. Những nơi này sẽ khiến `find` tạo ra các lỗi, nhưng bạn có thể bỏ qua chúng; chúng tôi sẽ không giấu cờ ở đó đâu! Cuối cùng, `find` có thể mất một khoảng thời gian; hãy kiên nhẫn nhé!

  * <img width="873" height="509" alt="image" src="https://github.com/user-attachments/assets/8ad4b2b1-9d07-4981-a5af-25c3880c9fe8" />

</details>


<details>
  <summary>🎥 <code>Symbolic Links</code></summary>

  * **A deeper look at files**

    Có nhiều loại tệp khác nhau. Bạn có thể sử dụng lệnh `ls -ld /path/to/your/file` để kiểm tra.

    ```sh
    yans@asdf ~ $ ls -ld /home/yans/flags
    drwxr-xr-x 2 yans users 4096 Aug 19 06:30 /home/yans/flags
    yans@asdf ~ $ ls -ld /home/yans/flags/TOPSECRET
    -rw-r--r-- 1 yans users 18 Aug 19 06:30 /home/yans/flags/TOPSECRET
    yans@asdf ~ $ █
    ```

    * Types:

      * `-` là một tệp thông thường (regular file)
      * `d` là một thư mục (các thư mục thực chất chỉ là các tệp đặc biệt)
      * `l` là một liên kết tượng trưng (symbolic link - một tệp con trỏ một cách trong suốt đến một tệp hoặc thư mục khác.)
      * `p` là một đường ống có tên (named pipe - còn được gọi là FIFO. Bạn sẽ trở nên rất quen thuộc với những thứ này trong module này!)
      * `c` là một tệp thiết bị ký tự (character device file - tức là, được hỗ trợ/đại diện bởi một thiết bị phần cứng tạo ra hoặc nhận các luồng dữ liệu, chẳng hạn như micrô)
      * `b` là một tệp thiết bị khối (block device file - tức là, được hỗ trợ/đại diện bởi một thiết bị phần cứng lưu trữ và tải các khối dữ liệu, chẳng hạn như ổ cứng)
      * `s` là một unix socket (về cơ bản là một kết nối mạng cục bộ được đóng gói trong một tệp)

  * **Symbolic (AKA soft) links?**

    Một liên kết tượng trưng/mềm (symbolic/soft link) là một loại tệp đặc biệt tham chiếu đến một tệp khác.

    Chúng được tạo ra bằng lệnh `ln -s`, `-s` viết tắt của _symbolic_

    ```sh
    yans@asdf ~ $ ln -s flags/TOPSECRET link_to_the_flag
    yans@asdf ~ $ ls -l
    total 24
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 Desktop
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 Documents
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 Downloads
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 Pictures
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 code
    drwxr-xr-x 2 yans users 4096 Aug 19 06:30 flags
    lrwxrwxrwx 1 yans users   15 Aug 19 07:29 link_to_the_flag -> flags/TOPSECRET
    yans@asdf ~ $ cat ./link_to_the_flag
    pwn_college{1337}
    yans@asdf ~ $ █
    ```

    Bạn cũng có thể liên kết các thư mục:

    ```sh
    yans@asdf ~ $ ln -s flags link_to_flags_dir
    yans@asdf ~ $ ls -ld link_to_flags_dir
    lrwxrwxrwx 1 yans users 5 Aug 19 07:32 link_to_flags_dir -> flags
    yans@asdf ~ $ cat link_to_flags_dir/TOPSECRET
    pwn_college{1337}
    yans@asdf ~ $ █
    ```

  * **Symbolic link gotchas** (gotchas: những cạm bẫy)

    Hãy cẩn thận (Beware): các liên kết tượng trưng trỏ đến các đường dẫn tương đối (relative paths) sẽ mang tính tương đối **so với thư mục chứa liên kết đó**!

    ```sh
    yans@asdf ~ $ ln -s flags/TOPSECRET link_to_the_flag
    yans@asdf ~ $ ls -l link_to_the_flag
    lrwxrwxrwx 1 yans users 15 Aug 19 07:45 link_to_the_flag -> flags/TOPSECRET
    yans@asdf ~ $ cat link_to_the_flag
    pwn_college{1337}
    yans@asdf ~ $ mv link_to_the_flag /tmp
    yans@asdf ~ $ ls -l /tmp
    total 0
    lrwxrwxrwx 1 yans users 15 Aug 19 07:45 link_to_the_flag -> flags/TOPSECRET
    yans@asdf ~ $ cat /tmp/link_to_the_flag
    cat: /tmp/link_to_the_flag: No such file or directory
    yans@asdf ~ $ █
    ```

    So với đường dẫn tuyệt đối (absolute path):

    ```sh
    yans@asdf ~ $ ln -s /home/yans/flags/TOPSECRET link_to_the_flag
    yans@asdf ~ $ ls -l link_to_the_flag
    lrwxrwxrwx 1 yans users 26 Aug 19 07:49 link_to_the_flag -> /home/yans/flags/TOPSECRET
    yans@asdf ~ $ cat link_to_the_flag
    pwn_college{1337}
    yans@asdf ~ $ mv link_to_the_flag /tmp
    yans@asdf ~ $ ls -l /tmp/link_to_the_flag
    lrwxrwxrwx 1 yans users 26 Aug 19 07:49 /tmp/link_to_the_flag -> /home/yans/flags/TOPSECRET
    yans@asdf ~ $ cat /tmp/link_to_the_flag
    pwn_college{1337}
    yans@asdf ~ $ █
    ```

    
  * **Hard Links?**

    Sự tồn tại của các liên kết mềm (soft links) ngụ ý sự tồn tại của một liên kết cứng (hard link).

    Các liên kết cứng (được tạo bằng lệnh ln mà không có đối số -s) tham chiếu trực tiếp đến tệp gốc bằng cách thực hiện phép thuật (magic) với những từ ngữ đáng sợ như "inode".

    ```sh
    yans@asdf ~ $ ln flags/TOPSECRET hard_link_to_flag
    yans@asdf ~ $ ls -l
    total 28
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 Desktop
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 Documents
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 Downloads
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 Pictures
    drwxr-xr-x 2 yans users 4096 Aug 19 06:27 code
    drwxr-xr-x 2 yans users 4096 Aug 19 07:33 flags
    -rw-r--r-- 2 yans users   18 Aug 19 06:30 hard_link_to_flag
    yans@asdf ~ $ cat hard_link_to_flag
    pwn_college{1337}
    yans@asdf ~ $ █
    ```

    Một liên kết cứng là một tham chiếu "hợp lệ" (valid) đến tệp gốc ngang bằng với chính bản thân tệp gốc đó. Nó là một tệp tình cờ được hỗ trợ (backed by) bởi cùng một dữ liệu giống hệt như tệp gốc.
</details>


<details>
  
  <summary>🏴 <code>Linking files</code></summary>

  * Nếu bạn sử dụng Linux (hoặc máy tính) trong một khoảng thời gian đủ lâu để làm bất kỳ công việc thực sự nào, cuối cùng bạn sẽ gặp phải một biến thể nào đó của tình huống sau: bạn muốn hai chương trình truy cập vào cùng một dữ liệu, nhưng các chương trình lại mong đợi dữ liệu đó nằm ở hai vị trí khác nhau. May mắn thay, Linux cung cấp một giải pháp cho tình thế khó khăn (quandary) này: các liên kết (links).

  * Các liên kết có hai loại (hương vị): liên kết cứng (hard) và mềm (soft - còn được gọi là liên kết tượng trưng - symbolic). Chúng ta sẽ phân biệt hai loại này bằng một phép loại suy (analogy):

    * Một liên kết cứng giống như khi bạn định địa chỉ cho căn hộ của mình bằng nhiều địa chỉ mà tất cả đều dẫn trực tiếp đến cùng một nơi (ví dụ: Căn hộ số 2 so với Phòng số 2).

    * Một liên kết mềm giống như khi bạn chuyển căn hộ và yêu cầu dịch vụ bưu chính tự động chuyển tiếp thư từ nơi ở cũ sang nơi ở mới của bạn.

  * Trong một hệ thống tệp, về mặt khái niệm, một tệp là một địa chỉ nơi chứa nội dung của tệp đó sinh sống (tồn tại). Một liên kết cứng là một địa chỉ thay thế dùng để chỉ mục (indexes) dữ liệu đó --- các truy cập vào liên kết cứng và các truy cập vào tệp gốc hoàn toàn giống hệt nhau, ở chỗ chúng ngay lập tức mang lại dữ liệu cần thiết. Thay vào đó, một liên kết mềm/tượng trưng lại chứa tên tệp gốc. Khi bạn truy cập liên kết tượng trưng, Linux sẽ nhận ra rằng nó là một liên kết tượng trưng, đọc tên tệp gốc, và sau đó (thông thường) tự động truy cập tệp đó. Trong hầu hết các trường hợp, cả hai tình huống đều dẫn đến việc truy cập vào dữ liệu gốc, nhưng các cơ chế thì khác nhau.

  * Các liên kết cứng nghe có vẻ đơn giản hơn đối với hầu hết mọi người (ví dụ điển hình, tôi đã giải thích nó trong một câu ở trên, so với hai câu cho liên kết mềm), nhưng chúng có nhiều nhược điểm (downsides) và những cạm bẫy khi triển khai (implementation gotchas) khiến các liên kết mềm/tượng trưng trở thành giải pháp thay thế phổ biến hơn rất nhiều.

  * Trong thử thách này, chúng ta sẽ tìm hiểu về các liên kết tượng trưng (còn được gọi là symlinks). Các liên kết tượng trưng được tạo ra bằng lệnh `ln` với đối số `-s`, giống như thế này:

    ```sh
    hacker@dojo:~$ cat /tmp/myfile
    This is my file!
    hacker@dojo:~$ ln -s /tmp/myfile /home/hacker/ourfile
    hacker@dojo:~$ cat ~/ourfile
    This is my file!
    hacker@dojo:~$
    ```

  * Bạn có thể thấy rằng việc truy cập vào symlink sẽ dẫn đến việc lấy được nội dung tệp gốc! Ngoài ra, bạn có thể thấy cách sử dụng lệnh `ln -s`. Lưu ý rằng đường dẫn tệp gốc đứng trước đường dẫn liên kết trong lệnh!

  * Một symlink có thể được nhận dạng như vậy bằng một vài phương pháp. Ví dụ, lệnh `file`, lệnh này nhận một tên tệp và cho bạn biết nó là loại tệp gì, sẽ nhận ra các symlinks:
    ```sh
    hacker@dojo:~$ file /tmp/myfile
    /tmp/myfile: ASCII text
    hacker@dojo:~$ file ~/ourfile
    /home/hacker/ourfile: symbolic link to /tmp/myfile
    hacker@dojo:~$
    ```

  * Được rồi, bây giờ bạn hãy thử xem! Trong cấp độ này, cờ (flag), như thường lệ, nằm ở `/flag`, nhưng chương trình `/challenge/catflag` thay vào đó sẽ đọc tệp `/home/hacker/not-the-flag`. Hãy sử dụng symlink, và đánh lừa nó để nó cấp cho bạn cờ!

  * <img width="548" height="186" alt="image" src="https://github.com/user-attachments/assets/5ce69de1-759e-4024-8d79-56517f6713ed" />

</details>
