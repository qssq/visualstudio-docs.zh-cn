---
title: Message 任务 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0b61bf9def1ba37667302850527715eed1db4ff
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178327"
---
# <a name="message-task"></a>Message 任务
在生成期间记录消息。  
  
## <a name="parameters"></a>参数  
 下表描述了 `Message` 任务的参数。  
  
|参数|描述|  
|---------------|-----------------|  
|`Importance`|可选 `String` 参数。<br /><br /> 指定消息的重要性。 此参数的值可以是 `high`、`normal` 或 `low`。 默认值为 `normal`。|  
|`Text`|可选 `String` 参数。<br /><br /> 要记录的错误文本。|  
  
## <a name="remarks"></a>备注  
 通过 `Message` 任务，[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 项目可以在生成过程中的不同阶段将消息发送到记录器中。  
  
 如果 `Condition` 参数的计算结果为 `true`，则将会记录 `Text` 参数值，并继续执行生成。 如果 `Condition` 参数不存在，则将记录消息文本。 有关日志记录的详细信息，请参阅[获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)。  
  
 默认情况下，该消息将发送到 MSBuild 控制台记录器。 通过设置 <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> 参数可以对此进行更改。 记录器解释 `Importance` 参数。  
  
 除上面列出的参数外，此任务还从 <xref:Microsoft.Build.Tasks.TaskExtension> 类继承参数，后者自身继承自 <xref:Microsoft.Build.Utilities.Task> 类。 有关这些其他参数的列表及其说明的信息，请参阅 [TaskExtension 基类](../msbuild/taskextension-base-class.md)。  
  
## <a name="example"></a>示例  
 下面的代码示例将消息记录到所有已注册的记录器。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>请参阅  
 [任务参考](../msbuild/msbuild-task-reference.md)   
 [获取生成日志](../msbuild/obtaining-build-logs-with-msbuild.md)