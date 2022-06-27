# FunboxRookie  
  
掃一下 感覺是要從FTP上傳東西再到網站拿webshell(?  
![](images/HtFoTSJ.png)  
  
用anonymous連上去 沒有寫入的權限  
![](images/SPR69EA.png)  
  
但拿FTP的版本去找exploit可以翻到有RCE的  
![](images/tPs652d.png)  
  
但可惜不能用  
![](images/fjpWh6P.png)  
  
嘗試把裡面的zip載下來看 發現可能是進入點 id_rsa包在有密碼的壓縮檔內  
![](images/Wp0Bn8q.png)  
  
把所有的zip下載下來用zip2john取hash 發現有幾個是可以爆出密碼的  
![](images/1rEU2fT.png)  
![](images/3InYMdq.png)  
  
cathrine連不上去  
![](images/8AQp50u.png)  
  
tom可以 但發現是在一個被限制的shell內  
![](images/VpdQvz0.png)  
  
![](images/dbTJxTL.png)  
  
#### 提權  
  
發現.mysql_history有點肥  
![](images/zf45Oo8.png)  
  
貓他可以看到好像是tom的憑證的奇怪東西(?  
![](images/nHWVj2h.png)  
  
嘗試sudo 發現去掉040可以過驗證 而且sudo還能ALL 直接`sudo su`就是root了  
![](images/4hjB4Y5.png)  
  
#### Proof  
  
local.txt  
`63e4802a0c92e631b4755db78602e22a`  
![](images/uHYnPWC.png)  
  
proof.txt  
`f720af6ecf3dbdb082e2bef3614a6262`  
![](images/8H8BmAO.png)  
