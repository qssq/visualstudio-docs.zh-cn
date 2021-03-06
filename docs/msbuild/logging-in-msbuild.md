---
title: MSBuild 中的日志记录 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d866f0bc3181b6f338ec0b07df0ad5ff0e51010
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079156"
---
# <a name="logging-in-msbuild"></a>MSBuild 中的日志记录
通过日志记录可监视生成的进度。 日志记录捕获日志文件中的生成事件、消息、警告和错误。  
  
## <a name="in-this-section"></a>本节内容  
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)  
 描述 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 中日志记录的各个方面。  
  
 [生成记录器](../msbuild/build-loggers.md)  
 概述创建单处理器记录器所需的步骤。  
  
 [多处理器环境下的日志记录](../msbuild/logging-in-a-multi-processor-environment.md)  
 介绍日志记录在多处理器环境和两个多处理器日志记录模型下的工作原理。  
  
 [编写可识别多处理器的记录器](../msbuild/writing-multi-processor-aware-loggers.md)  
 概述如何创建多处理器感知记录器以及如何使用可配置的转发记录器。  
  
 [创建转发记录器](../msbuild/creating-forwarding-loggers.md)  
 概述如何创建自定义转发记录器。  
  
## <a name="see-also"></a>请参阅  
 [并行生成多个项目](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)  
 介绍如何通过并行运行多个项目来更快地生成它们。