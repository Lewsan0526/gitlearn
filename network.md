# 数据链路层
## 数据链路层通常会提供以下 3 种可能的服务：
>> 1.无确认的无连接服务。
>> 2.有确认的无连接服务。
>> 3.有确认的有连接服务。

## 比特流拆分
>> 1.字节计数法。每个帧第一字节标识帧的大小。以此确定帧的边界。
>> 2.字节填充的标志字节法。每个帧采用一些特殊的字节作为帧的开始和结束边界，这些字节称为标志字节FLAG（如同c语言里字符串的结尾0）。考虑到这些字节可能出现在数据中，需要额外的转义字节ESC，与c语言类似，构成【ESC FLAG】。当然，数据中遇到转义字节，也要进行转义【ESC ESC】。这些FLAG和ESC都属于额外填充的字节，故而帧大小不确定。
>> 3.比特填充的标志比特法。帧的划分可以在bit级完成。每个帧采用一个特殊字节，作为边界，它是01111110或0x7E标记。帧的大小是任意大小bit数，而不一定是8的倍数（不完整字节）。发送方在数据里每遇到5个连续的1，就填充一个0。如果数据中有标志字节01111110，会被填充后成为011111010。故而保证标志字节是唯一的，只能出现在边界。
>> 4.物理层编码违禁法。
