# learn_git
# GIT CƠ BẢN  
## Khái niệm  
Git là hệ thống quản lý mã nguồn và quản lý phân tán. Gít lưu lại những thay đổi code của bạn, mỗi sự thay đổi có ID duy nhất  
## Kiến trúc git
- **Repository** là nhóm các tập tin, thư mục, các ghi chép trong quá khứ.
- Một repo bao gồm thư mục **.git** và **working tree**.
- **Working tree** là nơi bạn thực hiện các thay đổi trên file, thư mục  
- **Chỉ mục( index )**: là staging area của thư mục .git Một lớp riêng biệt với worrking tree, có tác dụng giúp nhà phát triển có thể lựa chọn các thay đổi và push lên git repo  
- **commit**: là nhóm các thay đổi hay thao tác của bạn trong working tree. Không commit  trực tiếp từ worrking tree mà thông qua các thay đổi đã được thêm vào chỉ mục  
- **branch**: Thực chất là con trỏ trỏ đến commit mới nhất. Khi commit tự động trỏ đến commit mới nhất.
- **HEAD và head**: HEAD là con trỏ chỏ đến commit hiện tại và một repo chỉ có 1 HEAD nhưng có thể có nhiều head  
## Các lệnh git cơ bản
1. **git init**: Khởi tạo 1 reop git rỗng.  
2. **git help**: List danh sách các lệnh có sẵn  
   - **git help -a**: list tất cả các lệnh 
   - **git help name_command**: Chi tiết về lẹnh 
3. **git add**: Thêm một file vào  thư mục  
- Thêm vào thư mục hiện tại: git add namefile  
- Thêm vào thư mục khác: git add ./path/to/file

  (Nếu thêm vào thư mục khác, không có trong commit. Khi thêm  file, file sẽ được chuyển vào staging area )
4. **git branch**: Tạo nhánh mới 
- Thêm nhánh mới: **git branch namebranch**  
- Xóa nhánh : **git branch -d namebranch**
- Đổi tên nhánh:**git branch -m oldname newname**
5. **git status**: Lấy ra các thay đổi trong nhánh hiện tại và index  
6. **git checkout**: Thao tác chuyển nhánh 
 Có thể tạo mới và chuyển trực tiếp đén nhánh : **git checkout -b namebranch**
7. **git commit**: Lưu lại những thay đổi hiện tại của index trong commit mới.
8. **git diff**: lấy ra các thay đổi trong thư mục hiện taij , index và commit mới nhất
- git diff : Lấy ra các thay đổi giữa thư mục hiện tại và index 
- git diff --cache: lấy ra các thay đổi giữa index và commit mới nhất
- git diff HEAD: lấy ra các thay đổi giữa thư mục hiện tại và commit mới nhất
9. **git config**: Dùng để lấy ra  giá trị hoặc thiết lập giá trị
10. **git remote**:
- git remote -v: list danh sách các remote hiện có 
- git remote add name url: Thêm remote mới vào 
11. **git log**: Liệt kê danh sách các commit 
12. **git merge**: Gộp các nhánh lai với nhau:
- **git merge namebranch**: Gộp nhánh với nhánh hiện tại
13. **git mv**: Đặt lại tên hoặc di chuyển file
- **git mv namefile newname**: Đặt lại tên file
- **git mv namefile ./path/to/newlocation**: Di chuyển file 
- **git mv -f myfile existfile**: ghi đè file exist
14. **git clone**: Tạo thư mục và sao chép tất cả các file,các nhánh trên git repo
 **git clone url **
15. **git push**: Tải các cam kết từ local lên git     
    **git push \<remote\> \<branch\>** 
16. **git pull**: Kéo các commit trên git và merge vào nhánh  
**git pull \<remote\> \<branch\>**  
    (Mặc định là git push origin master)
