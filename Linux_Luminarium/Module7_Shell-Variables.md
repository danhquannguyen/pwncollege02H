# Shell Variables

* Giao diện dòng lệnh Linux thực ra là một ngôn ngữ lập trình tinh vi mà với nó, bạn có thể viết các chương trình thực thụ! Bởi vì giao diện dòng lệnh được gọi một cách thông tục là một "shell", nên các chương trình được viết bằng ngôn ngữ này được gọi là các "shell scripts" (tập lệnh shell). Khi bạn đang sử dụng dòng lệnh, về cơ bản là bạn đang viết một tập lệnh shell theo từng dòng một!

* Giống như hầu hết các ngôn ngữ lập trình, shell hỗ trợ các biến. Module này sẽ giúp bạn làm quen với việc thiết lập, in ra và sử dụng các biến này!

<details>
  <summary>🏴 <code>Printing Variables</code></summary>

  * Hãy bắt đầu với việc in các biến ra. Chương trình `/challenge/run` sẽ không, và không thể, cung cấp cho bạn lá cờ (flag), nhưng điều đó không sao cả, bởi vì lá cờ đã được đặt vào một biến có tên là "FLAG"! Chỉ cần để shell của bạn in nó ra!

  * Bạn có thể hoàn thành việc này bằng một số cách, nhưng chúng ta sẽ bắt đầu với lệnh `echo`. Lệnh này chỉ đơn giản là in các nội dung ra. Ví dụ:

    ```sh
    hacker@dojo:~$ echo Hello Hackers!
    Hello Hackers!
    ```

  * Bạn cũng có thể in ra các biến bằng lệnh `echo`, bằng cách thêm một dấu `$` vào trước tên biến. Ví dụ, có một biến tên là `PWD`, luôn lưu trữ thư mục làm việc hiện tại của shell hiện hành. Bạn in nó ra như thế này:

    ```sh
    hacker@dojo:~$ echo $PWD
    /home/hacker
    ```

  * Bây giờ đến lượt bạn. Hãy để shell của bạn in ra biến `FLAG` và giải quyết thử thách này!

  * <img width="522" height="98" alt="image" src="https://github.com/user-attachments/assets/12f43589-dd49-4779-91b5-70022224982e" />

</details>


<details>
  <summary>🏴 <code>Setting Variables</code></summary>

  * Đương nhiên, cũng giống như việc đọc các giá trị được lưu trữ trong các biến, bạn có thể ghi các giá trị vào các biến. Điều này được thực hiện, giống như trong nhiều ngôn ngữ khác, bằng cách sử dụng dấu `=`. Để thiết lập biến `VAR` thành giá trị `1337`, bạn sẽ sử dụng:

    ```sh
    hacker@dojo:~$ VAR=1337
    ```

  * Lưu ý rằng **không có khoảng trắng** xung quanh dấu `=`! Nếu bạn đặt các khoảng trắng (ví dụ: `VAR = 1337`), shell sẽ không nhận diện đó là một phép gán biến và thay vào đó, nó sẽ cố gắng chạy lệnh `VAR` (một lệnh không tồn tại).

  * Cũng cần lưu ý rằng thao tác này sử dụng `VAR` chứ không phải `$VAR`: dấu `$` chỉ được thêm vào phía trước để **truy cập** các biến. Trong thuật ngữ của shell, việc thêm dấu $ vào phía trước này kích hoạt một quá trình được gọi là **mở rộng biến** (variable expansion), và thật đáng ngạc nhiên, đây lại là nguồn gốc của rất nhiều lỗ hổng bảo mật tiềm ẩn (nếu bạn quan tâm đến điều đó, hãy thử xem qua dojo Art of the Shell khi bạn đã sử dụng thành thạo dòng lệnh!).

  * Sau khi thiết lập các biến, bạn có thể truy cập chúng bằng các kỹ thuật mà bạn đã học trước đây, chẳng hạn như:

    ```sh
    hacker@dojo:~$ echo $VAR
    1337
    ```

  * Để vượt qua cấp độ (level) này, bạn phải thiết lập biến `PWN` thành giá trị `COLLEGE`. Hãy cẩn thận: cả tên và giá trị của các biến đều phân biệt chữ hoa chữ thường! `PWN` không giống với `pwn` và `COLLEGE` không giống với `College`.

  * <img width="640" height="125" alt="image" src="https://github.com/user-attachments/assets/e3d25437-0cc0-41d4-91c3-b78f801cd40b" />

