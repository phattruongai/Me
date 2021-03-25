# Chuẩn bị dữ liệu

```{note}
Download dữ liệu tại [đây](https://phat-collection.s3-ap-southeast-1.amazonaws.com/cachua_resize2.rar)
```

## 1. Clone github về local machine của mình:

* Chạy: 

```
git clone https://github.com/phattruongai/Tomato-classification-system.git
cd Tomato-classification-system/Classification
```

## 2. Tổ chức thư mục 

Sau khi download dữ liệu về và giải nén thì ta sẽ có 1 thư mục tên `cachua_resize2`, đặt thư mục này như đường dẫn sau `Tomato-classification-system/Classification/cachua_resize2`

* Cây thư mục:

```
Classification
    |---cachua_resize2
        |---train
        |   |---loai1
        |   |---loai2
        |   |---loai3
        |   |---loai4
        |   |---loai5
        |   `---loai6
        `---test
            |---loai1
            |---loai2
            |---loai3
            |---loai4
            |---loai5
            `---loai6
```

## 3. Tiền xử lí và đóng gói dữ liệu:

Mở file `Classification/make_data_and_preprocessing/make_data/make_data/make_data.py` để xem các đoạn code, mình sẽ giải thích một số đoạn, để đơn giản, các bạn chỉ cần chạy script như cuối phần này

* Resize và normalize:
> Tất cả các ảnh được đưa về 100x100 và chia 255 để có giá trị nằm trong khoảng [0,1]

```
train_classes = os.listdir(train_dir)
x_train = []
y_train = []
i = 0
for t_class in train_classes:
    y_now = np.zeros((6,))
    t_list = os.listdir(train_dir+t_class)
    y_now[int(t_class[4])-1] = 1
    for img_name in t_list:
        print(t_class,img_name)
        img = cv2.imread(train_dir+t_class+"/"+img_name)
        img = cv2.resize(img,(100,100)) #resize
        img = img/255 #normalization
        x_train.append(img)
        y_train.append(y_now)
```

* Đóng gói bằng thư viện h5py:

Sau khi tạo ra được mảng x_train và y_train dưới dạng numpy.array, ta lưu vào file h5py để tiện việc sử dụng nhiều lần trong lúc huấn luyện

```
x = np.asarray(x_train) #data, shape (num_image,100,100,3)
y = np.asarray(y_train) #label,shape (num_image,6)
print(len(x))
x_train,y_train = shuffle_data(x,y)
with h5py.File(args.output,'w') as F:
    F.create_dataset('x_train',data = x_train)
    F.create_dataset('y_train',data = y_train)
```

```{note}
Để đơn giản, chỉ cần chạy script dưới đây
```

```
python3 make_data_and_preprocessing/make_data/make_data/make_data.py --working . --output train_data_100.h5
```

Sau khi chạy xong, ta có file `train_data_100.h5` là file lưu dataset trực tiếp dưới dạng numpy array, tiện để load lên dùng lại nhiều lần trong lúc train. **Lưu ý, với các dataset cực lớn thì lưu trực tiếp vào h5py sẽ không có lợi, thậm chí không chạy được vì không đủ RAM, khi đó ta sẽ dùng các cách khác để load dataset theo từng phần nhỏ trong lúc huấn luyện**