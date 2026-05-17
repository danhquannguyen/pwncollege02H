# Digesting Documentation

* Module này sẽ dạy cho bạn một trong những kỹ năng Linux quan trọng nhất: tìm kiếm sự trợ giúp về cách sử dụng các chương trình. Kỹ năng này sẽ phục vụ bạn rất tốt trong cuộc hành trình của bạn. Hãy đi sâu vào khám phá ngay bên dưới!

<details>
  <summary>🏴 <code>Learning From Documentation</code></summary>

  * Nhu cầu điển hình mà bạn sẽ có đối với tài liệu (documentation) chỉ là để tìm ra cách sử dụng tất cả những chương trình chết tiệt này (dang programs), và một trường hợp cụ thể của điều đó là tìm ra những đối số (arguments) nào cần chỉ định trên dòng lệnh. Module này sẽ chủ yếu đi sâu vào khái niệm đó, như một cách đại diện (proxy) cho việc tìm hiểu cách sử dụng các chương trình nói chung. Xuyên suốt phần còn lại của module, bạn sẽ đi qua nhiều cách khác nhau để yêu cầu môi trường trợ giúp về các chương trình, nhưng trước tiên, chúng ta sẽ đi sâu vào khái niệm đọc tài liệu.

  * Việc sử dụng chính xác các chương trình phụ thuộc phần lớn vào việc chỉ định đúng các đối số cho chúng. Hãy nhớ lại `-a` của lệnh `ls -a` trong thử thách _hidden files_ (các tệp ẩn) của module _Basic Commands_ (Các lệnh cơ bản): `-a` đó là một đối số báo cho lệnh `ls` biết để liệt kê ra các tệp ẩn cũng như các tệp không bị ẩn. Bởi vì chúng ta đã muốn liệt kê ra các tệp ẩn, việc gọi lệnh `ls` với đối số `-a` là cách sử dụng chính xác trong kịch bản của chúng ta.

  * Chương trình cho thử thách này là `/challenge/challenge`, và bạn sẽ cần phải gọi nó một cách chính xác để nó cấp cho bạn cờ (flag). Hãy giả vờ rằng đây là tài liệu của nó:

    * Chào mừng bạn đến với tài liệu hướng dẫn cho `/challenge/challenge`! Để chạy chương trình này một cách chính xác, bạn sẽ cần phải truyền (pass) cho nó đối số `--giveflag`. Chúc may mắn!

  * Với kiến thức đó, hãy đi lấy cờ đi nào!

  * <img width="627" height="134" alt="image" src="https://github.com/user-attachments/assets/0b057d83-fb10-420f-a4b1-ad1bc7f8a3da" />

</details>


<details>
  <summary>🏴 <code>Learning Complex Usage</code></summary>

  * Mặc dù việc sử dụng hầu hết các lệnh là khá đơn giản (straightforward), cách sử dụng của một số lệnh có thể trở nên khá phức tạp. Ví dụ, các đối số cho các lệnh như `sed` và `awk`, những thứ mà chúng ta chắc chắn sẽ không đi sâu vào lúc này, là toàn bộ các chương trình được viết bằng một ngôn ngữ lập trình bí truyền (esoteric)! Nằm đâu đó trên dải quang phổ (spectrum) giữa lệnh `cd` và `awk` là các lệnh nhận các đối số cho chính các đối số của chúng...

  * Điều này nghe có vẻ điên rồ, nhưng bạn đã từng bắt gặp điều này ở cấp độ `find` trong module Các lệnh cơ bản (Basic Commands). Lệnh find có một đối số `-name`, và bản thân đối số `-name` đó lại nhận một đối số chỉ định tên cần tìm kiếm. Rất nhiều lệnh khác cũng tương tự như vậy (analogous).

  * Dưới đây là tài liệu của cấp độ này dành cho `/challenge/challenge`:

    * Chào mừng bạn đến với tài liệu hướng dẫn cho `/challenge/challenge`! Chương trình này cho phép bạn in các tệp tùy ý (arbitrary files) ra terminal, khi được cung cấp đối số `--printfile`. Đối số cho đối số `--printfile` là đường dẫn của cờ (flag) cần đọc. Ví dụ, `/challenge/challenge --printfile /challenge/DESCRIPTION.md` sẽ in ra phần mô tả của cấp độ này!

  * Với tài liệu đó, hãy đi lấy cờ đi nào!

  * <img width="885" height="160" alt="image" src="https://github.com/user-attachments/assets/4a94caea-dbc6-45ff-a242-bba57e7e69fa" />

</details>


