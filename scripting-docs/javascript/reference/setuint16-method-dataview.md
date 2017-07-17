---
title: "setUint16 方法 (DataView) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: bdf47cda-7fa5-4aaa-8aa2-8cf9a8d56cb3
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# setUint16 方法 (DataView)
在相对于视图开始处的指定字节偏移量位置处设置 Uint16 值。  没有对齐约束；可按任何偏移量设置多字节值。  
  
## 语法  
  
```  
dataView.setUint16(byteOffset, value, littleEndian);   
```  
  
## 参数  
 `testInt`  
 必需。  从该方法返回的 Uint16 值。  
  
 `value`  
 要设置的值。  
  
 `byteOffset`  
 缓冲区中将用于检索该值的位置。  
  
 `littleEndian`  
 可选。  如果为 false 或未定义，则应写入 big\-endian 值；否则应写入 little\-endian 值。  
  
## 备注  
 如果这些方法在视图末尾之外进行写入，则将引发异常。  
  
## 示例  
 下面的示例演示如何在 DataView 中设置第一个 Uint16。  
  
```javascript  
var req = new XMLHttpRequest();  
    req.open('GET', "http://www.example.com");  
    req.responseType = "arraybuffer";  
    req.send();  
  
    req.onreadystatechange = function () {  
        if (req.readyState === 4) {  
            var buffer = req.response;  
            var dataView = new DataView(buffer);  
            dataView.setUint16(0, 9);  
        }  
    }  
  
```  
  
## 要求  
 [!INCLUDE[jsv10](../../javascript/reference/includes/jsv10-md.md)]