# File Globbing

* Thậm chí chỉ mới trải qua một vài cấp độ, bạn có thể đã cảm thấy mệt mỏi với việc phải gõ ra tất cả các đường dẫn tệp này. May mắn thay, shell có một giải pháp: globbing (khớp mẫu đại diện)! Đó là những gì chúng ta sẽ học trong module này.

* Trước khi thực thi các lệnh mà bạn nhập vào, shell trước tiên sẽ thực hiện các phép mở rộng (expansions) trên chúng, và một trong những phép mở rộng này chính là globbing. Globbing cho phép bạn tham chiếu đến các tệp mà không cần phải gõ toàn bộ chúng ra, hoặc gõ ra các đường dẫn đầy đủ của chúng. Hãy cùng đi sâu vào tìm hiểu nhé!


<details>
  <summary>🏴 <code>Matching with *</code></summary>

  * Glob (mẫu đại diện) đầu tiên mà chúng ta sẽ học là `*`. Khi gặp một ký tự `*` trong bất kỳ đối số nào, shell sẽ coi nó như một "ký tự đại diện" (wildcard) và cố gắng thay thế đối số đó bằng bất kỳ tệp nào khớp với mẫu (pattern). Việc cho bạn thấy thì dễ hơn là giải thích:

    ```sh
    hacker@dojo:~$ touch file_a
    hacker@dojo:~$ touch file_b
    hacker@dojo:~$ touch file_c
    hacker@dojo:~$ ls
    file_a	file_b	file_c
    hacker@dojo:~$ echo Look: file_*
    Look: file_a file_b file_c
    ```
    
  * Tất nhiên, mặc dù trong trường hợp này, glob dẫn đến nhiều đối số, nó cũng có thể khớp với chỉ một đối số một cách đơn giản tương tự. Ví dụ:

    ```sh
    hacker@dojo:~$ touch file_a
    hacker@dojo:~$ ls
    file_a
    hacker@dojo:~$ echo Look: file_*
    Look: file_a
    ```
    
  * Khi không có tệp nào khớp, theo mặc định, shell sẽ giữ nguyên glob không thay đổi:

    ```sh
    hacker@dojo:~$ touch file_a
    hacker@dojo:~$ ls
    file_a
    hacker@dojo:~$ echo Look: nope_*
    Look: nope_*
    ```
    
  * Ký tự `*` khớp với bất kỳ phần nào của tên tệp ngoại trừ `/` hoặc ký tự `.` đứng ở đầu. Ví dụ:

    ```sh
    hacker@dojo:~$ echo ONE: /ho*/*ck*
    ONE: /home/hacker
    hacker@dojo:~$ echo TWO: /*/hacker
    TWO: /home/hacker
    hacker@dojo:~$ echo THREE: ../*
    THREE: ../hacker
    ```
    
  * Bây giờ, hãy tự mình thực hành điều này! Bắt đầu từ thư mục nhà (home directory) của bạn, hãy chuyển thư mục của bạn sang `/challenge`, nhưng hãy sử dụng globbing để giữ cho đối số mà bạn truyền cho lệnh `cd` có tối đa bốn ký tự! Khi bạn đã ở đó, hãy chạy chương trình `/challenge/run` để lấy cờ!

  * <img width="675" height="191" alt="image" src="https://github.com/user-attachments/assets/0cf07f39-46e5-423a-bafa-97ffe78b99d9" />

</details>


<details>
  <summary>🏴 <code>Matching with ?</code></summary>

  * Tiếp theo, hãy cùng tìm hiểu về `?`. Khi gặp một ký tự `?` trong bất kỳ đối số nào, **shell** sẽ coi nó như một ký tự đại diện cho *một ký tự duy nhất* (single-character wildcard). Điều này hoạt động giống như ***, nhưng chỉ khớp với một ký tự. Ví dụ:

    ```sh
    hacker@dojo:~$ touch file_a
    hacker@dojo:~$ touch file_b
    hacker@dojo:~$ touch file_cc
    hacker@dojo:~$ ls
    file_a	file_b	file_cc
    hacker@dojo:~$ echo Look: file_?
    Look: file_a file_b
    hacker@dojo:~$ echo Look: file_??
    Look: file_cc
    ```

  * Bây giờ, hãy tự mình thực hành điều này! Bắt đầu từ thư mục nhà (home directory) của bạn, hãy chuyển thư mục của bạn sang `/challenge`, nhưng hãy sử dụng ký tự `?` thay vì `c` và `l` trong đối số cho lệnh `cd`! Khi bạn đã ở đó, hãy chạy chương trình `/challenge/run` để lấy cờ (flag)!

  * <img width="666" height="203" alt="image" src="https://github.com/user-attachments/assets/88dbaac5-d058-485c-846e-3ca4452bdbce" />

