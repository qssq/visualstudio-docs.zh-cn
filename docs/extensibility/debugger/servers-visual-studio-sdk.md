---
title: 服务器 (Visual Studio SDK) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 871eeb59832c640ede32e0fcd188941605c4afcb
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276648"
---
# <a name="servers-visual-studio-sdk"></a>服务器 (Visual Studio SDK)
在调试器体系结构中， *server*:  
  
-   是一个容器的端口和端口提供程序和与会话调试管理器 (SDM) 和调试引擎进行通信的端口和端口提供程序。  
  
-   可以按名称、 标识本身和枚举其端口和端口提供程序。  
  
-   为由[IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)接口，仅实现由 Visual Studio （在 Visual Studio 运行的每个实例的服务器的一个实例）。  
  
## <a name="see-also"></a>请参阅  
 [端口](../../extensibility/debugger/ports.md)   
 [端口提供程序](../../extensibility/debugger/port-suppliers.md)   
 [调试器概念](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)