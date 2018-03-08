## 5. Kiểm thử
![Kiểm thử](/images/testing.png)
* Thêm môi trường chế độ `kiểm thử` nếu cần thiết.

    _Tại sao:_
    >Trong khi đôi lúc việc testing end to end trong chế độ `sản xuất` có vẻ là đủ, tuy nhiên cũng có vài ngoài lệ: 1 ví dụ như là khi bạn có thể không muốn bật các thống tin phân tích trong chế độ `sản phẩm` và bôi ra trang dashboard của ai đó những dữ liệu test. Một ví dụ khác là API của bạn có thể có những mức giới hạn trong `sản xuất` và phần test của bạn gọi 1 lượng các request.

* Đặt các file kiểm thử của bạn cạnh các module test sử dụng quy ước đặt tên `*.test.js` hoặc `.*spec,js`, như `moduleName.spec.js`.

    _Tại sao:_
    > Bạn sẽ không muốn phải lùng xục cấu trúc thư mục để tìm 1 unit test đâu[đọc thêm...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc) 
    

* Đặt các file kiểm thử bổ sụng của bạn vào trong các thư mục kiểm thử riêng biệt để tránh nhầm lẫn

    _Tại sao:_
    > Một vài file kiểm thử không liên quan rõ ràng đến bất ký các file thực hiện cụ thể nào. Bạn cần phải đặt chúng tron các thử mục hay được các lập trình viên khác tìm kiếm: thư mục `__test__`. Cái tên `__test__` cục khá là tiêu chuẩn và được lựa chọn bởi hầu hết các framework kiểm thử Javascript.