</details>


<details>
  <summary>🏴 <code>Matching with []</code></summary>

  * Tiếp theo, chúng ta sẽ tìm hiểu về `[]`. Các dấu ngoặc vuông, về cơ bản, là một dạng giới hạn của `?`, ở chỗ thay vì khớp với bất kỳ ký tự nào, `[]` là một ký tự đại diện (wildcard) cho một tập hợp con các ký tự tiềm năng, được chỉ định bên trong các dấu ngoặc. Ví dụ, `[pwn]` sẽ khớp với ký tự `p`, `w`, hoặc `n`. Ví dụ:

    ```sh
    hacker@dojo:~$ touch file_a
    hacker@dojo:~$ touch file_b
    hacker@dojo:~$ touch file_c
    hacker@dojo:~$ ls
    file_a	file_b	file_c
    hacker@dojo:~$ echo Look: file_[ab]
    Look: file_a file_b
    ```
    
  * Hãy thử ngay tại đây! Chúng tôi đã đặt một loạt các tệp trong `/challenge/files`. Hãy thay đổi thư mục làm việc của bạn thành `/challenge/files` và chạy lệnh `/challenge/run` với một đối số duy nhất sử dụng glob dấu ngoặc vuông (bracket-globs) để khớp với các tệp `file_b`, `file_a`, `file_s`, và `file_h`!

  * <img width="638" height="138" alt="image" src="https://github.com/user-attachments/assets/ec5fc5f2-277f-48c8-8c78-f2ea259a7a78" />

</details>


<details>
  <summary>🏴 <code>Matching paths with []</code></summary>

  * Globbing diễn ra trên cơ sở từng đường dẫn (path basis), vì vậy bạn có thể mở rộng toàn bộ các đường dẫn bằng các đối số sử dụng glob của mình. Ví dụ:

    ```sh
    hacker@dojo:~$ touch file_a
    hacker@dojo:~$ touch file_b
    hacker@dojo:~$ touch file_c
    hacker@dojo:~$ ls
    file_a	file_b	file_c
    hacker@dojo:~$ echo Look: /home/hacker/file_[ab]
    Look: /home/hacker/file_a /home/hacker/file_b
    ```
    
  * Bây giờ đến lượt bạn. Một lần nữa, chúng tôi đã đặt một loạt các tệp trong `/challenge/files`. Bắt đầu từ thư mục nhà (home directory) của bạn, hãy chạy lệnh `/challenge/run` với một đối số duy nhất sử dụng glob dấu ngoặc vuông (bracket-globs) để khớp thành các đường dẫn tuyệt đối dẫn đến các tệp `file_b`, `file_a` , `file_s`, và `file_h`!

  * <img width="695" height="108" alt="image" src="https://github.com/user-attachments/assets/f6682723-3549-456e-a097-1341effbd79b" />

</details>


