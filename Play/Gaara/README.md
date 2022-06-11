### Gaara

怎麼PG都是打Web
![](images/ZH9kac1.png)

不知道為什麼都枚舉不到路徑 直到用了directory-list-2.3-big.txt這個wordlist才找到
![](images/gEQw0Ft.png)

拉到最下面可以看到三條路徑 打開以後都是一串長到吐的文章 到這邊線索就斷了 直到看了Write up才知道要在這堆文章中翻出一行encode過的文字 (這什麼垃圾設計==
![](images/JrdO7EO.png)

![](images/DgmHbFc.png)

`curl http://192.168.203.142/iamGaara | grep -oE '\w+' | sort -u -f | more`
![](images/PtKwETQ.png)

拿CyberChef用base58解可以噴出一串憑證
![](images/3D1OJC2.png)

但這個憑證是無效的 不過至少我們拿到了username 用hydra炸一下就噴出來了
![](images/FZdHCBY.png)

成功登入
![](images/OHy115J.png)

#### 提權

進去以後跑linPEAS 可以看到gdb有SUID 直接查GTFOBins就能翻到生shell的指令 輸入就直接root了
![](images/KwGSB84.png)

![](images/uUbDHwI.png)

#### Proof

local.txt
`4e63c838b940d3a9476e7acde72b409f`
![](images/LTbyi0A.png)

proof.txt
`0aeda9dd270f8b39e99c463c1b0df05f`
![](images/ls2Ecdo.png)