* Viết các đoạn code test được, tránh ảnh hưởng bên ngoài, tách các ảnh hưởng bên ngoài, viết các hàm thuần khiết.

    _Tại sao:_
    > Bạn muốn kiểm tra logic kinh doanh như các thành phần riêng biệt. Bạn cần phải hạn chế nhưng quy trình ngẫu nhiên và không xác định trong sự tin cậy của code của bạn [đọc thêm...](https://medium.com/javascript-scene/tdd-the-rite-way-53c9b46f45e3)
    
    > Một hàm thuần khiết là một hàm luôn luôn trả về các giá trị giống nhau với cùng một đầu vào. Ngược lại, một hàm không thuần khiết là hàm mà có thể có những ảnh hướng bên ngoài hay phụ thuộc vào các điểu kiện từ bên ngoài để đưa ra kết quả. Điều này sẽ khiến nó khó dự đoán hơn.[đọc thêm...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)

* Sử dụng bộ kiểm tra cố định

    _Tại sao:_
    > Đôi khi bạn có thể sẽ cần những bộ kiểm tra cố định. Nó mang lại độ tin cậy chắc chắn cho code của bạn. [đọc thêm...](https://medium.freecodecamp.org/why-use-static-types-in-javascript-part-1-8382da1e0adb)


* Chạy các kiểm thử cục bộ trước khi tạo các pull request cho `develop`.

    _Tại sao:_
    > Bạn sẽ không muốn là người gây ra sự thất bại cho cái nhánh kiến trúc sẵn sàng sản xuất đâu. Chạy các kiểm thủ sau các lần `rebase` của bạn và trước khi đẩy các nhánh tính năng của bạn lên remote repository.

* Làm tài liệu cho các kiểm thử của bạn bao gồm các hướng dẫn cho các phần liên quan trong file `README.md` của bạn.

    _Tại sao:_
    -> Đây là ghi chú viết tay bạn dành cho các lập trình viên khác hoặc các chuyên gia DevOps hoặc QA hoặc bất  kỳ ai may mắn làm việc trên code của bạn.

<a name="structure-and-naming"></a>
## 6. Cấu trúc và đặt tên 

![Cấu trúc và đặt tên](/images/folder-tree.png) 

* Sắp xếp các file xung quanh các tính năng, các trang và các thành phần của sản phẩm, chứ không phải các vai trò. Mặt khác, đặt các file test bên cạnh các phần thực hiện. 

  

  

    **Tệ** 

  

    ``` 

    . 

    ├── controllers 

    |   ├── product.js 

    |   └── user.js 

    ├── models 

    |   ├── product.js 

    |   └── user.js 

    ``` 

  

    **Tốt** 

  

    ``` 

    . 

    ├── product 

    |   ├── index.js 

    |   ├── product.js 

    |   └── product.test.js 

    ├── user 

    |   ├── index.js 

    |   ├── user.js 

    |   └── user.test.js 

    ``` 

  

    _Tại sao:_ 

   

    > Thay vì 1 danh sách dài các file, bạn có thể tạo các module nhỏ đóng gói 1 nhiệm vụ nào đó, bao gồm phần test, ... của nó. Như vậy nó sẽ dễ dàng điều hướng hơn rất nhiều và bạn có thể tìm thấy mọi thứ trong thoáng chốc. 

  

* Đặt các file test bổ sung vào thư mục test riêng biệt để tránh nhầm lẫn. 

    _Tại sao:_ 

    > Vì nó là 1 cách tiết kiệm thời gian cho các lập trình viên khác cũng như các chuyên gia DevOps trong team của bạn. 

  

* Sử dụng 1 thư mục `./config` và không sử dụng các file cấu hình khác nhau cho các môi trường khác nhau. 

  

    _Tại sao:_ 

    > Khi bạn thay đổi file cấu hình cho các mục đích khác nhau (cơ sở dữ liệu, API, vân vân ); đặt chúng trong các thư mục với cái tên dễ nhân biết như `config` sẽ hợp lý hơn. Hãy nhớ rằng không tạo các file cấu hình khác nhau cho các môi trường khác nhau. Nó sẽ khó mở rộng, vì ứng dụng sẽ có nhiều triển khai hơn, cần thiết có tên của môi trường mới. 

    Các giá trị được sử dụng trong file cấu hình nên được cung cấp bởi các biến môi trường [đọc thêm...](https://medium.com/@fedorHK/no-config-b3f1171eecd5) 

     

  

* Đặt các script của bạn trong thư mục `./script`. Nó sẽ bao gồm các `bash` và `node` scripts. 

  

    _Tại sao:_n 

    ->Điều này giống như là bạn có thể có được với hơn 1 script, thiết kế sản xuất, thiết kế phát triển, bộ sinh cơ sở dữ liệu, đồng bộ hóa cơ sở dữ liệu, vân vân. 

     

  

* Đặt các thiết kế đầu ra của bạn trong thư mục `./build`. Thêm `build/` vào `.gitignore`. 

  

    _Tại sao:_ 

    >Đặt cho nó bất cứ cái tên nào bạn thích, `dist` nghe cũng ổn đấy. Nhưng hay chắc rằng nó phù hợp với nhóm của bạn. Những gì bạn thu được ở đây là tạo ra (đóng gói, biên dịch, chuyển đổi) hoặc di chuyển chúng tới đó. Những gì bạn có thể tạo ra, người trong nhóm của bạn cũng có thể tạo ra, vì vậy khôngcó lý nào lại commit chúng lên remote reposity của bạn cả. Trừ khi bạn thực sự muốn thế. 

  

<a name="code-style"></a> 

## 7. Phong cách lập trình 

  

![Phong cách lập trình](/images/code-style.png) 

  

<a name="code-style-check"></a> 

### 7.1 Một vài hướng dẫn phong cách lập trình

  

* Sử dụng cú pháp JavaScript (hiện đại) mức 2 hoặc cao hơn cho các dự án mới. Với các dự án cũ, duy trì cũ pháp hiện tại trừ khi bạn dự định cải tiến dự án của mình. 

  

    _Tại sao:_ 

    > Điều này phụ thuộc vào bạn. Chúng tôi sử dụng các bộ chuyển đổi để sử dụng các thế mạnh của cú pháp mới. Mức 2 thì sẽ là sự lựa chọn cuối cùng với những chỉnh sửa nhỏ.

  

* Thêm các phần kiểm tra phong cách lập trình vào quá trình kiến trúc của bạn.

  

    _Tại sao:_ 

    > Thay đổi kiến trúc của bạn là 1 trong những cách để áp dụng phong cách lập trình. Nó sẽ làm bản không cảm thấy nó bớt quan trọng đi. Áp dụng nó cho cả code bên phía client cũng như phía server. [đọc thêm...](https://www.robinwieruch.de/react-eslint-webpack-babel/) 

  

* Sử dụng [ESLint - Pluggable JavaScript linter](http://eslint.org/) để áp dụng phong cách lập trình.

  

    _Tại sao:_ 

    > Đơn giản là do chúng tôi thíchích `eslint` hơn, còn bạn thì không cần phải như vậy. Nó hỗ trợ nhiều luật hơn, có khả năng cấu hình lại các luật và khả năng thêm các luật tùy chỉnh nữa.

  

* Chúng tôi sử dụng [hướng dẫn phong cách JavaScript Airbnb](https://github.com/airbnb/javascript) cho JavaScipt, [Đọc thêm](https://www.gitbook.com/book/duk/airbnb-javascript-guidelines/details).  Sử dụng hướng dẫn phong cách javascript phù hợp yêu cầu của dự án hoặc nhóm của bạn. 

  

* Chúng tôi sử dụng [Phong cách kiểm tra luật dạng Flow cho ESLint](https://github.com/gajus/eslint-plugin-flowtype) khi sử dụng [FlowType](https://flow.org/). 

  

    _Tại sao:_ 

    > Flow cung cấp một vài cú pháp mà cần tuân theo phong cách lập trình cụ thể và cần được kiểm tra

  

* Sử dụng `.eslintignore` để loại trù các file hay thư mục khỏi việc kiểm tra phong cách lập trình. 

  

    _Tại sao:_ 


    > Bạn không cần phải làm bẩn code của bạn với những dòng comment `eslint-disable` khi bạn cần loại các file ra khỏi việc kiểm tra phong cách.

  

* Loại bỏ bất cứ comment tắt `eslint` của bạn trước khi tạo các Pull Request.

  

    _Tại sao:_ 

    > Sẽ rất bình thường khi bạn tắt các kiểm tra phong cách trong khi làm việc trên 1 đoạn code để tập trung hơn vào logic. Hãy nhớ loại các comment `eslint-disable` và tuân theo các luật.

  

* Phụ thuộc vào kích thước của công việc mà sử dụng các comment `//TODO:` hoặc mở thẻ.

  

    _Tại sao:_ 

    > Vì sau đó bạn có thể nhắc nhở bản thân hoặc người khác về các công việc nhỏ ( như là sắp xếp lại các hàm hoặc cập nhật các comment). Với các công việc lớn hơn sử dụng `//TODO(#3456)` được thực hiện bởi các luật và con số là 1 thẻ mở.

  

* Luôn luôn comment liên quan những thay đổi của code. Loại bỏ các đoạn code được comment.

     

    _Tại sao:_ 

    > Code của bạn nên càng dễ đọc càng tốt, bạn nên thoát ra khỏi những thứ gây xao nhãng. Nếu bạn sắp xếp lại các hàm, đừng chỉ comment những cái cũ, hãy xóa chúng đi. 

  

* Tránh những comment, log hay cách đặt tên vui vẻ hay không liên quan.

  

    _Tại sao:_ 

    > Khi mà cái quy trình kiến trúc của bạn có thể(nên) tránh xa khỏi chúng, đôi khi mã nguồn của bạn có thể được bàn giao cho công ty/ khách hàng khác mà họ có thể không cười nhạo chúng.

  

* Đặt tên  dễ tìm kiếm với nhưng ý nghĩa phân biệt tránh tên ngắn. Với các hàm sử dụng các tên dài, mang nghĩa mô tả. Tên của các hàm nên là 1 động từ hoặc cụm động từ, và nó cần liên quan đến chủ đích của hàm đó.

  

      _Tại sao:_ 

    > Nó làm cho việc đọc mã nguồn tự nhiên hơn.

  

* Tổ chức các hàm của bạn trong 1 file dựa theo luật step-down. Những hàm ở mức cao hơn nên ở trên cùng và mức thấp thì ở bên dưới.

  

    _Tại sao:_ 

    > Nó làm cho việc đọc mã nguồn tự nhiên hơn.

  

<a name="enforcing-code-style-standards"></a> 

### 7.2 Áp dụng các chuẩn phong cách lập trình 

  
* Sử dụng 1 file [.editorconfig](http://editorconfig.org/) để giúp các lập trình viên định nghĩa và bảo trì phong cách lập trình thích hợp giữa các trình soạn thảo và các IDE khác nhau trên dự án

  

    _Tại sao:_ 
    > Dự án EditorConfig bao gồm các định dạng file để định nghĩa các phong cách lập trình và 1 tập các plugin của các trình soạn thảo văn bản cho phép các trình soạn thảo đọc các định dạng file và tuân theo để định nghĩa các phong cách, Các file EditorConfig cũng rất dễ đọc và nó cũng tương tác hiệu quả với các hệ thống quản lý phiên bản.

  

* Để các trình soạn thảo thông báo cho bạn về các lỗi phong  cách lập trình. Sử dụng [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier) và [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) với các cấu hình ESLint hiện tại của bạn. [đọc thêm...](https://github.com/prettier/eslint-config-prettier#installation) 

  

* Xem xét sử dụng Git hooks.

  

    _Tại sao:_ 


    > Git hooks sẽ tăng mạnh năng suất của các lập trình viên. Chúng ta có thể tạo các thay đổi, commit và push lên môi trường staging hoặc production mà không sợ phá vỡ kiến trúc. [đọc thêm...](http://githooks.com/) 

  

* Sử dụng Prettier với precommit hook

  

    _Tại sao:_ 

    > Vì bản thân `prettier` nó rất mạnh, nên việc đơn giản chạy nó như nhưng công việc npm độc lập mỗi lần để chỉnh sửa code sẽ không năng suất lắm. Đây cũng là lúc mà `lint-staged` ( và `husky`) trở nên quan trọng. Đọc thêm về cấu hình `lint-staged` [ở đây](https://github.com/okonet/lint-staged#configuration)
 và cấu hình `husky` [ở đây](https://github.com/typicode/husky).
  

  

<a name="logging"></a> 

## 8. Ghi log 

  

![Ghi log](/images/logging.png) 

  

* Tránh các in ra log trong môi trường sản xuất bên phía client

  

    _Tại sao:_ 

    > Mặc dù quá trình xây dựng của bạn có thể (nên) thoát khỏi chúng, hãy chắc rằng bộ kiểm tra phong cách lập trình của bạn cảnh báo bạn về việc in log ra bên ngoài.

  

* Tạo ra các log production dễ đọc. Lý tưởng nhất là sử dụng thửz viện ghi log trong chế độ production ( ví dụ như [winston](https://github.com/winstonjs/winston) hoặc 
[node-bunyan](https://github.com/trentm/node-bunyan)).


  

    _Tại sao:_ 

    > Nó khiến bạn việc xử lý sự cố của bạn trở nên dễ dàng hơn với màu sắc, dấu thời gian, và các log trong file được thêm vào trong console hoặc thậm chí là ghi log vào file hàng ngày. [đọc thêm ..](https://blog.risingstack.com/node-js-logging-tutorial/) 

  

  

<a name="api"></a>   
