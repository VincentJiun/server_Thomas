# Django Project - Thomas

## Django 介紹
    作業系統    webserver       資料庫          程式
    Windows    IIS(非常爛)       MSSQL         ASP.NET
                Apache           MySQL         PHP
                Django           MySQL(首選)   Python

    Linus       Apache           MySQL         PHP
    (ubuntu)    Nginx            MSSQL      
                Django           MySQL         python

> MSSQL : 正式版要錢

    - MSSQL Express : 免費 但有 10G 容量限制
    - MySQL : 免費 無限制   (甲骨文 Orac甲骨文 Oracle)
    - MariaDB : 免費 無限制 準備接手 MySQL

## 專案使用語言撰寫
1. Django : 架設(後端)
2. heml + CSS + JavaScript : 前端
3. 全端 = 前端 + 後端
4. 後端網頁撰寫 : 表單、template ......

### 補充
> 常用 DOS 指令
- c: -> 切換磁碟機
- cd (folder-name) -> 進入資料夾
- dir -> 列出檔案及目錄

## 學習目標
- 網路概論
- 後端資料傳輸 (randen)

## 環境設置

### 虛擬環境
> python -m venv (env-Name)

### 啟動虛擬環境
> (env-name)\Scripts\activate

### 安裝系統級 Django(非虛擬環境)
> pip install django
- 不要進入專案目錄(啟動虛擬環境) -> 才是安裝系統級套件

### Linux 環境設置指令
- sudo : 切換最高權限, 使用root帳號
> sudo apt-get install python3-django

> sudo apt-get install python3-venv

> cd (project-folder)

> python -m venv (env-Name) -> 建立虛擬環境

> ./(env-name)/bin/

## 開始 Django Project

### 啟動專案
> django-admin startproject (Project-Name) .        
- 後面如果有 . -> 代表該目錄資料夾為專案目錄資料夾 (不會再裡面新增一個 Project-Name) 的專案資料夾

### 啟動應用程式(App)
> python manage.py startapp (App-Name)

> setting.py 檔案內
- INSTALLED_APPS = ['APP-Name'] -> 加入 App 至專案

### 執行 Django Project (啟動伺服器)
> python manage.py runserver 0.0.0.0:7000
- 0.0.0.0 : 代表所有IP都可以連線進入此專案
- :7000 : 執行 Port
- 執行完 -> 瀏覽器 http://localhost:7000 即可進入專案伺服器
- 9000 port 不要執行 -> 9000 port 為Nginx 連接PHP主要Port

> 電腦啟動後 自動啟動 Django Server
1. 開始/Windows 系統管理工具/工作排程器
2. 建立基本工作 -> 輸入:名稱 -> 觸發程序:電腦啟動時執行 -> 動作:啟動程式 
3. 輸入 程式或指令碼: 瀏覽 專案目錄\env-name\Scripts\python.exe
4. 新增 引數 : 專案目錄\manage.py runserver 0.0.0.0:7000
5. 完成後在主畫面上找到剛才的排程 (點兩下 進入修改)
6. 選擇 不論使用者登入與否均執行
- 網路上常教學 : shell:startup 執行 -> 這是錯的，因為需要登入才會執行。

## 網路概論 (建立 網域)

### 查詢IP
1. 查詢 虛擬ip : cmd輸入 ipconfig
2. 查詢 真實ip : chrome -> https://www.whatismyip.com.tw/tw/

### 申請網域
- no-ip : https://www.noip.com/ (免費網域)
- Godaddy : https://tw.godaddy.com/ (付費網域)
- 回報真實ip (以 no-ip為例) : Dynamic DNS/Dynamic Update Client : DUC
- 測試 : cmd輸入 ping hostname.申請網域 -> 有出現 ip 位置就代表成功

### 設定 ADSL/ip 分享器 
1. chrome 輸入 : http://192.168.1.1 (ip config 預設閘道)
2. 輸入帳號/密碼

### Port (埠)
- 好比機場的登機閘門
- 電腦的port 共有 65536
- 常用port -> 80:http , mysql:3306, mssql:1433, 監視器:3777, ftp:21, ssh:22

### IP
- x.x.x.x:由四組數字組成, 稱為 IPv4, 每組數字介於 0~255 之間
- 256*256*256*256 = 2^32
- x.x.x.x.x.x: IPv6 -> 常用於 IoT(物聯網)  AIoT = AI + IoT
- 虛擬IP:
    
    - Class A : 10.x.x.x 
    - Class B : 172.16.x.x ~ 172.31.x.x
    - Class C : 192.168.x.x
    > 虛擬IP是不能上網的
- 真實IP:

    - 非上述IP才可以上網
    > 真正在上網的並不是電腦，而是數據機(兩張網卡) -> 一張網卡:對外連線(真實IP)/另一張網卡:數據機與電腦溝通(虛擬IP 跳轉)

### 浮動與固定 IP
- 每次開機取得的IP位置都不一樣，稱 浮動IP
- 每次開機取得的IP位置一樣，稱 固定IP
> 真實IP有分為固定以及浮動IP -> YES

> 虛擬IP有分為固定以及浮動IP -> YES

- 中華電信(ISP業者)的固定IP，並非一輩子不變

