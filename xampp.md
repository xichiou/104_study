# 安裝 XAMPP

### 下載

https://www.apachefriends.org/zh_tw/download.html


### 安裝

1. Learn more about Bitnami for XAMPP 可以不用勾選
![](images/xamp-setup1.png)

2. 開放防火牆
![](images/xamp-setup2.png)

3. 安裝完成，啟動XAMPP控制台
![](images/xamp-setup3.png)

4. 修改 Apache->Config->httpd-ssl.conf
![](images/xamp-setup4.png)
找到 
```
ServerName www.example.com:443
```
改成
```
ServerName localhost:443
```

5. 啟動Windoes工作管理員，結束httpd.exe，回到 XAMPP Control Panel， Apache->Start
![](images/xamp-setup5.png)

6. XAMPP Control Panel， MySQL->Start 
![](images/xamp-setup6.png)

7. XAMPP Control Panel， Apache->Admin 開啟網頁，建議點選英文版本

8. 點選網頁上 Security， [allowed only for localhost]那行的連結，修改 MySQL 密碼
![](images/xamp-setup7.png)
![](images/xamp-setup8.png)