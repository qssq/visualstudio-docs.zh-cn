---
title: 如何：在 Visual Studio 的负载测试结果中创建自定义关系图 | Microsoft Docs
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load test results graphs, creating
- load test results graphs
ms.assetid: 17fcafce-76f9-4411-9389-6e5376eab236
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 740e9c9c04874f2510bf7b1c8992e28d62787ce8
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-create-custom-graphs-in-load-test-results"></a>如何：在负载测试结果中创建自定义关系图

可以设计用于显示有关负载测试结果的特定信息的关系图。 可以通过指定关系图将显示的负载测试计数器来设计自定义关系图。

 可以在运行负载测试时执行以下过程，也可在负载测试完成运行之后执行。

## <a name="to-create-a-custom-load-test-results-graph"></a>创建自定义负载测试结果关系图

1.  在“负载测试”工具栏上选择“添加新关系图”。

     \- 或 -

     在负载测试分析器上，右键单击“计数器”面板或右键单击关系图，然后选择“添加关系图”。

     随即显示“请输入关系图名称”对话框。

2.  在“关系图名称”下，键入关系图的名称，然后选择“确定”。

     新关系图将出现在负载测试分析器中。 新关系图还会出现在当前所选的关系图面板中，并替换该面板中原来显示的关系图。

3.  通过添加计数器来自定义新的关系图。 有关详细信息，请参阅[如何：在关系图上添加和删除计数器](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)。

## <a name="see-also"></a>请参阅

- [在关系图视图中分析负载测试结果](../test/analyze-load-test-results-in-the-graphs-view.md)
- [如何：在关系图上添加和删除计数器](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)