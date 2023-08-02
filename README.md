# Deduce-public-key-from-signature

#实验名称

ECDSA

#实验简介

report on the application of this deduce technique in Ethereum with ECDSA

#姓名

王晖

202100141110

githubID：jokerduck

#实验截图


#密钥产生
每个签名者需要产生一个密钥对，包括一个私钥和一个公钥。签名者，假设是Bob，通过以下步骤产生上述两个密钥：

1.选择随机整数d，d在1到n-1之间

2.计算Q=dG，得到一个曲线上的解点。


3.Bob的公钥是Q，私钥是d
#签名产生
1、选择一条椭圆曲线Ep(a,b)，和基点G；

2、选择私有密钥k（k<n，n为G的阶），利用基点G计算公开密钥K=kG；

3、产生一个随机整数r（r<n），计算点R=rG；

4、将原数据和点R的坐标值x,y作为参数，计算SHA1做为hash，即Hash=SHA1(原数据,x,y)；

5、计算s≡r - Hash * k (mod n)

6、r和s做为签名值，如果r和s其中一个为0，重新从第3步开始执行


#签名验证
1、接受方在收到消息(m)和签名值(r,s)后，进行以下运算

2、计算：sG+H(m)P=(x1,y1), r1≡ x1 mod p。

3、验证等式：r1 ≡ r mod p。

4、如果等式成立，接受签名，否则签名无效。

![image](https://user-images.githubusercontent.com/75195549/181193670-593fd30b-66fa-4338-bba2-856781fe89af.png)


代码运行结果：

<img width="254" alt="屏幕截图 2023-07-07 005959" src="https://github.com/jokerduck/Deduce-public-key-from-signature/assets/130890730/66f694ba-c8f7-40dd-a390-15b4776c12dc">
