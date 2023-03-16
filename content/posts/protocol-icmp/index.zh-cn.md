---
title: "Icmp"
keywords:
- icmp
- 协议
- 报文格式
- 工具
- ping
description : "Icmp协议的报文格式，可以做什么"
date: 2023-03-14T15:30:58+08:00
draft: true
---

# 什么是ICMP？

因特网控制报文协议ICMP(Internet Control Message Protocol)是一个差错报文协议，是TCP/IP协议簇中的重要子协议，被IP或TCP/UDP层使用，属于网络协议。主要用于在主机和路由器之间传递控制消息，用于报告主机是否可达、路由是否可用。对于收集各种网络信息、诊断和排除各种网络故障以及用户数据的传递具有至关重要的作用。

## 为什么需要ICMP？
数据传输过程中，IP提供尽力而为的服务，只做将数据包发送到目的主机的工作，并不对目的主机是否收到数据包进行验证，无法进行流量控制和差错控制。为了更有效的转发IP数据包和提高数据包交付成功的情况，可以使用ICMP。当数据包传输出现问题时，主机或设备向上层协议报告差错情况和提供有关异常情况，使上层协议可以利用自己的差错控制程序进行控制，从而保证服务质量。

## ICMP包头报文格式

> - ICMP差错报文不会产生差错报文，但ICMP查询报文会产生差错报文，防止ICMP出现无限产生和传递
> - 目的地址是广播地址或多播地址，一个网段的最后一个地址是广播地址
> - 源地址不能为零地址，环回地址，广播地址或多播地址

<table>
    <tr>
        <td>type</td>
        <td>8bit</td>
        <td>icmp消息类型</td>
    </tr>
    <tr>
        <td>code</td>
        <td>8bit</td>
        <td>icmp消息类型的子类型</td>
    </tr>
    <tr>
        <td>checksum</td>
        <td>16bit</td>
        <td>icmp报文校验和</td>
    </tr>
</table>

<table>
    <tr>
        <td>type</td>
        <td>code</td>
        <td>描述</td>
        <td>查询/差错</td>
    </tr>
    <tr>
        <td>0 echo 响应</td>
        <td>0</td>
        <td>echo 响应报文</td>
        <td>查询</td>
    </tr>
    <tr>
        <td rowspan="16">3 目的不可达</td>
        <td>0</td>
        <td>目标网络不可达</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>1</td>
        <td>目标主机不可达</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>2</td>
        <td>目标协议不可达</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>3</td>
        <td>目标端口不可达</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>4</td>
        <td>要求分段DF flag标志</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>5</td>
        <td>源路由失败</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>6</td>
        <td>未知的目标网络</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>7</td>
        <td>未知的目标主机</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>8</td>
        <td>源主机隔离</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>9</td>
        <td>禁止访问的网络</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>10</td>
        <td>禁止访问的主机</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>11</td>
        <td>对特定的TOS网络不可达</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>12</td>
        <td>对特定的TOS网络不可达</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>13</td>
        <td>由于过滤网络流量被禁止</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>14</td>
        <td>主机越权</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>15</td>
        <td>优先权终止生效</td>
        <td>差错</td>
    </tr>
    <tr>
        <td rowspan="4">5 重定向</td>
        <td>0</td>
        <td>重定向网络</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>1</td>
        <td>重定向主机</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>2</td>
        <td>基于TOS的网络重定向</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>3</td>
        <td>基于TOS的主机重定向</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>8 echo 请求</td>
        <td>0</td>
        <td>echo 请求</td>
        <td>查询</td>
    </tr>
    <tr>
        <td>9 路由器通知</td>
        <td>0</td>
        <td>路由通告</td>
        <td>查询</td>
    </tr>
    <tr>
        <td>10 路由器请求</td>
        <td>0</td>
        <td>路由器的发现、选择、请求</td>
        <td>查询</td>
    </tr>
    <tr>
        <td rowspan="2">11 ICMP超时</td>
        <td>0</td>
        <td>TLL超时报文</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>1</td>
        <td>分片重组超时报文</td>
        <td>差错</td>
    </tr>
    <tr>
        <td rowspan="3">12 参数问题</td>
        <td>0</td>
        <td>IP报首部参数错误</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>1</td>
        <td>丢失必要选项</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>2</td>
        <td>不支持长度</td>
        <td>差错</td>
    </tr>
    <tr>
        <td>13 时间戳请求</td>
        <td>0</td>
        <td>时间戳请求报文</td>
        <td>查询</td>
    </tr>
    <tr>
        <td>14 时间戳应答</td>
        <td>0</td>
        <td>时间戳应答报文</td>
        <td>查询</td>
    </tr>
    <tr>
        <td>15 信息请求</td>
        <td>0</td>
        <td>信息请求报文</td>
        <td>查询</td>
    </tr>
    <tr>
        <td>16 信息应答</td>
        <td>0</td>
        <td>信息应答报文</td>
        <td>查询</td>
    </tr>
</table>

## ICMP可以做什么？
### Ping
用于检测IPv4和IPv6网络设备的工具，通过ICMP的包头信息来确认

### 泛洪攻击
基于ICMP的泛洪攻击，攻击者在短时间内向目标设备发送大量ICMP虚假报文，导致目标设备忙于应付无用报文
##### 针对带宽的DOS攻击
攻击者发送伪造的ICMP请求报文，交换机、路由器等网络设备需要CPU响应无用报文，导致占用宽带和CPU资源
##### 端口扫描攻击
攻击者发送端口扫描报文，交换机需要回应大量的ICMP目的不可达报文，攻击者可以获取设备开启的端口
##### 针对主机的DOS攻击
在paylod中构造64KB导致内存分配错误，导致TCP/IP堆栈崩溃，致使被攻击主机宕机

### 攻击防范
##### 报文限速
ICMP报文限速，通过端口限速、VLAN限速、全局限速
##### 报文合法性检查
TLL为0，ICMP类型为15、16、17的报文，进行丢弃
##### 不响应不可达报文
直接丢弃端口不可达或网络不可达报文















