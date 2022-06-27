### FunboxEasy  
  
又是Web  
![](images/qV0Caq6.png)  
  
掃了一下路徑 發現有幾條奇怪的東西 對secret掃下去以後可以看到更多奇怪的東西  
![](images/gX7Ozlf.png)  
  
![](images/ETB7jGp.png)  
  
看了一下 都沒有什麼用 到store裡面可以用`admin:admin`登入管理介面  
![](images/rTONJAk.png)  
  
但不知道怎麼RCE 查了一下有沒有exploit 發現一個  
![](images/GZONiBh.png)  
  
運行以後發現能用 加一個reverse shell下去就直接RCE了  
![](images/QfmsH0n.png)  
  
#### 橫向提權  
  
在`/home/tony`下可以發現一個叫`password.txt`的檔案 打開後發現是一坨憑證 可以用這個憑證`su tony`  
![](images/Q76WMrn.png)  
  
![](images/jZ52PDG.png)  
  
#### 垂直提權  
  
`sudo -l`看到一堆東西 這根本隨便提 直接`sudo /usr/bin/pkexec /bin/sh`就是root了  
![](images/wLq7QjU.png)  
  
![](images/IsOxRws.png)  
  
#### Proof  
  
local.txt  
`74395882813e93aeb6a422e6dfb0618b`  
![](images/PjrCJ4r.png)  
  
proof.txt  
`93e8d166b41519f8859e66a83d7d497a`  
![](images/tH3mDpw.png)