<details>
  <summary>🏴 <code>Multiple globs</code></summary>

  * Cho đến nay, bạn mới chỉ chỉ định từng glob (mẫu đại diện) một, nhưng bạn có thể làm được nhiều hơn thế! Bash hỗ trợ việc mở rộng nhiều glob trong một từ duy nhất. Ví dụ:

    ```sh
    hacker@dojo:~$ cat /*fl*
    pwn.college{YEAH}
    hacker@dojo:~$
    ```
    
  * Những gì xảy ra ở trên là shell tìm kiếm tất cả các tệp trong thư mục `/` bắt đầu bằng bất cứ thứ gì (bao gồm cả việc không có ký tự nào), sau đó có một chữ `f` và một chữ `l`, và kết thúc bằng bất cứ thứ gì (bao gồm cả `ag`, để tạo thành từ `flag`).

  * Bây giờ đến lượt bạn thử. Chúng tôi đã đặt một vài tệp "vui vẻ", nhưng được đặt tên đa dạng trong thư mục `/challenge/files`. Hãy `cd` (chuyển thư mục) đến đó và chạy lệnh `/challenge/run`, cung cấp một đối số duy nhất: một từ sử dụng glob ngắn gọn (có 3 ký tự trở xuống) với hai glob `*` bên trong nó để bao hàm (khớp với) mọi từ có chứa chữ cái `p`.

  * <img width="823" height="221" alt="image" src="https://github.com/user-attachments/assets/2da9cec5-2443-48dd-b377-7fc77af8cebf" />

</details>


<details>
  <summary>🏴 <code>Mixing globs</code></summary>

  * Bây giờ, hãy cùng kết hợp các cấp độ trước lại với nhau! Chúng tôi đã đặt một vài tệp "vui vẻ", nhưng được đặt tên đa dạng trong thư mục `/challenge/files`. Hãy `cd` (chuyển thư mục) đến đó và, sử dụng kiến thức globbing (khớp mẫu đại diện) mà bạn đã học, hãy viết một glob duy nhất, ngắn gọn (có 6 ký tự trở xuống) mà (khi được truyền dưới dạng một đối số cho `/challenge/run`) sẽ chỉ khớp với các tệp "challenging", "educational", và "pwning"!

  * GỢI Ý: Đảm bảo rằng bạn hãy xem qua tên của các tệp trong `/challenge/files`. Bạn có thấy bất kỳ quy luật/mẫu (patterns) nào có thể giúp bạn tạo ra glob của mình không?

  * <img width="578" height="172" alt="image" src="https://github.com/user-attachments/assets/020283e7-26e3-4ca4-b1f2-a88062b7e830" />

</details>


<details>
  <summary>🏴 <code>Exclusionary globbing</code></summary>

  * Đôi khi, bạn muốn lọc bỏ (filter out) các tệp trong một glob! May mắn thay, `[]` giúp bạn làm chính xác điều này. Nếu ký tự đầu tiên bên trong dấu ngoặc vuông là `!` hoặc (trong các phiên bản bash mới hơn) là `^`, glob sẽ đảo ngược (inverts), và trường hợp dấu ngoặc đó sẽ khớp với các ký tự không được liệt kê. Ví dụ:

    ```sh
    hacker@dojo:~$ touch file_a
    hacker@dojo:~$ touch file_b
    hacker@dojo:~$ touch file_c
    hacker@dojo:~$ ls
    file_a	file_b	file_c
    hacker@dojo:~$ echo Look: file_[!ab]
    Look: file_c
    hacker@dojo:~$ echo Look: file_[^ab]
    Look: file_c
    hacker@dojo:~$ echo Look: file_[ab]
    Look: file_a file_b
    ```
    
  * Được trang bị kiến thức này, hãy tiến tới thư mục `/challenge/files` và chạy lệnh `/challenge/run` với tất cả các tệp không bắt đầu bằng `p`, `w`, hoặc `n`!  

  * LƯU Ý: Ký tự `!` có một ý nghĩa đặc biệt khác trong bash khi nó không phải là ký tự đầu tiên của một glob `[]`, vì vậy hãy ghi nhớ điều đó nếu mọi thứ trở nên khó hiểu (stop making sense)! Ký tự `^` không gặp phải vấn đề này, nhưng nó cũng không tương thích với các shell cũ hơn.

  * <img width="755" height="190" alt="image" src="https://github.com/user-attachments/assets/c6fa17a9-e60a-4733-b306-7688b5299713" />

</details>


