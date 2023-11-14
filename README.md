# Git Commit Convention 
Xem một thay đổi nhỏ trong phong cách commit message có thể tạo ra sự khác biệt như thế nào. [Examples](#examples)

<img src="https://nhobethoi.com/wp-content/uploads/2021/06/git-merge-gop-cac-nhanh-thanh-nhanh-duy-nhat-1.png" width="400" height="300" />

## Định dạng Commit

### Default
<pre>
<b><a href="#types">&lt;type&gt;</a></b></font>(<b><a href="#scopes">&lt;optional scope&gt;</a></b>): <b><a href="#description">&lt;description&gt;</a></b>
<!-- <sub>empty separator line</sub> -->
<b><a href="#body">&lt;optional body&gt;</a></b>
<!-- <sub>empty separator line</sub> -->
<b><a href="#footer">&lt;optional footer&gt;</a></b>
</pre>

### Merge Commit
<pre>
Merge branch '<b>&lt;branch name&gt;</b>'
</pre>
<sup>(Dựa theo mặc định commit merge branch)</sup>

### Revert Commit
<pre>
Revert "<b>&lt;reverted commit subject line&gt;</b>"
</pre>
<sup>(Dựa theo mặc định commit revert)</sup>


### Types - Phân loại Commit
* Những thay đổi liên quan đến tính năng:
    * `feat` Commit thêm hoặc xóa một tính năng mới (cũ)
    * `fix` Commit fix một bug

* `refactor` Commit viết lại hoặc cấu trúc lại code nhưng không làm thay đổi các tính năng trước đó, hoặc clean code.
    * `perf` Commit là một commit `refactor` tái cấu trúc đặc biệt, nhằm cải thiện hiệu năng

* `style` Commit sửa lại các định dạng code, không làm thay đổi ý nghĩa code ( loại bỏ khoảng trắng, dòng trắng, format code, thêm dấu chấm phẩy, vv)

* `test` Commit thêm, sửa test case, unit test
* `docs` Commit chỉ dành cho việc ảnh hưởng đến tài liệu sản phẩm
* `build` Commit ảnh hưởng đến các thành phần build dự án như công cụ build, CI/CD, thư viện liên kết, build version, relase version, ...
* `ops` Commit ảnh hưởng đến các thành phần hoạt động như cơ sở hạ tầng, triển khai, sao lưu, phục hồi, ...
* `chore` Các commit khác, làm các việc vặt ví dụ như sửa file `.gitignore`

### Scopes - Phạm vi
`scope` cung cấp thêm thông tin ngữ cảnh của commit.
* Là một tùy chọn **optional** cho format commit
* Phạm vi tùy thuộc vào dự án cụ thể
* Không sử dụng mã định danh issue làm phạm vi

### Chỉ báo thay đổi đột phá
Những thay đổi đột phá nên được chỉ định bởi một ký tự `!` trước dấu `:` trong dòng chủ đề. Ví dụ:
<pre>
feat(api)!: remove status endpoint
</pre>
* Là một tùy chọn **optional** cho định dạng commit

### Description - Miêu tả
`description` Mô tả chứa mô tả ngắn gọn về sự thay đổi.
* Là một phần **mandatory - bắt buộc** cho định dạng commit
* Sử dụng câu mệnh lệnh, thì hiện tại: "change" không phải "changed" cũng không phải "changes"
* Không viết in hoa chữ cái đầu tiên
* không dùng chấm câu (.) ở cuối

### Body - Thân commit
`body` nên bao gồm động lực cho sự thay đổi và đối chiếu commit này với commit trước đó.
* Là một tùy chọn **optional** cho format commit
* Sử dụng câu mệnh lệnh, thì hiện tại: "change" không phải "changed" cũng không phải "changes"
* Đây là nơi đề cập đến các mã định danh issue và mối quan hệ của các issue, commit

### Footer - Phần chân commit
`footer` nên chứa bất kỳ thông tin nào về **Breaking Changes - Những thay đổi đột phá** và cũng là nơi để **reference Issues - tham chiếu đến issues khác** mà commit này đề cập đến.
* Là một tùy chọn **optional** cho format commit
* **Optional - Tùy chọn** tham chiếu 1 issue bằng ID của nó.
* **Breaking Changes - Những thay đổi đột phá** nên bắt đầu bằng từ `BREAKING CHANGES:` theo sau là dấu cách hoặc hai dòng mới. Phần còn lại của commit message sau đó sẽ được sử dụng cho việc này.


### Examples
* ```
  feat: add email notifications on new direct messages
  ```
* ```
  feat(shopping cart): add the amazing button
  ```
* ```
  feat!: remove ticket list endpoint

  refers to JIRA-1337

  BREAKING CHANGES: ticket enpoints no longer supports list all entites.
  ```
* ```
  fix(api): handle empty message in request body
  ```
* ```
  fix(api): fix wrong calculation of request body checksum
  ```
* ```
  fix: add missing parameter to service call

  The error occurred because of <reasons>.
  ```
* ```
  perf: decrease memory footprint for determine uniqe visitors by using HyperLogLog
  ```
* ```
  build: update dependencies
  ```
* ```
  build(release): `bump version to 1.0.0
  ```
* ```
  refactor: implement fibonacci number calculation as recursion
  ```
* ```
  style: remove empty line
  ```

-----
## References
* https://www.conventionalcommits.org/
* https://github.com/angular/angular/blob/master/CONTRIBUTING.md
* https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13
