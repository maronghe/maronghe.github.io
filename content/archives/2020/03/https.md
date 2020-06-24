

``````
前端工程化
HTTP 2.0 HTTPs
``````





HTTP 1.0 1.1

1.1



// HTTPs = HTTP + SSL



HTTP 2.0

1. 首部压缩
2. 多路复用
3. 二进制分帧
4. 服务端推送



cookie  header  -》  20 

ok 2 byte

22  = 2 + 20 







​             http  1.1

client --------------------------- server 





























http -> tcp 

tcp 3 4   

1.0 短连接

1.1 长链接 connection = keep-alive



Connect 

1 - > 

  <-- 

  -> 

  <-

.. 

close



1.1 

header + cookie  20 

body = 2 

---> 占网络带宽 ->                       

2  / 22  





Header 压缩

---

2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 

-----



1. 首部压缩
2. 服务端推送
3. 





index.html 

index.js

index.css





2.0 

Index.html 
                <----         index.js 

​                <----         index.css 





![image-20200524113116006](/Users/logan/Library/Application Support/typora-user-images/image-20200524113116006.png)













http                                         server 

Client                                       Server 



data    ----- >      (data)  ---- >      data    





对称加密的秘钥 abc



data + **abc** -> 291j39hcfwqj        --------->     291j39hcfwqj ------>>>     291j39hcfwqj  + **abc** = > data    加密、解密









client ->   server 

server create           秘钥abc  -> 

  client             < ----    秘钥**abc**   ----  server 

非对称加密    

「 public  a 、  private a 」                             data +  public a  => 2n31fuuqn1nf 

2n31fuuqn1nf    + private a  --->  data 



abc             ——》 **abc**       -————》   abc                  非对称加密 







tcp 消耗内存  2K    4G        

N Request - > N tcp 

-------------------------

-------------------------

-------------------------

-------------------------

-------------------------

1 tcp  ->  M  request 







TODO

http 1.0 1.1有证书么？





