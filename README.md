# 🏡 House Prices: Feature Selection & Price Prediction

> **Báo cáo:** Lab04 - Feature Selection (Lựa chọn đặc trưng)   

> **Môn học:** Máy học (Machine Learning)  

> **Giảng viên hướng dẫn:** Đỗ Như Tài  

---

## 📌 1. Giới thiệu Dự án (Overview)

Dự án nghiên cứu và ứng dụng các kỹ thuật chọn lọc đặc trưng (Feature Selection) nhằm nâng cao hiệu suất dự báo giá nhà dựa trên tập dữ liệu **House Prices - Advanced Regression Techniques** từ Kaggle.
* **Nguồn dữ liệu:** Kaggle Dataset (`train.csv`)
* **Kích thước dữ liệu:** 1,460 dòng, 81 cột (dữ liệu thô) \\(\rightarrow\\) 1,458 dòng (sau khi lọc Outliers) \\(\rightarrow\\) 224 cột (sau One-Hot Encoding).
* **Biến mục tiêu (Target Variable):** `SalePrice` (Giá nhà) và `LogSalePrice` = \\(\ln(1 + \text{SalePrice})\\).
* **Mô hình dự báo:** Support Vector Regression (`SVR`), `RandomForestRegressor`, `XGBRegressor`.
* **Kỹ thuật Feature Selection:** 6 phương pháp thuộc 3 nhóm Filter (Pearson, Mutual Information), Wrapper (RFE), và Embedded (Lasso L1, Random Forest Importance) đối sánh với Baseline.

---

### 👥 2. Phân công Nhiệm vụ (Task Assignment)

| STT | Thành viên | MSSV | Chi tiết công việc trong Notebook / Project |
| :-: | :--- | :-: | :--- |
| **1** | **Nguyễn An Nhung** | `3124411203` | • Tổng hợp kết quả project, thiết kế & soạn toàn bộ Slide báo cáo ( `PPT` ).<br>• Nạp các thư viện cốt lõi ( `numpy` , `pandas` , `matplotlib` , `seaborn` ) & cấu hình môi trường.<br>• Kiểm tra & nạp dữ liệu thô ( `train.csv` ), xác nhận kích thước tập dữ liệu ( `df_raw.shape` ).<br>• Lọc ngoại lệ cơ bản theo diện tích ( `GrLivArea > 4000` ) & điền giá trị khuyết thiếu ( `NaN` ). |
| **2** | **Cao Ngọc Hân** | `3124411083` | • Tạo các biến tổng hợp mới ( `TotalSF` , `TotalBath` , `HouseAge` ).<br>• Biến đổi Logarit ( `np.log1p` ) cho biến mục tiêu `SalePrice` & các biến diện tích bị lệch phải.<br>• Kiểm tra tương quan Pearson & loại bỏ các biến đa cộng tuyến ( `GarageArea` , `1stFlrSF` ).<br>• Mã hóa biến định tính ( `pd.get_dummies` ) & sanity check dữ liệu sau tiền xử lý.<br>• Soạn báo cáo PDF : **chương I** (tổng quan), **chương II** (môi trường thực thi), **chương III** (tiền xử lý dữ liệu & Skewness). |
| **3** | **Trần Đỗ Khánh Linh** | `3124411151` | • Tách tập dữ liệu Train/Test ( `80/20` ) & dựng Pipeline cho 6 kỹ thuật Feature Selection.<br>• Đánh giá hiệu suất 5-Fold Cross-Validation trên các mô hình cơ bản ( `SVM` , `XGBoost` , `RandomForest` ).<br>• Tinh chỉnh siêu tham số ( `GridSearchCV` ) & quy đổi sai số ( `RMSE` , `MAE` ) về đơn vị USD thực tế.<br>• Biểu diễn đồ thị thặng dư ( `Residuals Plot` ) & vẽ biểu đồ đối sánh sai số các kỹ thuật Feature Selection.<br>• Soạn báo cáo PDF : **chương IV** (lý thuyết & thực nghiệm FS), **chương V** (đánh giá mô hình & RMSE USD), **kết luận**. |

---

### 🛠️ 3. Công nghệ & Thư viện Sử dụng (Tech Stack)
* **Ngôn ngữ:** Python 3.x
* **Môi trường phát triển:** Jupyter Notebook / VS Code / Kaggle Notebook
* **Thư viện chính:**
  * `pandas`, `numpy`: Thao tác, biến đổi dữ liệu cấu trúc và xử lý logarit `np.log1p`.
  * `matplotlib`, `seaborn`: Trực quan hóa biểu đồ phân phối, đồ thị thặng dư và so sánh sai số RMSE (\$).
  * `scipy`: Thống kê toán học và kiểm định độ lệch Skewness.
  * `scikit-learn`: Phân chia dữ liệu (`train_test_split`), Cross-Validation (`KFold`), Chuẩn hóa (`StandardScaler`), Đóng gói Pipeline, Trích chọn đặc trưng (`RFE`, `SelectKBest`, `LassoCV`, `mutual_info_regression`) và Mô hình hóa (`SVR`, `RandomForestRegressor`, `GridSearchCV`).
  * `xgboost`: Thuật toán `XGBRegressor` tối ưu dự báo.
