---
title: 部署 64 位应用程序的必备组件 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], 64-bit
- 64-bit [Visual Studio]
- 64-bit programming [Visual Studio]
- 64-bit applications [Visual Studio]
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 10a5883e655fc5ee8a37bbe61f531b6b266ebb55
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281881"
---
# <a name="deploy-prerequisites-for-64-bit-applications"></a>部署 64 位应用程序的先决条件
ClickOnce 部署支持 64 位平台上的应用程序安装。 目标平台是**x86**对于 32 位平台， **x64**的计算机支持 AMD64 和 EM64T 指令集，并**Itanium**为 64 位 Itanium 处理器。  
  
## <a name="prerequisites"></a>系统必备  
 下表列出了可用作 64 位应用程序安装的系统必备组件的可再发行组件。  
  
 如果选择不具有 64 位组件的系统必备组件，则可能会看到一条警告，该警告声明选择的程序包不能用于 64 位平台。  
  
|可再发行组件|x64 支持|IA64 支持|  
|---------------------|-----------------|------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|是|否|  
|Visual C++ 2010 运行库 (IA64)|否|是|  
|Visual C++ 2010 运行库 (x64)|是|否|  
|Microsoft .NET Framework 4（x86 和 x64）|是||  
|Microsoft .NET Framework 4 Client Profil（x86 和 x64）|是||  
  
## <a name="see-also"></a>请参阅  
 [部署应用程序、 服务和组件](../deployment/deploying-applications-services-and-components.md)   
 [如何： 与 ClickOnce 应用程序安装的必备组件](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [64 位应用程序](/dotnet/framework/64-bit-apps)