# 📥 Hướng Dẫn Hệ Thống Tự Động Nạp Flashcards

## Tổng Quan

Hệ thống tự động nạp cho phép bạn import flashcards từ nhiều định dạng text khác nhau, giúp việc thêm và quản lý flashcards trở nên dễ dàng hơn.

## Cách Sử Dụng

### Mở Modal Import

**Cách 1:** Click vào nút "📥 Nạp từ Text (I)" trên thanh điều khiển

**Cách 2:** Nhấn phím `I` trên bàn phím

### 3 Cách Nhập Dữ Liệu

#### 1️⃣ Nhập Text Trực Tiếp
- Chọn tab "Nhập Text"
- Dán nội dung flashcards vào ô textarea
- Click "✓ Nạp Dữ Liệu"

#### 2️⃣ Upload File
- Chọn tab "Upload File"
- Click vào vùng upload hoặc kéo thả file vào
- Hỗ trợ file: `.txt`, `.tsv`, `.json`

#### 3️⃣ Drag & Drop
- Kéo file trực tiếp vào vùng upload
- Hệ thống tự động phát hiện và nạp dữ liệu

## Định Dạng Hỗ Trợ

### 📖 Định Dạng Custom (Dễ đọc, dễ viết)

```
=== Card ===
Topic: Phương tiện
JP: 飛行機
Kana: ひこうき
Romaji: hikōki
VI: máy bay
Example JP: ひこうきで東京へ行きます。
Example VI: Tôi đi Tokyo bằng máy bay。
Image: https://...
Credit: https://...

=== Card ===
Topic: Địa điểm
JP: 学校
...
```

**Đặc điểm:**
- Mỗi thẻ bắt đầu bằng `=== Card ===`
- Mỗi trường theo format `Key: Value`
- Trường bắt buộc: `JP`, `VI`
- Trường tùy chọn: `Topic`, `Kana`, `Romaji`, `Example JP`, `Example VI`, `Image`, `Credit`

### 📊 Định Dạng TSV (Tab-separated Values)

```
topic	jp	kana	romaji	vi	exJp	exVi	img	credit
Phương tiện	飛行機	ひこうき	hikōki	máy bay	ひこうきで東京へ行きます。	Tôi đi Tokyo bằng máy bay。	https://...	https://...
Địa điểm	学校	がっこう	gakkō	trường học	バスで学校へ行きます。	Tôi đi đến trường bằng xe buýt。	https://...	https://...
```

**Đặc điểm:**
- Dòng đầu tiên là header (tên các cột)
- Các giá trị cách nhau bởi Tab
- Tương thích với Excel, Google Sheets
- Export từ Excel: File → Save As → Text (Tab delimited)

### 💻 Định Dạng JSON

```json
[
  {
    "topic": "Phương tiện",
    "jp": "飛行機",
    "kana": "ひこうき",
    "romaji": "hikōki",
    "vi": "máy bay",
    "exJp": "ひこうきで東京へ行きます。",
    "exVi": "Tôi đi Tokyo bằng máy bay。",
    "img": "https://...",
    "credit": "https://..."
  },
  {
    "topic": "Địa điểm",
    "jp": "学校",
    ...
  }
]
```

**Đặc điểm:**
- Format JSON chuẩn
- Có thể là array hoặc single object
- Phù hợp cho lập trình viên
- Dễ dàng generate từ code

## File Mẫu

Trong thư mục này có 3 file mẫu:

- `sample-custom.txt` - Ví dụ định dạng Custom
- `sample-tsv.txt` - Ví dụ định dạng TSV
- `sample-json.json` - Ví dụ định dạng JSON

Bạn có thể tải và chỉnh sửa các file này để tạo flashcards của riêng mình.

## Tự Động Nhận Diện Định Dạng

Hệ thống tự động nhận diện định dạng dựa trên nội dung:

1. **JSON**: Nếu bắt đầu bằng `[` hoặc `{`
2. **TSV**: Nếu có ký tự Tab (`\t`)
3. **Custom**: Nếu có `=== Card ===` hoặc `Topic:`, `JP:`, etc.

## Trường Dữ Liệu

| Trường | Bắt buộc | Mô tả |
|--------|----------|-------|
| `jp` | ✅ | Chữ Kanji/Hiragana/Katakana |
| `vi` | ✅ | Nghĩa tiếng Việt |
| `topic` | ❌ | Chủ đề (mặc định: "Khác") |
| `kana` | ❌ | Cách đọc Hiragana/Katakana (mặc định: giống `jp`) |
| `romaji` | ❌ | Phiên âm Latinh |
| `exJp` | ❌ | Câu ví dụ tiếng Nhật |
| `exVi` | ❌ | Câu ví dụ tiếng Việt |
| `img` | ❌ | URL hình ảnh |
| `credit` | ❌ | Nguồn hình ảnh |

## Tips & Tricks

### 1. Tạo Flashcards Từ Excel
1. Tạo bảng trong Excel với các cột: topic, jp, kana, romaji, vi, exJp, exVi
2. File → Save As → Text (Tab delimited) (*.txt)
3. Upload file .txt vào hệ thống

### 2. Tạo Flashcards Từ Google Sheets
1. Tạo bảng trong Google Sheets
2. File → Download → Tab-separated values (.tsv)
3. Upload file .tsv vào hệ thống

### 3. Backup Dữ Liệu
- Lưu flashcards của bạn dưới dạng file text
- Dễ dàng khôi phục khi cần
- Có thể chia sẻ cho bạn bè

### 4. Tạo Flashcards Nhanh
- Sử dụng định dạng Custom cho tạo thủ công
- Chỉ cần điền JP và VI là đủ
- Các trường khác sẽ tự động điền giá trị mặc định

## Phím Tắt

| Phím | Chức năng |
|------|-----------|
| `I` | Mở modal import |
| `Esc` | Đóng modal import |

## Xử Lý Lỗi

Nếu gặp lỗi khi import:

1. **"Nội dung trống"** - Kiểm tra xem có paste/upload đúng không
2. **"Không nhận diện được định dạng"** - Kiểm tra lại format, xem ví dụ trong tab "Hướng dẫn"
3. **Không có thẻ nào được tạo** - Đảm bảo có ít nhất trường `JP` và `VI`

## Ví Dụ Tạo Flashcards Nhanh

### Tối thiểu (chỉ cần JP và VI):

```
=== Card ===
JP: 本
VI: sách

=== Card ===
JP: 猫
VI: mèo
```

### Đầy đủ thông tin:

```
=== Card ===
Topic: Động vật
JP: 猫
Kana: ねこ
Romaji: neko
VI: mèo
Example JP: 猫がいます。
Example VI: Có một con mèo。
```

## Hỗ Trợ

Nếu có vấn đề hoặc câu hỏi, vui lòng:
1. Kiểm tra tab "Hướng dẫn" trong modal import
2. Xem các file mẫu trong thư mục
3. Đảm bảo định dạng đúng theo hướng dẫn

---

**Lưu ý:** Hệ thống sẽ **thay thế hoàn toàn** các flashcards hiện tại khi import. Nếu muốn giữ lại dữ liệu cũ, hãy backup trước khi import.
