# Lampiao  
  
感覺1898超級可疑  
![](images/zO3GEBC.png)  
  
掃一下是HTTP Server  
![](images/F3X8W8D.png)  
  
80好酷 感覺進入點可能不是這邊  
![](images/Qj1zuDe.png)  
  
1898開著Drupal 7 利用這個資訊去找Exploit可以找到一個  
![](images/DxnMVVH.png)  
  
![](images/dRAqdaY.png)  
  
把它載下來直接run就拿到initial shell了  
![](images/D6NjQFo.png)  
  
#### 橫向提權  
  
跑linPEAS可以看到一個密碼 裡面有一個叫tiago的使用者 直接su就變成他了`tiago:Virgulino`  
![](images/JzQ36bv.png)  
  
![](images/SDeL2by.png)  
  
#### 垂直提權  
  
跑linPEAS可以看到是易受攻擊的Kernel 用searchsploit可以找到一大坨exploit  
![](images/Ld3FT6f.png)  
  
![](images/MxTwGjs.png)  
  
載下來直接編譯的話會噴錯 改PATH可以解決 但還是噴錯  
`export PATH=/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin`  
![](images/tiGPC1o.png)  
  
![](images/VGtobzV.png)  
  
最後把清單上的exploit都戳過 但都爛掉 最後找到一個另一版的linux exploit suggester 翻到一堆exploit  
https://github.com/mzet-/linux-exploit-suggester  
![](images/Ez2jGtU.png)  
  
![](images/bZFSAvb.png)  
  
最後用了dirtycow 2的ext-url exploit 編譯以後執行就成功root了  
![](images/yqEXgMQ.png)  
  
![](images/VN1IBok.png)  
  
#### Proof  
  
local.txt  
`569a509bad162e12796cc5d58b4deffd`  
![](images/vFlQnuC.png)  
  
proof.txt  
`137a048a9cb1e0d72e7087ad6ef54e31`  
![](images/c8CVGDM.png)