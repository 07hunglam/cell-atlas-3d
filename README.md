# Cell Atlas 3D

Một tế bào động vật chạy trên trình duyệt, bay xuyên qua được. Mọi thứ sinh ra từ code: không có model 3D, không có texture, không có bước build.

A procedural 3D animal cell in the browser: fly through it, watch a gene being expressed, simulate diffusion, and diagnose a broken organelle. One HTML file, three.js, no build step.

**Chạy thử: https://cell.hunglam.id.vn**

## Có gì

1. **Atlas bào quan.** 13 bào quan dựng bằng hình học procedural và shader. Bấm vào bào quan để bay tới, xem mô tả tiếng Anh kèm thuật ngữ Anh–Việt.
2. **Central dogma.** Nhập một chuỗi DNA (tối đa 120 nucleotide). RNA polymerase phiên mã trong nhân, mRNA chui qua lỗ nhân, ribosome dịch mã thành polypeptide. Bảng trình tự chạy song song, thẳng cột theo codon.
3. **Khuếch tán.** Tới 50.000 phân tử chuyển động Brown và va chạm. Dò va chạm bằng spatial hash (counting sort, nửa lân cận) thay vì dò mọi cặp O(n²); vẽ bằng một `InstancedMesh`. Có ô bật O(n²) để so sánh.
4. **Quiz chẩn đoán.** Một bào quan bị hỏng. Quan sát triệu chứng trong cảnh 3D, đọc ba kết quả xét nghiệm, rồi chọn bào quan nghi ngờ. 11 ca.

## Điều khiển

| Thao tác | Tác dụng |
|---|---|
| Kéo chuột | Xoay |
| Cuộn | Phóng to, thu nhỏ |
| `W` `A` `S` `D`, `Q` `E` | Bay; giữ `Shift` để bay nhanh |
| Bấm bào quan | Bay tới, mở thông tin |
| `L` | Ẩn hoặc hiện nhãn |
| `Esc` | Đóng bảng thông tin |

## Chạy trên máy

Cần mạng để tải three.js và font từ CDN.

```bash
python -m http.server 5173
```

Rồi mở `http://localhost:5173`.

## Tự kiểm

Mở `index.html?check` và xem console. Trang tự kiểm ba việc: mỗi bào quan có đủ nhãn, vật liệu và vật thể bấm được; spatial hash tìm ra đúng tập cặp va chạm như cách dò mọi cặp; mỗi ca quiz bật rồi tắt triệu chứng trả cảnh về nguyên trạng.

## Giới hạn đã biết

- Mô hình rút gọn: phiên mã cả chuỗi, không có promoter, intron, mũ 5′, đuôi poly-A, tRNA.
- Kích thước phân tử phóng đại nhiều lần so với bào quan.
- Phân tử khuếch tán chỉ bị chặn bởi màng và nhân, bay xuyên các bào quan khác.

## Công nghệ

three.js r170 (WebGL), GLSL cho màng tế bào, HTML và CSS thuần.
