# Đồ án xây dụng web serverless trên dịch vụ đám mây AWS

Thực hiện tạo một webside serverless quản lý sinh viên đơn giản sử dụng dịch vụ
DynamoDB và Lambda của AWS

## Hướng dẫn cài đặt

### 1. Cài đặt một máy ảo EC2

- Tạo máy ảo EC2 Cloud9Ubuntu cấu hình thì tùy theo nhu cầu sử dụng
- Tạo lần lượt các giao thức SSH, HTTP, HTTPS và một giao thức có Port là 8889
  để truy cập web cho máy ảo.

### 2. Tạo 1 địa chỉ ElasticIP và gán nó vào máy ảo EC2 vừa tạo

- Ở đây mình dùng ElasticIP là:

### 3. Thực hiện cấu hình máy ảo

- Chạy lệnh "sudo apt-get update" để cập nhật phiên bản mới nhất, "sudo apt-get
  install npm" để cài đặt Nodejs.
- Chạy lệnh aws configure và cung cấp lần lượt các thông tin AWS Access Key ID,
  AWS Secret Access Key, Default region name, Default output format.
- Chạy lệnh    
  để cung cấp token.

  -Kiểm tra cách cấu hình kết nối với AWS CLI có thành công hay không: aws sts get-caller-identity

- Tạo thêm các Simple queue service, với 25 sqs
  (ChangePass,DeleteDiemm,DeleteGV,DeleteKhoa,DeleteLop,DeleteMonHoc,DeletePhanCong,DeleteSV,Delete_Account,InsertDiem,InsertGV,InsertLop,InsertMonHoc,InsertPhanCong,InsertSV,Insert_Account,UpdateDiem,UpdateGV,UpdateKhoa,UpdateLop,UpdateMonHoc,UpdatePhanCong,UpdateSV,Update_Account,test,
  )
- Tạo các 8 tables in Dynamodb
  (Account,Diems,GiangViens,Khoas,Lops,MonHocs,PhanCongs,SinhViens)
- Tên các table trong DynamoDB có thể thấy ở các file \*.js ở trong folder
  /environment/Model

### 4. Chạy trương trình

- Đi đến thư mục environment bằng lệnh "cd AWS/environment"
- Chạy lệnh "node index" để chạy trang web

### 5. Áp dụng VPC vào ứng dụng

- Tạo vpc: aws ec2 create-vpc-endpoint --vpc-id vpc-086106c39d2c8ae5c
  --service-name com.amazonaws.us-east-1.dynamodb --route-table-ids
  rtb-0a374d0d08f4479fb

### 6. Deploy Docker

- Cấu hình file Dockerfile
- Đăng nhặp Docker trên máy: docker Login
- Tiến hành build file docker bằng lệnh: docker build -t 19133050/aws:19133050
  -f DockerFile .

- Lệnh chạy Docker: docker run 19133050/aws:19133050
- Deploy Docker lên DockerHub: docker push 19133050/aws:191133050s

### 6. Chú ý

- Nếu xảy ra trùng port thì phải kill port: sudo kill -9 $(sudo lsof -t -i:8889)
