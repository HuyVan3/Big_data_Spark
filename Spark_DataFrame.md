# Spark DataFrame
DataFrame là một tập hợp dữ liệu phân tán được tổ chức thành các cột được đặt tên. Về mặt khái niệm, nó tương đương với một bảng trong cơ sở dữ liệu quan hệ hoặc một khung dữ liệu trong R / Python, nhưng với các tối ưu hóa phong phú hơn. DataFrames có thể được xây dựng từ nhiều nguồn như tệp dữ liệu có cấu trúc, Hive table, cơ sở dữ liệu bên ngoài hoặc RDD hiện có.

Dataframe thường đề cập đến một cấu trúc dữ liệu, có bản chất là dạng bảng. Nó đại diện cho các Hàng, mỗi hàng bao gồm một số quan sát. Các hàng có thể có nhiều định dạng dữ liệu khác nhau (Không đồng nhất), trong khi một cột có thể có dữ liệu có cùng kiểu dữ liệu (Đồng nhất). Khung dữ liệu thường chứa một số siêu dữ liệu ngoài dữ liệu; ví dụ, tên cột và hàng.

![Spark_DataFrame_Define](https://user-images.githubusercontent.com/77387844/114503872-2a8ef880-9c58-11eb-9ca8-6dc71f4276f1.png)

# Lý do sử dụng DataFrames
![why_use_dataframe](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2019/04/new-3-528x270.png)
 - ***Tương thích nhiều ngôn ngữ lập trình (Multiple Programming languages)***:
   - Dataframe trong Spark hỗ trợ nhiều ngôn ngữ lập trình bao gồm. R, Python, Scala, Java
 - ***Nhiều Nguồn dữ liệu (Multiple data sources)***.
   - Dataframe trong Spark hỗ trợ nhiều nguồn dữ liệu khác nhau.
 - ***Xử lý dữ liệu có cấu trúc và bán cấu trúc (Processing Structured and Semi-Structured Data)***:
   - DataFrames được thiết kế để xử lý một tập hợp lớn dữ liệu có cấu trúc cũng như bán cấu trúc . 
   - Điều này giúp Spark tối ưu hóa kế hoạch thực hiện trên các truy vấn này và có thể xử lý petabyte dữ liệu.
 - ***Cắt lát và thái hạt lựu (Slicing and Dicing the data)***:
   - PI DataFrames thường hỗ trợ các phương thức phức tạp để cắt và xử lý dữ liệu. Nó bao gồm các hoạt động như "chọn" các hàng, cột và ô theo tên hoặc theo số, lọc ra các hàng, v.v. Dữ liệu thống kê thường rất lộn xộn và chứa nhiều giá trị thiếu và không chính xác và vi phạm phạm vi. Vì vậy, một tính năng cực kỳ quan trọng của DataFrames là quản lý dữ liệu bị thiếu.
# ĐẶC ĐIỂM DATAFRAME

![features_spark_dataframe](https://www.edureka.co/blog/content/ver.1554792280/uploads/2019/04/Picture11.png)

* Các khung dữ liệu được phân phối trong tự nhiên, điều này làm cho nó có khả năng chịu lỗi và cấu trúc dữ liệu có sẵn cao.
* Đánh giá lười biếng là một chiến lược đánh giá giữ việc đánh giá một biểu thức cho đến khi giá trị của nó là cần thiết. Nó tránh đánh giá lặp lại. Đánh giá lười biếng trong Spark có nghĩa là quá trình thực thi sẽ không bắt đầu cho đến khi một hành động được kích hoạt. Trong Spark, bức tranh về sự lười biếng xuất hiện khi các phép biến đổi Spark xảy ra.
* Dataframe có bản chất là Bất biến . Không thay đổi được, ý tôi là nó là một đối tượng có trạng thái không thể sửa đổi sau khi nó được tạo. Nhưng chúng ta có thể biến đổi các giá trị của nó bằng cách áp dụng một phép biến đổi nhất định , như trong RDD.

# DATAFRAME CREATION

DataFrame trong Pyspark có thể được tạo theo nhiều cách:

![sources_spark_dataframe](https://www.analyticsvidhya.com/wp-content/uploads/2016/10/DataFrame-in-Spark.png)

Dữ liệu có thể được tải vào thông qua tệp CSV, JSON, XML hoặc tệp Parquet. Nó cũng có thể được tạo bằng cách sử dụng RDD hiện có và thông qua bất kỳ cơ sở dữ liệu nào khác, như Hive Table hay Apache Cassandra . Nó cũng có thể lấy dữ liệu từ HDFS hoặc hệ thống tệp cục bộ.



## DataFrame Operations

Giống như RDD, DataFrame cũng có các hoạt động như Biến đổi (DataFrame Transformations) và Hành động (DataFrame Actions).


## Các định dạng tệp được hỗ trợ
![Dataframe_source](https://d1jnx9ba8s6j9r.cloudfront.net/blog/wp-content/uploads/2019/04/new-2-768x448.png)

DataFrame có một bộ API phong phú hỗ trợ đọc và ghi một số định dạng tệp như:

* csv
* text
* Avro
* Parquet
* tsv
* xml và nhiều hơn nữa,...

# VÍ DỤ CỤ THỂ VIỆC SỬ DỤNG DATAFRAME LOAD DATA TỪ 1 FILE CSV

Link Google Colab ví dụ: 


# TÀI LIỆU THAM KHẢO

* https://codetudau.com/xu-ly-du-lieu-voi-spark-dataframe/index.html
* https://helpex.vn/article/huong-dan-pyspark-dataframe-gioi-thieu-ve-dataframes-5c6b21e6ae03f628d053c29e
* https://www.edureka.co/blog/pyspark-dataframe-tutorial/#what
* https://sparkbyexamples.com/pyspark-tutorial/

