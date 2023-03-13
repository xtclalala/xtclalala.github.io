---
title: "ARP"
date: 2023-03-12T19:41:13+08:00
draft: false

toc: true
tags: ["protocol"]
categories: ["network"]
series: ["归档"]
---

## 什么是ARP？
ARP(Address Resolution Protocol，地址解析协议)可以将IP解析成对应的Mac地址。

## ARP报文格式
<table>
    <tr>
        <td>目的Mac</td> 
        <td rowspan="3">以太网首部</td> 
        <td>48bit</td>
        <td>发送arp请求报文时，该字段为广播的Mac地址0xffff-ffff-ffff</td> 
   </tr>
    <tr>
        <td>源Mac</td> 
        <td>48bit</td>
        <td>源Mac</td> 
   </tr>
    <tr>
        <td>帧类型</td> 
        <td>16bit</td>
        <td>arp请求和应答报文，该字段为0x0806</td> 
   </tr>
    <tr>
        <td>硬件类型</td> 
        <td rowspan="9" >ARP</td>  
        <td>16bit</td>
        <td>以太网类型，该字段为1</td> 
   </tr>
    <tr>
        <td>协议类型</td> 
        <td>16bit</td>
        <td>发送方要映射的协议地址类型，对于IP地址，该字段的值为0x0800</td> 
   </tr>
    <tr>
        <td>硬件地址长度</td> 
        <td>8bit</td>
        <td>arp请求或应答报文，该字段为6</td> 
   </tr>
    <tr>
        <td>协议地址长度</td> 
        <td>8bit</td>
        <td>arp请求或应答报文，该字段为4</td> 
   </tr>
    <tr>
        <td>OP</td> 
        <td>16bit</td>
        <td>arp操作类型，1为arp请求报文，2为应答报文</td> 
   </tr>
    <tr>
        <td>源Mac</td> 
        <td>48bit</td>
        <td>Mac地址和以太网帧的源Mac地址相同</td> 
   </tr>
    <tr>
        <td>源IP</td> 
        <td>32bit</td>
        <td>源IP</td> 
   </tr>
    <tr>
        <td>目的Mac</td> 
        <td>48bit</td>
        <td>发送arp请求报文，该字段为0x0000-0000-0000</td> 
   </tr>
    <tr> 
        <td>目的IP</td>
        <td>32bit</td> 
        <td>目的IP</td> 
   </tr>
</table>

## ARP可以做什么？
1. 利用arp可以对当前网段进行设备嗅探。
