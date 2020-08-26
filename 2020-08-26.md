# Báo cáo git flow
### Câu lệnh : 
- git flow init : Khởi tạo git flow vào dự án
---------------------------------------------------------------------
*Git flow dùng để cải thiện tình trạng làm việc giữa các thành viên trong team với nhau. Mục đích là các công việc được triển khai song song nhưng không ảnh hưởng tới nhau. Các môi trường development, staging và production tách biệt giúp dễ dàng kiểm thử, xử lý gọn gàng và thống nhất hơn*

*Git-Flow gồm có 2 nhánh chính là Master và Develop, 3 nhánh Phụ gồm: Feature, Release, HotFix*

*Trong Git flow ta không commit trực tiếp vào master mà đây chỉ là nhánh để thực hiện merge*

*Branch develop là branch trung tâm cho việc phát triển*

## Nhánh Feature branch
    1. Tách từ: develop
	2. Merge vào: develop
	3. Naming convention: tự do, ngoại trừ master, develop, release-*, hotfix-*
- Feature branches được sử dụng để phát triển các feature mới phục vụ cho release sau này

### Các lệnh:
- git flow feature start MYFEATURE : Tạo 1 feature dựa trên nhánh develop và chuyển sang nhánh mới này
- git flow feature finish MYFEATURE : Kết thúc nhánh ( merge nhánh MYFEATURE vào nhánh develop và xoá nhánh tính năng )
- git flow feature publish MYFEATURE : Công bố mã nguồn lên remote để người khác có thể cập nhật được
- git flow feature pull REMOTE_NAME MYFEATURE : Pull mã nguồn của tính năng được cập nhật bởi những thành viên khác

## Nhánh Release branch
	1. Tách từ: develop
	2. Merge vào: develop và master
	3. Naming convention: release-*
- Release branches được sử dụng để chuẩn bị cho release bản production mới. Tất cả các công việc cuối cùng trước khi release sẽ được thực hiện ở đây
### Các lệnh: 
- git flow release start RELEASE [BASE] : Tạo branch release
- git flow release publish RELEASE : Công bố phần code 'release' cho các thành viên khác
- git flow release track RELEASE : Theo dấu remote 'release' bằng lệnh
- git flow release finish RELEASE : Kết thúc release 
- git flow release finish RELEASE -m [message] : Kết thúc release
    1. merge nhánh release vào nhánh master
    2. gắn tag ở nhánh master dành cho bản release

## Nhánh Hotfix branch
	1. Tách từ: master
	2. Merge vào: develop và master
	3. Naming convention: hotfix-*
- Khi release sản phẩm cũng có khi ta phát hiện ra bug rất nghiêm trọng. Những lúc như vậy ta sẽ ngắt ra branch hotfix trực tiếp từ branch master để tiến hành sửa, sau khi sửa xong sẽ merge vào master và develop và ghi lại release tag. Sau đó sẽ xóa branch hotfix đi.
### Các lệnh:
- git flow hotfix start Version [Basename] : Bắt đầu 1 branch hotfix
- git flow hotfix finish VERSION : Kết thúc hotfix và merge lại nội dung thay đổi vào nhánh 'develop' và 'master'