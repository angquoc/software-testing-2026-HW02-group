# HW02 Domain Testing on EShop: Repo chung của nhóm

Repo này **chỉ dùng cho GitHub Issues** (bug report của cả nhóm) và bảng phân công feature.
Bài làm của mỗi người nằm ở **repo cá nhân riêng** (xem mục 2).

- SUT: [EShop](https://github.com/ttbhanh/eshop-sut)
- Đặc tả (oracle): `README.md` của repo EShop

---

## 1. Phân công feature

Quy tắc:
- Mỗi người làm đúng 4 feature: Pool A, B, C trên Web và Pool D trên Mobile.
- Mỗi FR chỉ có **một người** làm trong cả nhóm, tính chung Web và Mobile.

| Thành viên | MSSV | Pool A (Web) | Pool B (Web) | Pool C (Web Admin) | Pool D (Mobile) |
|---|---|---|---|---|---|
| Trần Thanh An | 23120017 | | | | |
| Hồ Thùy Hương | 23120046 | FR-03 Quên & đặt lại mật khẩu | FR-08 Thanh toán | FR-15 Quản lý sản phẩm | FR-10 Trạng thái đơn hàng (hủy đơn, FR-20) |
| Nguyễn Thị Ánh Ngọc | 23120061 | FR-01 Đăng ký | FR-07 Giỏ hàng | FR-17 Quản lý mã giảm giá | FR-04 Hồ sơ cá nhân |

Muốn đổi feature thì báo cả nhóm trước, sau đó sửa bảng này. Lịch sử commit giữ lại mọi thay đổi.

---

## 2. Repo cá nhân (mỗi người tự tạo)

HW02 là **bài cá nhân**. Đề ghi rõ: Chép bài của nhau, **kể cả chép prompt**, thì cả hai người đều bị 0 điểm.

1. Mỗi người tự tạo một repo **Private** trên GitHub cho bài làm của mình, ví dụ `software-testing-2026-HW02`.
2. **Không** add thành viên khác vào repo cá nhân, **không** gửi prompt, prompt log hay Agent Skill cho nhau.
3. Commit theo từng bước của từng feature (đề bắt buộc). Cuối cùng xuất `git log` ra file text để nộp.
4. Khi review chéo (policy môn học yêu cầu), chỉ gửi nhau **báo cáo** (report, test case, bug report), không gửi prompt.

Những thứ dùng chung trong nhóm: **Bảng phân công mục 1**, **quy ước commit mục 3**, **quy ước Issues mục 4**, và **dữ liệu/môi trường EShop**.

---

## 3. Quy ước commit

```
[<phạm vi>][<bước>] <Verb> <nội dung>
```

- Viết bằng **tiếng Anh**, bắt đầu bằng **động từ ở dạng mệnh lệnh** (Add, Identify, Design, Fix, Update…), không có dấu chấm ở cuối.
- Mỗi commit chỉ chứa **một bước**, không gộp nhiều bước vào một commit.

### 3.1 Commit cho bước kiểm thử (repo cá nhân)

`<phạm vi>` = `<Pool>-<FR>`, ví dụ `A-FR01`, `B-FR09`, `C-FR17`, `D-FR04` (Pool D = Mobile).

| Bước | Nội dung | Ví dụ |
|---|---|---|
| S0 | Trích đặc tả, khám phá giao diện | `[B-FR09][S0] Extract spec and explore UI` |
| S1 | Xác định biến Input / Output | `[B-FR09][S1] Identify input/output variables` |
| S2 | Chia lớp tương đương | `[B-FR09][S2] Identify equivalence classes` |
| S3 | Thiết kế test case Domain Testing | `[B-FR09][S3] Design domain test cases` |
| S4 | Thiết kế test case BVA | `[B-FR09][S4] Design boundary value test cases` |
| S5 | Review, bổ sung test case | `[B-FR09][S5] Review and add missing test cases` |
| S6 | Thực thi test, ghi kết quả | `[B-FR09][S6] Execute tests and record results` |
| S7 | Báo bug, tạo issue | `[B-FR09][S7] Report bugs` |
| S8 | Phân tích phần AI bỏ sót | `[B-FR09][S8] Analyse AI gaps` |

Nếu phải sửa lại một bước đã commit thì giữ nguyên tag của bước đó, ví dụ `[B-FR09][S2] Fix missing invalid class for expired coupon`.

### 3.2 Commit không thuộc feature nào

| Phạm vi | Dùng khi | Ví dụ |
|---|---|---|
| `[setup]` | Cấu trúc thư mục, công cụ, cấu hình | `[setup] Init folder structure` |
| `[skill]` | Agent Skill | `[skill] Add boundary value analysis skill` |
| `[report]` | Báo cáo chung, README, AI Critique, Audit | `[report] Add AI critique` |
| `[forms]` | Các form AI-0x | `[forms] Fill AI-02 audit report` |
| `[docs]` | Tài liệu của repo chung | `[docs] Update feature allocation` |
| `[template]` | Issue template của repo chung | `[template] Add severity field` |

---

## 4. Quy ước GitHub Issues

### 4.1 Ai báo bug nào

- Mỗi người chỉ báo bug tìm được **trong feature mình phụ trách**. Mỗi bug là một issue riêng.
- Trước khi tạo issue, **tìm xem đã có issue tương tự chưa**. Nếu cùng một lỗi cũng xuất hiện ở feature của người khác, ghi `Related #<số issue>` trong phần ghi chú thay vì tạo issue trùng.
- Bắt buộc dùng template **Bug report**. Phải có **ảnh chụp**: Kéo thả ảnh vào ô "Ảnh chụp".
- Tự gán (Assignees) issue cho chính mình.

### 4.2 Tiêu đề issue

```
[MSSV][FR-xx][Web|Admin|Mobile] Mô tả ngắn: Hành vi sai so với đặc tả
```

Ví dụ: `[23120061][FR-09][Web] Mã SAVE10 không áp dụng khi tổng đơn đúng bằng 300.000₫`

### 4.3 Label

| Nhóm | Label | Ý nghĩa |
|---|---|---|
| Loại | `bug` | Tự gắn bởi template |
| Mức độ | `severity: critical` | Mất dữ liệu, lỗ hổng bảo mật, chặn luồng chính (không mua hàng/đăng nhập được) |
| | `severity: high` | Sai nghiệp vụ quan trọng, không có cách đi vòng |
| | `severity: medium` | Sai nghiệp vụ hoặc validation, có cách đi vòng |
| | `severity: low` | Lỗi giao diện, câu chữ, ảnh hưởng nhỏ |
| Nền tảng | `platform: web` / `platform: admin` / `platform: mobile` | Frontend Web / Web Admin / App Mobile |
| Kỹ thuật | `technique: EP` / `technique: BVA` | Tìm ra nhờ Equivalence Partitioning hay Boundary Value Analysis |
| Pool | `pool: A` / `pool: B` / `pool: C` / `pool: D` | Pool của feature |

Mã FR đã ghi ở tiêu đề nên không cần label riêng cho từng FR.

**Cách gắn label cho mỗi issue:**

- Gắn đủ **4 nhóm**: 1 `severity` + 1 `platform` + ít nhất 1 `technique` + 1 `pool`. Label `bug` được template gắn sẵn.
- `technique`: Nếu test case phát hiện bug thuộc phần BVA (giá trị biên) thì gắn `technique: BVA`; thuộc lớp tương đương thì gắn `technique: EP`; nếu cả hai đều phát hiện được thì gắn cả hai.
- `pool` và `platform` phải khớp với bảng phân công ở mục 1. Ví dụ: FR làm trên Mobile thì gắn `pool: D` + `platform: mobile`.
- Chỉ dùng các label có sẵn. Cần thêm label thì báo nhóm, không tự tạo.

**Chọn severity:** Đi lần lượt từng câu hỏi, gặp câu trả lời "Có" đầu tiên thì dừng.

1. Lỗi làm lộ hoặc mất dữ liệu, vượt quyền, hay chặn hẳn luồng chính (không đăng ký, đăng nhập, mua hàng được)? → `severity: critical`
2. Hệ thống chấp nhận dữ liệu sai hoặc tính sai mà người dùng không có cách nào tránh? → `severity: high`
3. Sai quy tắc nghiệp vụ hoặc validation, nhưng vẫn có cách đi vòng để làm đúng? → `severity: medium`
4. Chỉ sai giao diện, câu chữ, thông báo, không ảnh hưởng dữ liệu? → `severity: low`

Ví dụ một issue đầy đủ: `bug`, `severity: medium`, `platform: web`, `technique: BVA`, `pool: A`

**Màu label** (để cả nhóm nhìn quen mắt):

| Label | Màu |
|---|---|
| `severity: critical` | `#B60205` |
| `severity: high` | `#D93F0B` |
| `severity: medium` | `#FBCA04` |
| `severity: low` | `#C2E0C6` |
| `platform: *` | `#1D76DB` |
| `technique: *` | `#5319E7` |
| `pool: *` | `#BFDADC` |

### 4.4 Trạng thái

- **Open:** Mới báo.
- Nếu phát hiện báo nhầm (hiểu sai đặc tả, lỗi do môi trường): **Close as not planned** và ghi lý do.
- Không xoá issue.

---

## 5. Môi trường EShop dùng chung

- Tài khoản mặc định: Admin `admin@eshop.com` / `Admin123!`; User `test@eshop.com` / `Test1234!`
  (`setup_guide.md` của EShop ghi mật khẩu admin `admin123` là **sai**, mật khẩu đúng trong DB là `Admin123!`).
- Reset dữ liệu trước mỗi đợt test: `cd backend && node database.js`.
- Mobile: Sửa `API_URL` trong `frontend-mobile/App.js` thành IP LAN của máy mình. Điện thoại và máy tính dùng chung Wi-Fi.
