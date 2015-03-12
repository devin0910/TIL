### Redis协议

 - 简单字符串：“+”
 - 错误： “-”
 - 整型： “：”
 - 字符串组： “$"
 - 数组："*"

简单字符串：
首先是个”+“号，接着是一串不能包含CR或LR字符的字符串，以CRLR（"\r\r"）结尾
非二进制安全的
”+OK\r\r"

错误信息：
"-Error message\r\n"
Error 为错误类型
message 为错误信息（空格隔开）

整型(signed 64 bit)：
“：0\r\n" 
also extensively used in order to return true or false
commands:
SETNX, DEL, EXISTS, INCR, INCRBY, DECR, DECRBY, DBSIZE, LASTSAVE, RENAMENX, MOVE, LLEN, SADD, SREM, SISMEMBER, SCARD.

字符串组：（二进制安全，最大长度512M）
"$6\r\nfoobar\r\n"
字符串的长度 + "\r\n" + 实际字符串 + "\r\n"
空字符串： "$0\r\n\r\n"
Null Bulk String: "$-1\r\n"

数组：
”×“ + 数组长度 + "\r\n" + 数组中各个元素的RESP类型

空数组： ”×0\r\n"
两个字符串组：
"*2\r\n$3\r\nfoo\r\n$3\r\nbar\r\n"
三个整数：
"*3\r\n:1\r\n:2\r\n:3\r\n"

发送命令：
eg: SET key value
"*3\r\n$3\r\nSET\r\n$3\r\nkey\r\n$5\r\nvalue\r\n"
Inline command:
telnet session: SET key value (space-separated)