---
title: "IDebugStackFrameSnifferEx 接口 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx 接口"
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx 接口
提供一种枚举元素已知的逻辑堆栈帧。  脚本引擎通常实现此接口。  进程内调试管理器使用此接口查找所有堆栈帧与特定线程。  
  
> [!NOTE]
>  此接口调用从线程相关的内部。  接口实现必须标识当前线程并返回适当的枚举器。  
  
 除了从 `IDebugStackFrameSniffer` 继承的方法之外，`IDebugStackFrameSnifferEx` 接口还公开下面的方法。  
  
## Vtable 顺序中的方法  
  
|方法|说明|  
|--------|--------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|返回堆栈帧的枚举数当前线程的。|