<details>
  <summary>🏴 <code>Reading Manuals</code></summary>

  * Cấp độ này giới thiệu lệnh `man`. `man` là viết tắt của `manual` (sổ tay hướng dẫn), và sẽ hiển thị (nếu có) hướng dẫn sử dụng của lệnh mà bạn truyền vào như một đối số. Ví dụ, giả sử chúng ta muốn tìm hiểu về lệnh `yes` (đúng vậy, đây là một lệnh có thật):

    ```sh
    hacker@dojo:~$ man yes
    ```

  * Điều này sẽ hiển thị trang hướng dẫn (manpage) cho lệnh yes, nó sẽ trông giống như thế này:

    ```sh
    YES(1)                           User Commands                          YES(1)

    NAME (TÊN)
           yes - output a string repeatedly until killed (xuất ra một chuỗi lặp đi lặp lại cho đến khi bị buộc dừng)

    SYNOPSIS (CÚ PHÁP)
           yes [STRING]... (yes [CHUỖI]...)
           yes OPTION (yes TÙY_CHỌN)

    DESCRIPTION (MÔ TẢ)
           Repeatedly output a line with all specified STRING(s), or 'y'. (Lặp đi lặp lại việc xuất ra một dòng với tất cả các CHUỖI được chỉ định, hoặc 'y'.)

           --help display this help and exit (hiển thị trợ giúp này và thoát)

           --version
                  output version information and exit (xuất thông tin phiên bản và thoát)

    AUTHOR (TÁC GIẢ)
           Written by David MacKenzie. (Viết bởi David MacKenzie.)

    REPORTING BUGS (BÁO CÁO LỖI)
           GNU coreutils online help: <https://www.gnu.org/software/coreutils/>
           Report any translation bugs to <https://translationproject.org/team/>

    COPYRIGHT (BẢN QUYỀN)
           Copyright  ©  2020  Free Software Foundation, Inc.  License GPLv3+: GNU
           GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
           This is free software: you are free  to  change  and  redistribute  it. (Đây là phần mềm tự do: bạn được tự do thay đổi và phân phối lại nó.)
           There is NO WARRANTY, to the extent permitted by law. (KHÔNG CÓ BẢO HÀNH, trong phạm vi pháp luật cho phép.)

    SEE ALSO (XEM THÊM)
           Full documentation <https://www.gnu.org/software/coreutils/yes>
           or available locally via: info '(coreutils) yes invocation'

    GNU coreutils 8.32               February 2022                          YES(1)
    ```
    
  * Các phần quan trọng là:

    ```
    shNAME(1)                           CATEGORY                          NAME(1)

    NAME (TÊN)
	          This gives the name (and short description) of the command or
	     concept discussed by the page.
            (Phần này đưa ra tên (và mô tả ngắn gọn) của lệnh hoặc khái niệm được thảo luận trong trang.)

    SYNOPSIS (CÚ PHÁP/TÓM TẮT)
	          This gives a short usage synopsis. These synopses have a standard
	          format. Typically, each line is a different valid invocation of the
	          command, and the lines can be read as:
             (Phần này đưa ra một tóm tắt ngắn gọn về cách sử dụng. Những cú pháp này có một định dạng tiêu chuẩn. Thông thường, mỗi dòng là một cách gọi lệnh hợp lệ khác nhau, và các dòng có thể được đọc như sau:)

	          COMMAND [OPTIONAL_ARGUMENT] SINGLE_MANDATORY_ARGUMENT
             (LỆNH [ĐỐI_SỐ_TÙY_CHỌN] MỘT_ĐỐI_SỐ_BẮT_BUỘC)

	          COMMAND [OPTIONAL_ARGUMENT] MULTIPLE_ARGUMENTS...
             (LỆNH [ĐỐI_SỐ_TÙY_CHỌN] NHIỀU_ĐỐI_SỐ...)

    DESCRIPTION (MÔ TẢ)
  	        Details of the command or concept, with detailed descriptions
	  of the various options.
            (Chi tiết về lệnh hoặc khái niệm, cùng với các mô tả chi tiết về các tùy chọn khác nhau.)

    SEE ALSO (XEM THÊM)
	          Other man pages or online resources that might be useful.
            (Các trang man khác hoặc các tài nguyên trực tuyến có thể hữu ích.)

    COLLECTION                        DATE                          NAME(1)
    ```
    

  * Bạn có thể cuộn quanh trang manpage bằng các phím mũi tên và PgUp/PgDn (Page Up/Page Down). Khi bạn đọc xong manpage, bạn có thể nhấn `q` để thoát (quit).

  * Các manpage được lưu trữ trong một cơ sở dữ liệu tập trung. Nếu bạn tò mò, cơ sở dữ liệu này nằm trong thư mục `/usr/share/man`, nhưng bạn không bao giờ cần phải tương tác trực tiếp với nó: bạn chỉ cần truy vấn nó bằng lệnh `man`. Các đối số cho lệnh `man` không phải là đường dẫn tệp, mà chỉ là tên của chính các mục nhập đó (ví dụ: bạn chạy `man yes` để tra cứu manpage của lệnh `yes`, thay vì `man /usr/bin/yes`, đây sẽ là đường dẫn thực tế đến chương trình `yes` nhưng sẽ dẫn đến việc lệnh `man` hiển thị ra một mớ rác - garbage).

  * Thử thách trong cấp độ này có một tùy chọn bí mật mà khi bạn sử dụng nó, sẽ khiến thử thách in ra cờ (flag). Bạn phải tìm hiểu tùy chọn này thông qua trang man của `challenge`!

  * <img width="990" height="783" alt="image" src="https://github.com/user-attachments/assets/e350639c-7f00-41da-a2a1-ccd1ce8a21e4" />

