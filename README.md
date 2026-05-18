# Customer Retention Analytics & Churn Prediction

> End-to-End Customer Analytics Pipeline – Phân tích hành vi khách hàng, xây dựng Data Warehouse và dự báo churn cho doanh nghiệp bán lẻ.


## Tổng Quan Dự Án

Dự án được xây dựng nhằm giải quyết bài toán:

* giữ chân khách hàng
* phân tích hành vi mua hàng
* hỗ trợ Sales ưu tiên chăm sóc khách hàng có nguy cơ churn

Pipeline kết hợp:

1. Data Cleaning & Feature Engineering bằng Python
2. SQL Server Data Warehouse & Reporting Layer
3. Machine Learning Churn Prediction
4. Dashboard & Business Reporting

Toàn bộ hệ thống được xây dựng theo flow gần với doanh nghiệp thực tế:

* xử lý dữ liệu thô
* tạo analytical dataset
* build feature khách hàng
* train model churn
* xuất báo cáo & dashboard


## Dashboard Phân Tích

### Customer Analytics Dashboard

Dashboard theo dõi:

* Doanh thu
* Lợi nhuận
* Margin %
* Số lượng khách hàng
* Doanh thu theo Segment
* Top khách hàng doanh thu cao
* Xu hướng khách hàng theo tháng

### Product Analytics Dashboard

Dashboard theo dõi:

* Doanh thu theo ngành hàng
* Top sản phẩm doanh thu cao
* Margin theo sản phẩm
* Revenue Share theo Segment
* Hiệu quả lợi nhuận theo nhóm khách hàng


## Cấu Trúc Project

```text
customer-retention-analytics
│
├── data/
│   └── ver1.xlsx
│
├── outputs/
│   ├── churn_list.xlsx
│   └── benchmark_report.xlsx
│
├── sql/
│   ├── sp_Report_ChurnList.sql
│   ├── sp_Report_ChurnBySegment.sql
│   └── sp_Report_RFM_Summary.sql
│
├── Clean_data.py
├── churn_pipeline_main.py
├── requirements.txt
└── README.md
```


## Data Cleaning & Processing

Dữ liệu gốc từ Excel được xử lý bằng Python:

* remove empty rows
* chuẩn hóa dữ liệu text
* convert datatype
* parse ngày tháng
* build Year / Month
* tạo Segment & Ngành Hàng

Sau bước này, dữ liệu được chuyển từ:

```text
raw transaction data
```

thành:

```text
analytical dataset
```


## Feature Engineering

Pipeline xây dựng các feature quan trọng:

* Recency
* Frequency
* AOV
* Margin
* Promo Rate

Các feature phục vụ:

* RFM Analysis
* Customer Segmentation
* Churn Prediction


## Machine Learning Pipeline

Pipeline ML sử dụng:

* Logistic Regression
* Random Forest
* XGBoost

Mục tiêu:

* dự đoán xác suất churn
* phân loại khách hàng theo mức độ rủi ro
* hỗ trợ đội Sales giữ chân khách hàng

Output cuối cùng:

```text
outputs/churn_list.xlsx
```


## SQL Server Reporting Layer

Dữ liệu được đưa vào SQL Server để:

* lưu trữ tập trung
* xây dựng reporting layer
* phục vụ dashboard Power BI

Stored Procedure chính:

* `sp_Report_ChurnList`
* `sp_Report_ChurnBySegment`
* `sp_Report_RFM_Summary`


## Hướng Dẫn Chạy Project

### 1. Cài đặt thư viện

```bash
pip install -r requirements.txt
```


### 2. Chạy Data Cleaning

```bash
python Clean_data.py
```

Script sẽ:

* clean raw data
* build feature
* tạo analytical dataset


### 3. Chạy Churn Prediction Pipeline

```bash
python churn_pipeline_main.py
```

Pipeline sẽ:

* train model
* benchmark model
* predict churn probability
* export churn list


### 4. Import Data vào SQL Server

Mở SSMS:

```text
Tasks
→ Import Data
```

Import:

```text
ver1.xlsx
```

vào bảng:

```text
DataModel
```


### 5. Chạy Stored Procedure

Ví dụ:

```sql
EXEC sp_Report_ChurnList
    @SnapshotDate = '2023-11-30'
```

Kết quả:

* danh sách khách hàng churn
* risk level
* hành động đề xuất cho Sales


## Kết Quả Đạt Được

Hệ thống hỗ trợ:

* phân tích hành vi khách hàng
* dự báo churn
* phân khúc khách hàng
* hỗ trợ Sales action
* xây dựng reporting layer cho dashboard


## Công Nghệ Sử Dụng

* Python
* Pandas
* Scikit-learn
* XGBoost
* SQL Server
* Excel
* Power BI


