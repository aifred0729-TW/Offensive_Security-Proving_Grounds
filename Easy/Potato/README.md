應該是打Web
![](images/A7Ti4vN.png)

隨便掃一下路徑可以發現有奇怪的東西
![](images/IZRw2gK.png)

admin就單純的後台頁面 但弱憑證跟SQL Injection都不能用
![](images/O6HwbnY.png)

在logs裡面有一些log 但幾乎都是沒什麼用的資訊
![](images/tig5nwq.png)

![](images/pyuDvKL.png)

![](images/x5ZHT5Y.png)

全Port的掃瞄結果出來了 可以看到有服務開在2112
![](images/J4U1tk5.png)

是ProFTPD 而且可以anonymous登入
![](images/2TComRF.png)

把index.php.bak載下來 貓他可以看到php的內容
![](images/sd7TTB9.png)

![](images/Ph9gt2A.png)

觀察一下 發現應該可以把password改成array來繞過登入
因為`strcmp(array(), "meow")`會等於NULL 所以這樣可以讓第二個判斷式=0

用Burp把封包攔下來 然後把password改成array 送出後就發現登入成功了
![](images/zDWRx7g.png)

![](images/vVM2vka.png)

到管理介面裡面隨便逛了一下 發現Logs的頁面有LFI的漏洞 只要改一下送出封包的內容就能觸發

![](images/rF5UGyB.png)

![](images/Ucc21uI.png)

在passwd的最下面看到一個有hash的使用者 拖回來用john炸一下就拿到憑證了

![](images/hAd50oR.png)

![](images/FxBJ0z0.png)

可以直接登入
![](images/HLqE3aq.png)

#### 提權

`sudo -l`可以看到一個奇怪的檔案 可以call到notes裡面的東西 看起來會直接執行對應的執行檔
![](images/vx0YfkZ.png)

![](images/s5KqzQb.png)

![](images/QmrqSXY.png)

因為他後面是星號 所以可以隨便加東西進去 直接在/tmp下塞一個reverse shell讓他執行就好了
![](images/9imCbch.png)

#### Proof

local.txt
`b57f9e8f2e09219fc0e9149439b0416f`
![](images/CtmlcC2.png)

proof.txt
`85056f8e37b28a3bc37fe1542463e698`
![](images/qq3gPSh.png)