</details>


<details>
  <summary>🏴 <code>Multi-word Variables</code></summary>

  * Trong cấp độ này, bạn sẽ học về cách trích dẫn (quoting). Các khoảng trắng (spaces) có ý nghĩa đặc biệt trong shell, và có những nơi bạn không thể sử dụng chúng một cách bừa bãi. Hãy nhớ lại cách thiết lập biến của chúng ta:

    ```sh
    hacker@dojo:~$ VAR=1337
    ```

  * Lệnh đó thiết lập biến `VAR` thành `1337`, nhưng điều gì sẽ xảy ra nếu bạn muốn thiết lập nó thành `1337 SAUCE`? Bạn có thể sẽ thử như sau:

    ```sh
    hacker@dojo:~$ VAR=1337 SAUCE
    ```

  * Điều này trông có vẻ hợp lý, nhưng nó không hoạt động, vì những lý do tương tự như việc cần phải không có khoảng trắng xung quanh dấu `=`. Khi shell nhìn thấy một khoảng trắng, nó sẽ kết thúc việc gán biến và diễn giải từ tiếp theo (trong trường hợp này là SAUCE) như một lệnh. Để thiết lập `VAR` thành `1337 SAUCE`, bạn cần phải đặt nó trong dấu ngoặc kép (trích dẫn nó):

    ```sh
    hacker@dojo:~$ VAR="1337 SAUCE"
    ```

  * Ở đây, shell đọc `1337 SAUCE` như một từ khóa (token) duy nhất, và vui vẻ thiết lập giá trị đó cho biến `VAR`. Trong cấp độ này, bạn sẽ cần phải thiết lập biến `PWN` thành `COLLEGE YEAH`. Chúc may mắn!

  * <img width="572" height="99" alt="image" src="https://github.com/user-attachments/assets/d169d556-e145-4136-8387-3eafe9e5f2bf" />

</details>


<details>
  <summary>🏴 <code>Exporting Variables</code></summary>

  * Theo mặc định, các biến mà bạn thiết lập trong một phiên shell là cục bộ đối với tiến trình shell đó. Nghĩa là, các lệnh khác mà bạn chạy sẽ không kế thừa chúng. Bạn có thể thử nghiệm điều này bằng cách đơn giản là gọi một tiến trình shell khác bên trong shell của chính bạn, như thế này:

    ```Bash
    hacker@dojo:~$ VAR=1337
    hacker@dojo:~$ echo "VAR is: $VAR"
    VAR is: 1337
    hacker@dojo:~$ sh
    $ echo "VAR is: $VAR"
    VAR is:
    ```
    
  * Trong đầu ra ở trên, dấu nhắc `$`  là dấu nhắc của `sh`, một bản cài đặt shell tối giản được gọi như một tiến trình con của tiến trình shell chính. Và nó không nhận được biến `VAR`!

  * Tất nhiên, điều này hoàn toàn hợp lý. Các biến shell của bạn có thể chứa dữ liệu nhạy cảm hoặc kỳ lạ, và bạn không muốn nó rò rỉ sang các chương trình khác mà bạn chạy trừ khi nó được chỉ định rõ ràng là nên làm vậy. Làm thế nào để bạn đánh dấu rằng nó nên rò rỉ (nên được truyền đi)? Bạn "xuất" (export) các biến của mình. Khi bạn xuất các biến của mình, chúng được truyền vào các biến môi trường (environment variables) của các tiến trình con. Bạn sẽ gặp lại khái niệm về các biến môi trường trong các thử thách khác, nhưng bạn sẽ quan sát thấy tác dụng của chúng ở đây. Dưới đây là một ví dụ:

    ```Bash
    hacker@dojo:~$ VAR=1337
    hacker@dojo:~$ export VAR
    hacker@dojo:~$ sh
    $ echo "VAR is: $VAR"
    VAR is: 1337
    ```
    
  * Ở đây, shell con đã nhận được giá trị của `VAR` và đã có thể in nó ra! Bạn cũng có thể kết hợp hai dòng đầu tiên đó lại với nhau.

    ```Bash
    hacker@dojo:~$ export VAR=1337
    hacker@dojo:~$ sh
    $ echo "VAR is: $VAR"
    VAR is: 1337
    ```
    
  * Trong thử thách này, bạn phải gọi lệnh `/challenge/run` với biến `PWN` được xuất (exported) và được thiết lập thành giá trị `COLLEGE`, cùng với biến `COLLEGE` được thiết lập thành giá trị `PWN` nhưng không được xuất (ví dụ: không được kế thừa bởi `/challenge/run`). Chúc may mắn!

  * <img width="667" height="314" alt="image" src="https://github.com/user-attachments/assets/cd156ace-bfa7-400f-a867-60570397522a" />

