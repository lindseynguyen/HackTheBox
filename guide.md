## Hướng dẫn lấy invitation từ trang HackTheBox
* Các bước tiến hành : 
1. Ở trang chủ hackthebox, tiến hành truy cập thẻ **join** để đến trang https://www.hackthebox.eu/invite nơi sẽ nhập invitecode
2. Click chuột phải chọn => **Inspect**
3. Chọn tab elements , ta sẽ tìm thấy đoạn script với source là: **/js/inviteapi.min.js**
4. Truy cập đến trang https://www.hackthebox.eu/js/inviteapi.min.js => tìm đến đoạn **makeInviteCode** và copy
5. Trở lại trang https://www.hackthebox.eu/invite chuyển sang tab console và paste đoạn ở trên rồi ấn enter ta sẽ nhận được 1 Object có
200 status success và data.
6. Mở rộng tab để xem toàn bộ thông tin ta sẽ thấy 1 đoạn data được mã hóa theo Base64.
7. Truy cập trang https://www.base64decode.org/ để decode ta được một đoạn văn bản : "In order to generate the invite code, make a POST request to /api/invite/generate".
Yêu cầu ta chuyển từ **GET** method sang **POST** method
8. Truy cập trở lại trang https://www.hackthebox.eu/invite vào thẻ **Network**
9. Thực hiện một request mới bằng POST đến https://www.hackthebox.eu/api/invite/generate
10. Check thẻ **Response** sẽ nhận được một đoạn mã được trả về và được mã hóa theo Base64.
11. Truy cập https://www.base64decode.org Giải mã ta được một đoạn code => đó chính là đoạn invite code
12. Truy cập trở về trang https://www.hackthebox.eu/invite và nhập code, lúc này ta sẽ có quyền tạo account đăng nhập vào HackTheBox
