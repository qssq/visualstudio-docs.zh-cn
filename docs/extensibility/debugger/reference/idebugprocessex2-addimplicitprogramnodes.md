---
title: IDebugProcessEx2::AddImplicitProgramNodes |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22f6cadaa88d6cc87ec70451d9da850cd49b7753
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
ms.locfileid: "31117015"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
此方法将添加指定每个调试引擎 (DE) 的程序节点。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>参数  
 `guidLaunchingEngine`  
 [in]`GUID`的 DE 是用于启动程序 （并且假定添加其自己的程序节点）。  
  
 `rgguidSpecificEngines`  
 [in]数组`GUID`s DEs 节点将添加的程序。  
  
 `celtSpecificEngines`  
 [in]数`GUID`中`rgguidSpecificEngines`数组。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回`S_OK`; 否则为返回错误代码。  
  
## <a name="remarks"></a>备注  
 [程序节点](../../../extensibility/debugger/program-nodes.md)中列出的每个 DE 将添加`rgguidSpecificEngines`-排除启动引擎 (在`guidLaunchingEngine`)，这假定它启动程序时添加自己的程序节点。  
  
## <a name="see-also"></a>另请参阅  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [程序节点](../../../extensibility/debugger/program-nodes.md)