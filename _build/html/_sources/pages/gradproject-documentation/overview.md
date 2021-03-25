# Overview


## Tomato Classification System

```{note}
Đây là đồ án tốt nghiệp của mình dưới sự hướng dẫn của thầy Vũ Quang Huy, Đại học Sư Phạm Kỹ Thuật TPHCM. Dự án bao gồm 3 phần bên dưới và source code mình đã public trên [Github](https://github.com/phattruongai/Tomato-classification-system), trong bài hướng dẫn này thì mình sẽ giới thiệu chủ yếu về cách mình xây dựng một mô hình phân loại ảnh (image classification model) và chạy hệ thống trên raspberry Pi trong thời gian thực.
```

```{note}
Mình cũng đã publish một [IEEE paper](https://ieeexplore.ieee.org/document/9303079) về mạng neural này và được trình bày tại hội nghị [GTSD 2020](https://easychair.org/cfp/GTSD2020)
```

![](images/3D.png)
<img src="images/tSNE.png" alt="drawing" width="200"/>
<img src="images/model.png" alt="drawing" width="700" height="200"/>


### 1. Mô hình phân loại ảnh (Mạng neural tích chập kết hợp với phép tính Grad-CAM để trực quan hóa dự đoán của mô hình):

#### Hướng dẫn: bấm vào từng link bên dưới để xem chi tiết

* [Chuẩn bị dữ liệu](dataprepare)

* [Huấn luyện](training)

* [Triển khai](deploy)

### 2. PCB và sơ đồ nguyên lí (Tham khảo):

<!-- * [PCB]() -->

### 3. Vi điều khiển (STM32F103C8T6) (Tham khảo):

<!-- * [Controller-STM32F1]() -->
