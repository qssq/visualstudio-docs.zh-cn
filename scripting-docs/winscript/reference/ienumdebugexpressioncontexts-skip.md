---
title: "IEnumDebugExpressionContexts::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExpressionContexts.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugExpressionContexts::Skip"
ms.assetid: 3498cbb5-8581-4dcd-b016-e86b049c7831
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExpressionContexts::Skip
跳过枚举序列中指定数目的段。  
  
## 语法  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### 参数  
 `celt`  
 \[in\]段的数字在跳过的枚举序列的。  
  
## 返回值  
 该方法返回 `HRESULT`。  可能的值包括，但是，并不限于，这些下表中。  
  
|值|说明|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 备注  
 此方法跳过段指定数目的枚举序列的。  
  
## 请参阅  
 [IEnumDebugExpressionContexts 接口](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)