<details>
  <summary>🏴 <code>Tab completion</code></summary>

  * Dù có thể rất cám dỗ, việc sử dụng `*` để rút ngắn những gì cần phải gõ trên dòng lệnh có thể dẫn đến những sai sót. Glob (mẫu đại diện) của bạn có thể mở rộng thành các tệp không mong muốn, và bạn có thể không phát hiện ra điều đó cho đến khi lệnh `rm` đã đang chạy! Không một ai là an toàn trước kiểu sai sót này.

  * Một giải pháp thay thế an toàn hơn khi bạn đang cố gắng chỉ định một mục tiêu cụ thể là tab completion (tự động hoàn thành bằng phím tab). Nếu bạn nhấn phím tab trong shell, nó sẽ cố gắng suy đoán xem bạn chuẩn bị gõ gì và tự động hoàn thành nó. Tính năng tự động hoàn thành (Auto-completion) cực kỳ hữu ích, và thử thách này sẽ khám phá việc sử dụng nó trong việc chỉ định các tệp.

  * Thử thách này đã sao chép cờ (flag) vào `/challenge/pwncollege`, và bạn có thể tự do `cat` tệp đó. Nhưng bạn không thể gõ ra tên tệp: chúng tôi đã sử dụng một vài thủ thuật phức tạp (serious trickery) để đảm bảo chắc chắn rằng bạn phải dùng phím tab để hoàn thành nó. Hãy thử xem sao!

    ```sh
    hacker@dojo:~$ ls /challenge
    DESCRIPTION.md  pwncollege
    hacker@dojo:~$ cat /challenge/pwncollege
    cat: /challenge/pwncollege: No such file or directory
    hacker@dojo:~$ cat /challenge/pwn<TAB>
    pwn.college{HECK YEAH}
    hacker@dojo:~$
    ```
    
  * Khi bạn nhấn phím tab đó, tên sẽ được mở rộng ra và bạn sẽ có thể đọc được tệp. Chúc may mắn!

  * <img width="554" height="106" alt="image" src="https://github.com/user-attachments/assets/1ad8529f-7bd2-4a55-ae14-cb5dc3ab3b8b" />

</details>


<details>
  <summary>🏴 <code>Multiple options for tab completion</code></summary>

  * Hãy xem xét tình huống sau:

    ```sh
    hacker@dojo:~$ ls
    flag  flamingo  flowers
    hacker@dojo:~$ cat f<TAB>
    ```
    
  * Có nhiều tùy chọn! Điều gì sẽ xảy ra?

  * Điều xảy ra sẽ khác nhau tùy thuộc vào shell cụ thể và các tùy chọn của nó. Theo mặc định, `bash` sẽ tự động mở rộng cho đến điểm đầu tiên khi có nhiều tùy chọn (trong trường hợp này là `fl`). Khi bạn nhấn phím tab lần thứ hai, nó sẽ in ra những tùy chọn đó. Thay vào đó, các shell và cấu hình khác sẽ lặp/xoay vòng (cycle) qua các tùy chọn.

  * Thử thách này có một thư mục `/challenge/files` với một loạt các tệp bắt đầu bằng `pwncollege`. Hãy tự động hoàn thành bằng phím tab (Tab-complete) từ `/challenge/files/p` hoặc đại loại như vậy, và tìm đường đến lấy cờ (flag)!

  * <img width="749" height="144" alt="image" src="https://github.com/user-attachments/assets/6eb11a68-1e68-4d86-8f43-ce4cf0965f92" />

</details>


<details>
  <summary>🏴 <code>Tab completion on commands</code></summary>

  * Tính năng tự động hoàn thành bằng phím tab (Tab completion) không chỉ dành cho các tệp! Bạn cũng có thể tự động hoàn thành các lệnh bằng phím tab. Cấp độ này có một lệnh bắt đầu bằng `pwncollege`, và nó sẽ cấp cho bạn cờ (flag). Hãy gõ `pwncollege` và nhấn phím tab để tự động hoàn thành nó!

  * LƯU Ý: Bạn có thể tự động hoàn thành bất kỳ lệnh nào, nhưng hãy cẩn thận: việc tự động hoàn thành một cách bất cẩn (callous auto-completes) mà không kiểm tra lại (double-checking) kết quả có thể tàn phá (wreak havoc) shell của bạn nếu bạn vô tình chạy sai các lệnh!

  * <img width="733" height="153" alt="image" src="https://github.com/user-attachments/assets/78047af9-0f8a-470a-a604-0f3b875fc198" />

</details>
