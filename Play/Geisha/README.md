# Geisha

掃出來感覺兔子洞很多
![](images/ZP5ewLL.png)

枚舉了一段時間後在7125翻到一個`/passwd` 載下來可以看到全部的使用者
![](images/iXRojzZ.png)

![](images/s065Vp4.png)

裡面有一個使用者 直接拿hydra爆密碼出來`geisha:letmein`
![](images/f8THy2g.png)

![](images/RcczCeP.png)

![](images/9ZWXHUs.png)

#### 提權

跑linPEAS可以看到SUID有base32
![](images/lWQHdiA.png)

到GTFOBins查base32可以看到能任意讀檔 可以讀root的id_rsa
![](images/Cs779yw.png)

![](images/JNrtEGi.png)

`chmod 600 id_rsa`以後可以直接連上去
![](images/GiCtOPL.png)

#### Proof

local.txt
`005adc32bd20cd3ac5ce49415e793197`
![](images/j49Hrol.png)

proof.txt
`7603b6bc4373f6944a68b13c5642d4ba`
![](images/pWVVig6.png)