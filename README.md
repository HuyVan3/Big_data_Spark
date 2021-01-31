# Mục Lục
1. [Tìm Hiểu Spark và MapReduce](#sparkmap)
2. [Apache Spark là gì](#Apachespark)
3. [MapReduce](#Mapreduce)
4. [Spark properties](#sparkprop)
5. [Spark RDD](#sparkrdd)
6. [Spark DataFrame](#sparkdata)


## Tìm Hiểu Spark và MapReduce <a name="sparkmap"></a>
## Apache Spark là gì <a name="Apachespark"></a>
  - Được phát triển vào năm 2009 bởi AMPLab. Sau này Apache Software Foundation đã được trao quyền phát triển vào năm 2013.
  - Apache spark là một công cụ tính toán dữ liệu mã nguồn mở. Apache spark được thiết kế để hỗ trợ trong tính toán dữ liệu lớn, stream data, graph data và hỗ trợ các hệ thống trí tuệ nhân tạo, học máy.
  - Tính năng nổi bật của Spark: tốc độ tính toán nhanh, hỗ trợ đa định dạng, và có nhiều thư viện hỗ trợ tính toán, đơn giản:
      - Tốc độ tính toán nhanh của spark đạt được thông qua việc chia đều khối lượng tính toán cho các cụm máy tính có khả năng tính toán song song có trong hệ thống.
      - Spark cho phép xử lý dữ liệu theo thời gian thực, vừa nhận dữ liệu từ các nguồn khác nhau đồng thời thực hiện ngay việc xử lý trên dữ liệu vừa nhận được ( Spark Streaming).
     - Spark không có hệ thống file của riêng mình, nó sử dụng hệ thống file khác như: HDFS, Cassandra, S3,…. Spark hỗ trợ nhiều kiểu định dạng file khác nhau (text, csv, json…) đồng thời nó hoàn toàn không phụ thuộc vào bất cứ một hệ thống file nào
     - Sự đơn giản của Spark tới từ việc thay vì đòi hỏi người dùng phải hiểu rạch ròi về MapReduce và lập trình Java, Spark sinh ra để gíup mọi người tiếp cận với công nghệ tính toán song song dễ dàng hơn rất nhiều. Người dùng chỉ cần một vài kiến thức cơ bản về database cộng với lập trình Python hay Scala là có thể sử dụng được.
  - **Các thành phần của spark** 
  ![spark](https://www.oreilly.com/library/view/learning-spark/9781449359034/assets/lnsp_0101.png)
      - Spark Core là nền tảng cho các thành phần còn lại và các thành phần này muốn khởi chạy được thì đều phải thông qua Spark Core do Spark Core đảm nhận vai trò thực hiện công việc tính toán và xử lý trong bộ nhớ (In-memory computing) đồng thời nó cũng tham chiếu các dữ liệu được lưu trữ tại các hệ thống lưu trữ bên ngoài.
      - Spark SQL cung cấp một kiểu data abstraction mới (SchemaRDD) nhằm hỗ trợ cho cả kiểu dữ liệu có cấu trúc (structured data) và dữ liệu nửa cấu trúc (semi-structured data – thường là dữ liệu dữ liệu có cấu trúc nhưng không đồng nhất và cấu trúc của dữ liệu phụ thuộc vào chính nội dung của dữ liệu ấy). Spark SQL hỗ trợ DSL (Domain-specific language) để thực hiện các thao tác trên DataFrames bằng ngôn ngữ Scala, Java hoặc Python và nó cũng hỗ trợ cả ngôn ngữ SQL với giao diện command-line và ODBC/JDBC server.
      -Spark Streaming được sử dụng để thực hiện việc phân tích stream bằng việc coi stream là các mini-batches và thực hiệc kỹ thuật RDD transformation đối với các dữ liệu mini-batches này. Qua đó cho phép các đoạn code được viết cho xử lý batch có thể được tận dụng lại vào trong việc xử lý stream, làm cho việc phát triển lambda architecture được dễ dàng hơn. Tuy nhiên điều này lại tạo ra độ trễ trong xử lý dữ liệu (độ trễ chính bằng mini-batch duration) và do đó nhiều chuyên gia cho rằng Spark Streaming không thực sự là công cụ xử lý streaming giống như Storm hoặc Flink.
      - MLlib (Machine Learning Library): MLlib là một nền tảng học máy phân tán bên trên Spark do kiến trúc phân tán dựa trên bộ nhớ. Theo các so sánh benchmark Spark MLlib nhanh hơn 9 lần so với phiên bản chạy trên Hadoop (Apache Mahout).
      - GrapX: Grapx là nền tảng xử lý đồ thị dựa trên Spark. Nó cung cấp các Api để diễn tả các tính toán trong đồ thị bằng cách sử dụng Pregel Api.
   - Spark là một công cụ quan trọng cốt lõi để xây dựng cái data warehouse cũng như xử lý lượng dữ liệu khổng lồ được tạo ra liên tục trên môi trường mạng. Đây là một phân khúc lớn trong ngành IT có khả năng thu về hàng tỉ đô doanh thu hằng năm.
   - Spark tạo ra nhiều lựa chọn cho các công cụ sử dụng hơn là chỉ mỗi Hadoop.
## MapReduce <a name="Mapreduce"></a>
  - MapReduce là mô hình tính toán được thiết kế có khả năng xử lý các tập dữ liệu lớn song song và công việc tính toán đó được chia đều ra trên 1 cụm máy tính.
  - Ý tưởng của MapReduce:
    - Chia vấn đề cần xử lý thành các phần nhỏ để xử lý.
    - Xử lý các phần nhỏ đó một cách song song và độc lập trên cụm các máy tính phân tán.
    - Tổng hợp các kết quả thu được để dưa ra kết quả cuối cùng.
  - Hoạt động của MapReduce có thể được tóm tắt như sau:
     - Đọc dữ liệu đầu vào
     - Xử lý dữ liệu đầu vào (thực hiện hàm map)
     - Sắp xếp và trộn các kết quả thu được từ các máy tính phân tán thích hợp nhất.
     - Tổng hợp các kết quả trung gian thu được ( thực hiện hàm reduce)
     - Đưa ra kết quả cuối cùng.
     ![MapReduce](https://todaysoftmag.com/images/articles/tsm33/large/a11.png)
   - MapReduce bao gầm 2 hàm chính: Map() và Reduce():
     - Hàm Map(): có nhiệm vụ nhận input và tạo ra một cặp (key, value) cặp dữ liệu này sẽ là input của hàm Reduce().
     - Hàm Reduce(): có nhiệm vụ tiếp nhận các cặp (key, value) trung gian lấy ra các value có cùng ke .
     - Ở giữa hàm Map() và Reduce() là công đoạn shuffle. Công đoạn này chuyển các cặp (key, value) vào hàm Reduce() và shuffle có thể xảy ra trước khi hàm Map() thực hiện xong. 
     - Trong công đoạn Shuffle còn có cả Sorting . 
     - Sorting giúp tiết kiệm thời gian cho hàm Reduce() khi sắp xếp lại các cặp giá trị (key, value).
   - Những ưu điểm của MapReduce khiến cho việc áp dụng rộng rãi trong lĩnh vực xử lý dữ liệu lớn:
     - Tính toán dễ dàng những bài toán có lượng dữ liệu lớn nhờ khả năng chia nhỏ dữ liệu cho các cụm máy tính.
     - Khả năng chạy tính toán song song trong cụm máy phân tán.
     - Thực hiện được trên nhiều ngôn ngữ lập trình khác nhau như Java, python, C/C++, Perl, Ruby.
  - Nhờ khả năng vượt trội trong tính toán dữ liệu lớn nên MapReduce được sử dụng trong thực tiễnL
     - Thống kê số từ khóa xuất hiện trong các documents.
     - Thống kê số documents có chứa từ khóa.
     - Thống kê số câu match với pattern trong các documents.
     - Thống kê số URLs xuất hiện trong các web pages.
     - Thống kê số lượt truy cập các URLs.
     - Thống kê số từ khóa trên các hostnames.
     - Distributed Sort.
  - [Count k Word](https://colab.research.google.com/drive/1lkCCFtDqb6-IGOqea-hTYxLQFyiYppS8)
## Spark Properties <a name="sparkprop"></a>
  
## Spark RDD <a name="sparkrdd"></a>
  - Resilient Distributed Datasets (RDD) là một cấu trúc dữ liệu cơ bản của Spark.
  - Nó là một tập hợp bất biến phân tán của một đối tượng. Mỗi dataset trong RDD được chia ra thành nhiều phần vùng logical. Có thể được tính toán trên các node khác nhau của một cụm máy chủ (cluster).
  - RDDs có thể chứa bất kỳ kiểu dữ liệu nào của Python, Java, hoặc đối tượng Scala, bao gồm các kiểu dữ liệu do người dùng định nghĩa.
  - Có hai cách để tạo RDDs:
    . Tạo từ một tập hợp dữ liệu có sẵn trong ngôn ngữ sử dụng như Java, Python, Scala.
    . Lấy từ dataset hệ thống lưu trữ bên ngoài như HDFS, Hbase hoặc các cơ sở dữ liệu quan hệ.
## Spark DataFrame <a name="sparkdata"></a>
