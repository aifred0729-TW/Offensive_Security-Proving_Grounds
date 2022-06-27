# SunsetNoontide

掃一下 只有IRC(?
![](images/g4ys67W.png)

好像有能用的exploit
![](images/gzK9hPu.png)

把檔案拖過來看一下原始碼 發現payload看起來只是在做Command Injection(?
![](images/jGIviGG.png)

直接nc上去丟Payload就RCE了
![](images/mJY4DQY.png)

## 提權

發現不管怎樣都提不了權 直到查了Write up發現是`root:root` 欸不是==
![](images/J3pmWRL.png)

## Proof

local.txt
`808632a00ce9a2645ac0eabb58dfc5c8`
![](images/0KcnB4J.png)

proof.txt
`4d3fdcd15faca0c06b5b4947df32c485`
![](images/syyA6u5.png)