17. **git rm namefile**: Dùng để xóa file trong working tre  
18. **git fetch**: dÙng để lấy các dữ liệu mà trên local repo chưa có, nó không ảng hưởng đến các hoạt động code  
git fetch nameremote. Git pull khác với git fetch, nó gần như là tải lại ,cập nhật lại code hiện tại sao cho giống với remote repo.
Cần chú ý những code chưa commit và push sẽ bị mất.
## Các từ khóa:
 1. **git fork**: Giúp copy một dự án và thực hiện các thay dổi 1 mà không ảnh hưởng tới reop gốc
.fork và clone khác nhau. Khi fork dự án của người khác, sẽ tạo cho bạn 1 repository chứa các file của dự án đó. Bạn có thể thao tác và thay đổi dự án đó trên repo của  bạn. Khi bạn clone dựa án, bạn chỉ lấy về local, bạn không thể thực hiện thay đổi trên git do bạn không có quyền  
2. **branch**: Branch dùng để phân luồng và ghi lại lịch sử . có thể hiểu nhánh như các con trỏ chỏ đến commit hiện tại.
Khi muốn thực hiển thử 1 chức năng nào đấy, có thể sử dụng nhánh để thực hiện các thử nghiệm mà không ảnh hưởng tới các nhánh khác.Sau khi thực hiện có thể gộp các nhánh lại.  
  **branch** có hai loại là **branch tích hợp** và **branch chủ đề**.  
- Branch tích hợp: là branch có thể phát hành các nhánh bất kỳ khni nào. Khi commit lần đầu tiên nhánh master được tạo ra và là mặc định. Thông thường nhánh master là nhánh tích hợp.

3. **git merge** :Dùng để hợp nhất các thay đổi các nhánh lại với nhau
- Trường hợp fast-forward (không taọ ra commit): Ví dụ có nhánh debux  từ nhánh master. Khi hợp nhất, chỉ có nhánh debux thay đỏi và nhánh master vẫn giữ nguyên ,  
- Trường hợp non fast( Tạo ra merge commit) : KHi nhánh master cũng có thay đổi trạng thái. Khi merge, sẽ tạo ra commit lấy thay đổi của hai nhánh và nhánh master sẽ được chuyển đến commit đó.
  ( có thể chỉ định việc non fast ).
4. **git conflict**: Xung đột có thể xây  ra khi gộp các nhánh lại với nhau.  
 Xung đột xảy ra khi mà thực hiện các thay đổi trên các nhánh khác nhau mà trên cùng dòng với nội dung khác nhau hoặc  có nhánh thêm file và có nhánh lại xóa file đo đi. 
 Để khắc phục xung đột , bật trình chỉnh sửa lên và sẽ thấy xung đột được đánh dấu. Thực hiện các thay đổi bạn muốn và đăng ký lại các thay đổi và commit lại. 
5.**git server**: Là một máy chủ có cài dịch vụ Git cho phép tạo ra các các repository như github và các repo trên git gọi là các remote repo  
6. **repository**: có thể hiểu là một kho lưu trữ tất cả các mã nguồn đưọc quản lý bởi Git 
- Local repository: repo trên máy cục bộ của từng cá nhân, được đồng bộ hóa với remote repo thông qua các lênh git
- Remote repository : repo được lưu trữ trên server như github
7. **issues** : Giúp bạn quản lý,theo dõi cái ý tưởng, vấn đề, các phản hồi và nhiệm vụ 
8. **wikis**: có chức năng như file readme.md, là tài liệu bổ sung cho file readme. 
9. **stash**: Được sinh ra để giải quyết vấn đề: Khi bạn đang làm việc trên hai nhánh khác nhau. Khi bạn đang thực hiện các task trên nhánh B và bạn cần quay lại nhánh A để fix lỗi. Khi 
đó bạn sẽ gặp lỗi " các thay đổi trên tệp cục bộ sẽ bị ghi đè.. vui lòng commit hoặc lưu trữ lại ".. Và bạn sẽ không thể chuyển về nhánh A.git stash đưọc sinh ra để giải quyết vấn đề này. 
Nó cho phép bạn lưu trữ các thay đổi chưa cam kết  và cho phép bạn chuyển nhánh 
và bạn có thể lấy lại các thay đổi khi cần. Đó là 1 lưu trữ cục bộ không thể đấy lên remote repo
