\# ☕ Voice Controlled Coffee Machine (Audio-KWS using Edge Impulse)



Dự án triển khai mô hình học máy nhận diện từ khóa giọng nói (\*\*Keyword Spotting - KWS\*\*) trên thiết bị biên (\*\*TinyML\*\*) để điều khiển máy pha cà phê thông minh. Dự án được huấn luyện và mô phỏng thông qua nền tảng \*\*Edge Impulse\*\*.



\---



\## 📌 Tổng quan đề tài

\* \*\*Loại đề tài:\*\* Audio-KWS (Keyword Spotting)

\* \*\*Thuật toán trích xuất đặc trưng:\*\* MFCC (Mel-Frequency Cepstral Coefficients)

\* \*\*Kiến trúc mô hình:\*\* 1D Convolutional Neural Network (CNN)

\* \*\*Mục tiêu:\*\* Nhận diện lệnh giọng nói tiếng Việt thời gian thực để kích hoạt các chế độ pha cà phê tương ứng mà không cần tiếp xúc.

\* \*\*Liên kết dự án Edge Impulse (Public):\*\* https://studio.edgeimpulse.com/studio/1019633



\---



\## 🏷️ Các nhãn nhận diện (Labels)

Hệ thống được huấn luyện với các từ khóa ngắn:

1\. `"duy\_nam"`: Từ kích hoạt hệ thống (Wake word).

2\. `"pha\_espresso"`: Lệnh kích hoạt chế độ pha cà phê Espresso.

3\. `"pha\_latte"`: Lệnh kích hoạt chế độ pha cà phê Latte.

4\. `"noise"`: Tập dữ liệu nhiễu môi trường (tiếng còi, tiếng quạt gió).



\---



\## 💻 Hướng Dẫn Chạy Mô Phỏng (Simulation Guide)



Dự án này được thiết kế để có thể chạy mô phỏng hoàn toàn trên giao diện Web của Edge Impulse bằng Micro của máy tính hoặc điện thoại mà không cần đến thiết bị phần cứng. Có thể kiểm thử mô hình theo 2 cách sau:



\### Cách 1: Kiểm thử thời gian thực bằng Giọng Nói (Live Classification)

1\. \*\*Truy cập dự án:\*\* Mở liên kết Edge Impulse công khai của dự án.

2\. \*\*Kết nối Micro thu âm:\*\* Di chuyển đến mục \*\*Live classification\*\* ở thanh công cụ bên trái -> Nhấn nút \*\*Connect a device\*\* -> Chọn \*\*Use your computer microphone\*\* (hoặc quét mã QR để dùng điện thoại).

3\. \*\*Tiến hành mô phỏng ra lệnh:\*\* Chọn thời gian thu âm (Sample length) là `1000 ms` -> Nhấn nút \*\*Start sampling\*\*, đồng thời đọc to rõ một trong các câu lệnh: `"duy\_nam"`, `"pha\_espresso"`, hoặc `"pha\_latte"`.

4\. \*\*Xem kết quả:\*\* Hệ thống sẽ ngay lập tức trích xuất MFCC và hiển thị bảng tỷ lệ phần trăm (%) dự đoán ở góc phải. Nhãn nào có số % cao nhất chính là lệnh mà AI nhận diện được.



\### Cách 2: Deployment -> WebAssembly -> Build -> Launch in browser -> Test realtime.

\---



\## 📊 Đánh giá mô hình (Model Testing Performance)

Dưới đây là bảng đánh giá hiệu năng thực tế thu được từ ma trận nhầm lẫn (\*\*Confusion Matrix\*\*) trên tập dữ liệu Test độc lập (Độ chính xác tổng thể: \*\*81.25%\*\*, Diện tích dưới đường cong ROC: \*\*0.97\*\*):





| Nhãn gốc (Thực tế) | DUY\_NAM | NOISE | PHA\_ESPR | PHA\_LATT | UNCERTAIN | \*\*Recall (%)\*\* |

| :--- | :---: | :---: | :---: | :---: | :---: | :---: |

| \*\*DUY\_NAM\*\* | \*\*100%\*\* | 0% | 0% | 0% | 0% | \*\*100.0%\*\* |

| \*\*NOISE\*\* | 0% | \*\*100%\*\* | 0% | 0% | 0% | \*\*100.0%\*\* |

| \*\*PHA\_ESPRES\*\* | 0% | 0% | \*\*66.7%\*\* | 25% | 8.3% | \*\*66.7%\*\* |

| \*\*PHA\_LATTE\*\* | 8.3% | 8.3% | 16.7% | \*\*58.3%\*\* | 8.3% | \*\*58.3%\*\* |



\---



\## 📁 Cấu trúc thư mục Source Code



├── data/                # Chứa dữ liệu mẫu thu để training

├── scr/                  # Chứa source code

├── README.md              # Tài liệu hướng dẫn dự án (File này)

```



\---



\## ✍️ Tác giả

\* \*\*Họ và tên:\*\* Đào Duy Nam

\* \*\*Mã số sinh viên:\*\* N23DCCI047

\* \*\*Lớp:\*\* D23CQCI01-N