</details>


<details>
  <summary>🏴 <code>Searching Manuals</code></summary>

  * Bạn có thể cuộn các trang man (man pages) bằng các phím mũi tên (và phím PgUp/PgDn) và tìm kiếm bằng phím `/`. Sau khi tìm kiếm, bạn có thể nhấn phím `n` để đi đến kết quả tiếp theo và `N` để đi đến kết quả trước đó. Thay vì `/`, bạn có thể sử dụng `?` để tìm kiếm ngược từ dưới lên (search backwards)!

  * Hãy tìm tùy chọn sẽ cấp cho bạn cờ (flag) bằng cách đọc trang man của `challenge`.

  * <img width="715" height="119" alt="image" src="https://github.com/user-attachments/assets/383bdb31-e195-4cbe-b2bb-e620f9992c1e" />

</details>


<details>
  <summary>🏴 <code>Searching For Manuals</code></summary>

  * Cấp độ này khá lắt léo (tricky): nó giấu trang hướng dẫn (manpage) của thử thách bằng cách đặt tên ngẫu nhiên cho nó. May mắn thay, tất cả các trang manpage đều được tập hợp trong một cơ sở dữ liệu có thể tìm kiếm được, vì vậy bạn sẽ có thể tìm kiếm trong cơ sở dữ liệu man page để tìm ra trang manpage của thử thách đang bị ẩn! Để tìm ra cách tìm kiếm đúng trang manpage, hãy đọc trang manpage của lệnh `man` bằng cách chạy: `man man`!

    * GỢI Ý 1: `man man` hướng dẫn bạn cách sử dụng nâng cao của chính lệnh `man`, và bạn phải sử dụng kiến thức này để tìm ra cách tìm kiếm trang manpage bị ẩn, trang này sẽ cho bạn biết cách sử dụng `/challenge/challenge`
    * GỢI Ý 2: mặc dù trang manpage được đặt tên ngẫu nhiên, thực chất bạn vẫn sử dụng chương trình `/challenge/challenge` để lấy cờ (flag)!

  * <img width="1039" height="1217" alt="image" src="https://github.com/user-attachments/assets/44508b99-d6f5-4ae6-b3d8-38cd40c5961d" />

</details>


<details>
  <summary>🏴 <code>Helpful Programs</code></summary>

  * Một số chương trình không có trang hướng dẫn (man page), nhưng có thể cho bạn biết cách chạy chúng nếu được gọi (invoked) với một đối số đặc biệt. Thông thường, đối số này là `--help`, nhưng nó cũng thường có thể là `-h` hoặc, trong những trường hợp hiếm hoi, là `-?`, `help`, hoặc các giá trị kỳ lạ (esoteric) khác như `/?` (mặc dù giá trị sau cùng đó thường được bắt gặp thường xuyên hơn trên Windows).

  * Trong cấp độ này, bạn sẽ thực hành việc đọc tài liệu của một chương trình bằng `--help`. Hãy thử xem sao!

  * <img width="913" height="377" alt="image" src="https://github.com/user-attachments/assets/f2cb0c0c-38e1-47ef-81d6-53c0d9f7d115" />

</details>

<details>
  <summary>🏴 <code>Help for Builtins</code></summary>

  * Một số lệnh, thay vì là các chương trình có các trang hướng dẫn (man pages) và các tùy chọn trợ giúp, lại được tích hợp sẵn vào chính shell. Những lệnh này được gọi là các lệnh tích hợp (builtins). Các lệnh tích hợp được gọi (invoked) giống hệt như các lệnh thông thường, nhưng shell xử lý chúng ở bên trong thay vì khởi chạy các chương trình khác. Bạn có thể lấy được danh sách các lệnh tích hợp của shell bằng cách chạy lệnh tích hợp `help`, giống như thế này:

    ```sh
    hacker@dojo:~$ help
    ```

  * Bạn có thể nhận trợ giúp về một lệnh cụ thể bằng cách truyền nó cho lệnh tích hợp `help`. Hãy cùng xem xét một lệnh tích hợp mà chúng ta đã sử dụng trước đó, `cd`!

    ```sh
    hacker@dojo:~$ help cd
    cd: cd [-L|[-P [-e]] [-@]] [dir]
        Change the shell working directory. (Thay đổi thư mục làm việc của shell.)
    
        Change the current directory to DIR.  The default DIR is the value of the
        HOME shell variable. (Thay đổi thư mục hiện tại thành DIR. DIR mặc định là giá trị của biến shell HOME.)
    ...
    ```

  * Quả là những thông tin hữu ích! Trong thử thách này, chúng ta sẽ thực hành sử dụng `help` để tra cứu trợ giúp cho các lệnh tích hợp. Lệnh `challenge` của thử thách này là một lệnh tích hợp của shell, chứ không phải là một chương trình. Giống như trước đây, bạn cần tra cứu trợ giúp của nó để tìm ra giá trị bí mật cần truyền cho nó!

  * <img width="634" height="335" alt="image" src="https://github.com/user-attachments/assets/dc37b7c6-39ba-447a-965b-6c9c997cc1f2" />

</details>
