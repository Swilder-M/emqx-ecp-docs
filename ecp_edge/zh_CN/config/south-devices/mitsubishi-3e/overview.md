# Mitsubishi 3E

Mitsubishi 3E 插件用于通过以太网访问三菱的 QnA 兼容 PLC，包括 Q 系列（MC）、iQ-F 系列（SLMP）和 iQ-L 系列。Mitsubishi 3E 完全兼容 Mitsubishi SLMP 协议。

## 插件配置

|  参数      | 说明                       |
| -------- | -------------------------- |
| **PLC IP 地址** |  目标设备 IPv4 地址         |
| **PLC 端口** | 目标设备端口号，默认为 2000 |

## 点位配置

### 数据类型

* INT16
* UINT16
* INT32
* UINT32
* FLOAT
* DOUBLE
* BIT
* STRING

### 地址格式

> <span>AREA ADDRESS\[.BIT]\[.LEN\[H]\[L]]</span>

#### .BIT

只可用于**非 bit 类型区域**，表示读取指定地址的指定二进制位，二进制位索引区间为[0, 15]。

#### .LEN\[H]\[L]

当数据类型是 string 类型时，**.LEN** 表示的是字符串长度；可以选填 **H**和 **L** 表示两种字节顺序，默认的是 **H** 的字节顺序。

#### 区域地址

| 区域 |数据类型 | 属性  | 备注                           |
| ---- | --------- | ---------- | -------------------------------- |
| X    | bit       | 读/写 | 输入继电器  (Q/iQ-F)             |
| DX   | bit       | 读/写 | (Q/iQ-F)                         |
| Y    | bit       | 读/写 | 输出继电器 (Q/iQ-F)            |
| DY   | bit       | 读/写 | (Q/iQ-F)                         |
| B    | bit       | 读/写 | 链接继电器 (Q/iQ-F)              |
| SB   | bit       | 读/写 | 链接专用继电器               |
| M    | bit       | 读/写 | 内部继电器 (Q/iQ-F)          |
| SM   | bit       | 读/写 | 特殊寄存器 (Q/iQ-F)           |
| L    | bit       | 读/写 | 锁存器 (Q/iQ-F)             |
| F    | bit       | 读/写 | 信号器 (Q/iQ-F)             |
| V    | bit       | 读/写 | 边缘继电器 (Q/iQ-F)              |
| S    | bit       | 读/写 | (Q/iQ-F)                         |
| TS   | bit       | 读/写 | 定时器触点 (Q/iQ-F)           |
| TC   | bit       | 读/写 | 定时器线圈 (Q/iQ-F)              |
| SS   | bit       | 读/写 | (Q/iQ-F)                         |
| STS  | bit       | 读/写 | 保持定时器触点 (Q/iQ-F)    |
| SC   | bit       | 读/写 | (Q/iQ-F)                         |
| CS   | bit       | 读/写 | 计数器触点 (Q/iQ-F)         |
| CC   | bit       | 读/写 | 计数器线圈 (Q/iQ-F)            |
| TN   | 所有类型   | 读/写 | 定时器当前值 (Q/iQ-F)     |
| STN  | 所有类型   | 读/写 | 保持定时器 (Q/iQ-F)         |
| SN   | 所有类型   | 读/写 | (Q/iQ-F)                         |
| CN   | 所有类型   | 读/写 | 计数器当前值  (Q/iQ-F)  |
| D    | 所有类型   | 读/写 | 数据寄存器 (Q/iQ-F)           |
| DSH  | -- |       |                                  |
| DSL  | -- |      |                                  |
| SD   | 所有类型   | 读/写 | 专用寄存器 Specical register (Q/iQ-F)       |
| W    | 所有类型   | 读/写 | 链接寄存器 (Q/iQ-F)           |
| WSH  | -- |      |                                  |
| WSL  | -- |      |                                  |
| SW   | 所有类型   | 读/写 | 链接专用寄存器 (Q/iQ-F)   |
| R    | 所有类型   | 读/写 | 文件寄存器 (Q/iQ-F)           |
| ZR   | 所有类型   | 读/写 | 文件寄存器 File register (Q/iQ-F)           |
| RSH  | -- |  |                                  |
| ZRSH | -- |  |                                  |
| RSL  | -- |  |                                  |
| ZRSL | -- |  |                                  |
| Z    | 所有类型  | 读/写  | 索引寄存器 Index register (Q/iQ-F)          |

## 地址示例

| 地址   | 数据类型 | 说明 |
| ----- | ------- | ----- |
| X0    | bit     | X 区域，地址为 0    |
| X1    | bit     | X 区域，地址为 1    |
| Y0    | bit     | Y 区域，地址为 0    |
| Y1    | bit     | Y 区域，地址为 1    |
| D100  | int16   | D 区域，地址为 100  |
| D1000 | uint16  | D 区域，地址为 1000 |
| D200  | uint32  | D 区域，地址为 200  |
| D10   | float   | D 区域，地址为 10   |
| D20   | double  | D 区域，地址为 20   |
| D20.0 | bit | D 区域，地址为 20，第 0 位|
| D20.2 | bit | D 区域，地址为 20，第 2 位|
| D1002.16L | string  | D 区域，地址为 1002，字符串长度为 16，字节顺序为 L |
| D1003.16 | string  | D 区域，地址为 1003，字符串长度为 16，字节顺序为 H |