### 預設閘道器
- 就是ADSL 或 IP分享器的IP
- 每台電腦的IP，前三組號碼必須跟預設閘道器一樣 (可以透過修改 子網路遮罩 來變更) -> 255.255.255.0
- 255:規定必須一樣 0:規定必須不一樣
- 查電腦本身的ip: ipconfig

### 變更虛擬 IP
- 網際網路存取/網路和網際網路設定/變更介面卡設定/乙太網路卡(右鍵)/內容/(TCP/IPv4)
- IP : 192.168.x.2
- 子網路遮罩 : ipconfig 查詢
- 預設閘道器 : ipconfig 查詢
- 慣用dns : 168.95.1.1 
- 其他dns : 168.95.192.1 (中華電信 DNS) : 速度穩定

### DNS/DDNS:
- DNS : Domain Name Server 網域名稱伺服器 : 將網域轉換成IP，IP依變更，通常需要一二小時才會更新。(不但要錢 而且更新速度慢)
- DDNS : Dynamic DNS 動態網域名稱伺服器 : IP改變了，會立即回報服務商並更改。

### ADSL 設定
- Chrome : http://預設閘道器 
    
    輸入 帳號/密碼 (以中華電信 亞旭RTF8270W 為例: 帳號:cht 密碼:207wxxxx, (xxxx)後面四碼為機上盒MAC貼紙的最後四碼)
- Routed : PPPoE Setting 帳號/密碼在中華電信密碼卡上
- 更改預設閘道器: IP Interface
- Port Forwarding : 
    - Interface : WAN-PPPoE
    - 通訊協議 : TCP
    - 遠端IP位置 : 0.0.0.0 (任何IP 都可以連近來)
    - 外部端口 : port
    - 區域網路IP位置 : 伺服器電腦 IP
    - 內部端口 : 伺服器電腦 port
- NAT Lookback : 外部可以連進伺服器電腦，但自己無法連自己的網站
    - Enable 必須打勾 (才能解決)
- DNS/ Dynamic DNS
    - State : Enable
    - Provider : No-IP (選擇服務商)
    - Host Name 
    - Interface : WAN-PPPoE
    - User Name (Account): 服務商 登入帳號
    - Password : 服務商登入密碼
> DMZ : 是把所有的 Port 指向你的電腦，很容易被入侵，千萬不能開

### IP分享器 設定
- Chrome : http://預設閘道器 

    登入 IP分享器

- 外部網路:
    - WAN 連線類型 : 一定要用 PPPoE
    - 輸入 PPPoE 帳號密碼

- 區域網路:
    - 內網位置設定 : 
        - IP 位址 : 預設閘道器
        - 子網路遮罩
    - DHCP 伺服器:
        - IP Pool 起始位址/結束位址 : 外部連線進入伺服器的起始/結束位址 (避免 伺服器IP(固定IP) 位置衝突)

- 外部網路:
    - 虛擬伺服器 : 
        - 服務名稱 : (選填)
        - 通訊協定 : TCP
        - 外部通訊埠 : Port
        - 內部通訊埠 : Port
        - 本地IP 位址 : 伺服器電腦 IP
    - DDNS :
        - 伺服器 : (選擇服務商)

### 設定防火牆
- Windows 安全性 / 防火牆與網路保護/ 進階設定
    - 輸入規則/ 新增規則
        - 規則類型 : 連接埠
        - 通訊協定及連接埠 : 本機連接埠(內部port)
        - 動作 : 允許連線
        - 名稱 : 輸入名稱

### Django 設定
> Django 預設是不允許外埠連入
- 專案目錄/setting.py
    - ALLOWED_HOSTS = ['*']

## 模板 (Templates)

### MVC架構
> Model/ View/ Controller

> 一個網頁app可能會由多個python 檔案組合而成
1. python manage.py startapp (app-name) -> 會在app資料夾中生成 admin/apps/models/tests/views.py 檔，其中 views.py 是網頁app 主要撰寫的 py檔
2. 編寫 views.py
3. 編寫 模板.html
4. 修改 urls.py : path('xxxx/', views.def-name)

### 模板設定
> settings.py 檔案內
- TEMPLATES -> 'DIRS': [os.path.join(BASE_DIR, 'templates').replace('\\', '/')],

> 編寫 views.py

> 設定 urls.py

### 靜態文件 (static)
- 由網路連結(urls.py) 經由(views.py)計算執行後，將資料送到模板，最後將結果顯示至客戶端

- 直接顯示 .html 檔 (方法):
    
    1. 專案目錄下 建立一個 static 資料夾
    2. /settings.py
        - STATIC_URL = 'static/'
        - STATICFILES_DIRS = [os.path.join(BASE_DIR, 'static')]
    3. 開啟瀏覽器
        - http://localhost:8000/static/靜態網頁.html

## 表單 (Form)

### method
- get : web-url/?參數一=xxxx&參數二=xxxx -> 表單內參數會顯示在網址列上
- post : 開啟另一條連線傳送參數，所以不會在網址列上顯示。

### csrf
- 先關閉"跨站請求攻擊"的保護
    - {% csrf_token %}

## 資料庫

### MySQL安裝
1. 

### MySQL備份
> mysqldump -u 帳號 -p --routines 資料庫名 > outputfile.sql

### MySQL還原
> mysql -u 帳號 -p --default-character-set=utf8 資料庫名 < outputfile.sql
- 資料庫語系必須為 utf8/utf8_unicode_ci.
