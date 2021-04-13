# Spark Properties
- Thuộc tính Spark kiểm soát hầu hết các cài đặt ứng dụng và được cấu hình riêng cho từng ứng dụng. Các thuộc tính này có thể được đặt trực tiếp trên SparkConf được chuyển đến của bạn SparkContext. SparkConf cho phép bạn định cấu hình một số thuộc tính chung (ví dụ: URL chính và tên ứng dụng), cũng như các cặp key-value tùy ý thông qua phương thức set().
- Ví dụ: chúng ta có thể khởi tạo một ứng dụng với hai luồng như sau:

```python
val conf = new SparkConf()
             .setMaster("local[2]")
             .setAppName("countingWord")
val sc = new SparkContext(conf)
```
- Với **local[2]**, nghĩa là hai luồng - thể hiện được việc tối thiểu có 2 luồng đang chạy song song, có thể giúp phát hiện lỗi chỉ tồn tại khi ta chạy trong bối cảnh phân tán.
- Các thuộc tính về một khoảng thời gian nhất định phải sử dụng đơn vị thời gian được hỗ trợ trong spark:
```note
25ms (milliseconds)
5s (seconds)
10m or 10min (minutes)
3h (hours)
5d (days)
1y (years)
```