</details>


<details>
  <summary>🏴 <code>Printing Exported Variables</code></summary>

  * Có nhiều cách để truy cập các biến trong bash. `echo` chỉ là một trong số đó, và bây giờ chúng ta sẽ học thêm ít nhất một cách nữa trong thử thách này.

  * Hãy thử lệnh `env`: nó sẽ in ra mọi biến đã được xuất (exported variable) được thiết lập trong shell của bạn, và bạn có thể xem qua đầu ra đó để tìm biến `FLAG`!

  * <img width="934" height="360" alt="image" src="https://github.com/user-attachments/assets/4ad2b0d5-d6ac-4df9-bdd0-b0833ed82429" />

</details>


<details>
  <summary>🏴 <code>Storing Command Output</code></summary>

  * Trong quá trình làm việc với shell, bạn sẽ thường muốn lưu trữ đầu ra (output) của một lệnh nào đó vào một biến. May mắn thay, shell làm cho việc này khá dễ dàng bằng cách sử dụng một thứ gọi là Thay thế Lệnh (Command Substitution)! Hãy quan sát:
  
    ```Bash
    hacker@dojo:~$ FLAG=$(cat /flag)
    hacker@dojo:~$ echo "$FLAG"
    pwn.college{blahblahblah}
    hacker@dojo:~$
    ```
    
  * Tuyệt vời! Bây giờ, bạn hãy thực hành. Hãy đọc đầu ra của lệnh `/challenge/run` trực tiếp vào một biến có tên là `PWN`, và nó sẽ chứa lá cờ (flag)!
  
  * Thông tin bên lề (Trivia): Bạn cũng có thể sử dụng các dấu phẩy ngược (backticks) thay vì `$(): FLAG='cat /flag'` thay vì `FLAG=$(cat /flag)` trong ví dụ trên. Đây là một định dạng cũ hơn và có một số nhược điểm (ví dụ: thử tưởng tượng nếu bạn muốn lồng các phần thay thế lệnh vào nhau. Làm thế nào bạn có thể thực hiện `$(cat $(find / -name flag))` với các dấu phẩy ngược?). Quan điểm chính thức của pwn.college là bạn nên sử dụng `$(blah)`thay vì `'blah'`. (Thay dấu ' = `)

  * <img width="692" height="177" alt="image" src="https://github.com/user-attachments/assets/a9048534-3fd9-4d0f-b65a-65d3c6445c8d" />

</details>


<details>
  <summary>🏴 <code>Reading Input</code></summary>

  * Chúng ta sẽ bắt đầu với việc đọc đầu vào (input) từ người dùng (chính là bạn). Việc này được thực hiện bằng cách sử dụng một lệnh tích hợp (builtin) có tên gọi rất phù hợp là `read`, lệnh này sẽ đọc đầu vào và lưu vào một biến!

  * Dưới đây là một ví dụ sử dụng đối số `-p`, cho phép bạn chỉ định một dấu nhắc văn bản (nếu không có nó, khi đọc tài liệu này bây giờ, bạn sẽ rất khó để phân biệt đâu là đầu vào và đâu là đầu ra trong ví dụ bên dưới):

    ```Bash
    hacker@dojo:~$ read -p "INPUT: " MY_VARIABLE
    INPUT: Hello!
    hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
    You entered: Hello!
    ```
    
  * Hãy ghi nhớ, `read` đọc dữ liệu từ đầu vào tiêu chuẩn (standard input) của bạn! Chữ `Hello!` đầu tiên ở trên là dữ liệu được nhập vào (inputted) chứ không phải được xuất ra (outputted). Hãy thử làm cho điều đó rõ ràng hơn. Ở đây, chúng tôi đã chú thích ở đầu mỗi dòng để chỉ rõ dòng đó đại diện cho ĐẦU VÀO (INPUT) từ người dùng hay ĐẦU RA (OUTPUT) hiển thị cho người dùng:

    ```Bash
     INPUT: hacker@dojo:~$ echo $MY_VARIABLE
    OUTPUT:
     INPUT: hacker@dojo:~$ read MY_VARIABLE
     INPUT: Hello!
     INPUT: hacker@dojo:~$ echo "You entered: $MY_VARIABLE"
    OUTPUT: You entered: Hello!
    ```
    
  * Trong thử thách này, nhiệm vụ của bạn là sử dụng lệnh `read` để thiết lập biến `PWN` thành giá trị `COLLEGE`. Chúc may mắn!

  * <img width="655" height="145" alt="image" src="https://github.com/user-attachments/assets/209bba1d-89b8-4d43-a10c-e1bd319a9edd" />

</details>


<details>
  <summary>🏴 <code>Reading Files</code></summary>

  * Thường thì, khi người dùng shell muốn đọc một tệp vào một biến môi trường (environment variable), họ sẽ làm những việc như sau:

    ```Bash
    hacker@dojo:~$ echo "test" > some_file
    hacker@dojo:~$ VAR=$(cat some_file)
    hacker@dojo:~$ echo $VAR
    test
    ```

  * Cách này có hiệu quả, nhưng nó đại diện cho thứ mà những hacker khó tính gọi là "Sử dụng Cat Vô Ích" (Useless Use of Cat). Nghĩa là, việc chạy nguyên cả một chương trình khác chỉ để đọc tệp là một sự lãng phí. Hóa ra là bạn chỉ cần sử dụng sức mạnh của shell!

  * Trước đây, bạn đã đọc đầu vào của người dùng vào một biến. Trước đây bạn cũng đã từng chuyển hướng (redirect) các tệp vào đầu vào của lệnh! Kết hợp chúng lại với nhau, và bạn có thể đọc các tệp bằng shell.

    ```Bash
    hacker@dojo:~$ echo "test" > some_file
    hacker@dojo:~$ read VAR < some_file
    hacker@dojo:~$ echo $VAR
    test
    ```
    
  * Chuyện gì đã xảy ra ở đó? Ví dụ này chuyển hướng `some_file` vào đầu vào tiêu chuẩn (standard input) của `read`, và do đó khi `read` đọc dữ liệu ghi vào `VAR`, nó đã đọc từ tệp đó! Bây giờ, hãy sử dụng cách đó để đọc tệp `/challenge/read_me` vào biến môi trường `PWN`, và chúng tôi sẽ đưa cho bạn lá cờ (flag)! Tệp `/challenge/read_me` sẽ liên tục thay đổi, vì vậy bạn sẽ cần đọc nó trực tiếp vào biến PWN chỉ bằng một lệnh duy nhất!

  * <img width="669" height="121" alt="image" src="https://github.com/user-attachments/assets/49efe04c-b38d-4d2b-bc88-be713ef288e8" />

</details>
