# Cài đặt node.js trên Windows
> node.js cài đặt rất dễ dàng trên môi trường linux như Ubuntu. Tuy nhiên khi cài trên Windows thì lại rất phiền phức. Bài viết này ghi lại kinh nghiệm của tác giả khi cài đặt node.js trên Windows 10.
Hướng dẫn này cài đặt bản node.js mới nhất vào thời điểm hiện nay (4.1.1) cùng bản npm mới nhất 3.3.4

### Mục lục
* [Cài đặt node.js và npm](#part-1)
* [Cài đặt môi trường cho Windows](#part-2)
  - [Python 2.7.0](#python-2.7.0)
  - [Visual Studio 2013](#vs2013)
  - [Các cập nhật](#capnhat)

## Cài đặt node.js và npm
Cài đặt node.js trên Windows như cài đặt các phần mềm thông thường khác trên Windows.
  1. **node.js** Download node.js từ trang [web](https://nodejs.org/en/) chính thức và cài đặt như bình thường.
    * Có nhiều lời khuyên rằng nên lựa chọn cài nodejs trên 1 thư mục khác với thư mục ngầm định của Windows. Ví dụ: C:\nodejs. Nguyên nhân do vấn đề quyền thư mục, có thể ảnh hưởng đến việc cài đặt các global packages sau này.
    * Lựa chọn ngầm định sẽ cài đặt cả npm là chương trình quản lý phần mềm của nodejs. Module npm này nằm trong thư mục node_modules tại thư mục cài đặt nodejs.
  2. **npm.js** Vào thời điểm của bài viết này, npm đang đưa ra bản beta, nên bản npm cài đặt theo nodejs là bản v2.latest.
    * Sử dụng lệnh sau để cài bản npm mới nhất `npm install -g npm@latest`
    Sự khác biệt giữa bản 2 và bản 3 của npm nằm ở cách npm quản lý các module phụ thuộc.
    * npm phân biệt global module và app module, vì vậy rất nên định nghĩa 1 thư mục rõ ràng để npm cài đặt các global module và thường nên lựa chọn 1 thư mục ít bị phụ thuộc vào quyền.
    Dùng `npm config get` để có được danh sách các thiết lập của npm
    Dùng `npm config set prefix đường\dẫn\` để định nghĩa thư mục lưu giữ các module global
    Đừng quên vào Windows, Advanced Settings, Đặt biến đường dẫn trỏ tới thư mục này

## Cài đặt môi trường cho Windows ##
Đến đây thì cũng chưa có gì là phức tạp, tuy nhiên khi bắt đầu xây dựng ứng dụng và sử dụng các module hỗ trợ cần thiết, nodejs sử dụng node-gyp nôm na để built các ứng dụng từ file nguồn. Trong môi trường linux, chỉ cẩn cài đặt bộ essential-build là đủ. Trong Windows phức tạp hơn và hay gặp lỗi.
  1. Python 2.7.0: nodejs cho đến lúc này sử dụng python 2.7 chứ không phải 3.x. Vậy hãy chắc chắn:
    * python 2.7 có cài đặt trên máy
    * Cài đặt đường dẫn môi trường cho python 2.7
    * Dùng `npm config set python \đường\dẫn\python\2.7` để đảm bảo node.js sử dụng đúng phiên bản python.
  2. Visual Studio 2013
  Không biết có cách nào nhẹ nhàng hơn không, nhưng tác giả đã phải sử dụng đến biện pháp này: Cài đặt Visual Studio 2013 (express) download trên trang web của Microsoft khoảng 6GB
  3. Các cập nhật khác
