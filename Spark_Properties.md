# Spark Properties
- Thuộc tính Spark kiểm soát hầu hết các cài đặt ứng dụng và được cấu hình riêng cho từng ứng dụng. Các thuộc tính này có thể được đặt trực tiếp trên SparkConf được chuyển đến của bạn SparkContext. SparkConf cho phép bạn định cấu hình một số thuộc tính chung (ví dụ: URL chính và tên ứng dụng), cũng như các cặp key-value tùy ý thông qua phương thức set().
Ví dụ: chúng ta có thể khởi tạo một ứng dụng với hai luồng như sau:

```python
val conf = new SparkConf()
             .setMaster("local[2]")
             .setAppName("countingWord")
val sc = new SparkContext(conf)
```

- Các thuộc tính về một khoảng thời gian nhất định phải sử dụng đơn vị thời gian được hỗ trợ trong spark:


