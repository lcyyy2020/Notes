## 说说 TCP 挥手过程？

! [](./说说TCP挥手过程.md)

1. 客户端调用 close 方法，执行「主动关闭」，会发送一个 FIN 报文给服务端（从这以后客户端不能再发送数据给服务端），客户端进入 FIN-WAIT-1 状态。

> 主动发起关闭的一方称为「主动关闭方」，另外一段称为「被动关闭方」。

2. 服务端收到 FIN 包以后回复确认 ACK 报文给客户端，服务端进入 CLOSE_WAIT，客户端收到 ACK 以后进入 FIN-WAIT-2 状态。

3. 服务端也没有数据要发送了，发送 FIN 报文给客户端，然后进入 LAST-ACK 状态，等待客户端的 ACK。

4. 客户端收到服务端的 FIN 报文以后，回复 ACK 报文用来确认第三步里的 FIN 报文，进入 TIME_WAIT 状态，等待 2 个 MSL 以后进入 CLOSED 状态。服务端收到 ACK 以后进入 CLOSED 状态。
