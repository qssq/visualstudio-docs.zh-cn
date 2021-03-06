---
title: 工作流设计器-如何： 定义和使用活动委托
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 2039c1792a5e42c3181a01b10ff5bf271ea3bf2f
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755751"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>如何：在工作流设计器中定义和使用活动委托

.NET framework 4.5 包括全新的设计器<xref:System.Activities.Statements.InvokeDelegate>活动。 此设计器可用于将委托分配给从 <xref:System.Activities.ActivityDelegate> 派生的活动，例如 <xref:System.Activities.ActivityAction> 或 <xref:System.Activities.ActivityFunc%601>。

## <a name="define-an-activity-delegate"></a>定义活动委托

1.  在 Visual Studio 中，选择**文件** > **新建** > **项目**。

1. 在**新的项目**对话框中，选择**工作流**左边的类别，然后选择**工作流控制台应用程序**项目模板。 命名项目 （如果需要），然后单击**确定**。

   > [!NOTE]
   > 如果没有看到**工作流**类别中，首次安装**Windows Workflow Foundation**组件的 Visual Studio 2017。 有关详细说明，请参阅[安装 Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)。

2.  右键单击该项目中**解决方案资源管理器**，然后选择**添加** > **新项**。 选择**工作流**类别中，并选择**活动**项模板。 新活动命名**MyForEach.xaml** ，然后选择**确定**。

   该活动在工作流设计器中打开。

3.  在工作流设计器中，单击**自变量**选项卡。

4.  单击**创建参数**。 新的自变量命名**项**。

5.  在中**自变量类型**列中，选择 **[T] 的数组**。

6.  在类型浏览器中，选择**对象**，然后选择**确定**。

7.  单击**创建自变量**试。 新的自变量命名**正文**。 在中**方向**新的自变量，选择的列**属性**。

8.  在自变量类型列中，选择**浏览类型**

9. 在类型浏览器中，输入**ActivityAction**中**类型名称**字段。 选择**ActivityAction\<T >** 树视图中。 选择**对象**显示为指定类型的下拉列表中**ActivityAction\<对象 >** 的参数。

10. 拖动<xref:System.Activities.Statements.While>活动从**控制流**部分中的工具箱拖到设计器图面。

11. 选择<xref:System.Activities.Statements.While>活动，然后选择**变量**选项卡。

12. 选择**创建的变量**。 命名新变量**索引**。

13. 在中**变量类型**列中，选择**Int32**。 将保留**作用域**作为**虽然**，并**默认**列保留为空白。

14. 设置**条件**的属性<xref:System.Activities.Statements.While>活动**索引 < Items.Length;**。

15. 拖动<xref:System.Activities.Statements.InvokeDelegate>活动从**基元**部分中的工具箱拖到**正文**的<xref:System.Activities.Statements.While>活动。

16. 选择**正文**委托下拉列表中。

17. 在中**属性**网格<xref:System.Activities.Statements.InvokeDelegate>活动中，单击 **...** 按钮**委托参数**属性。

18. 在中**值**自变量名为的列**自变量**，输入**Items [Index]**。 单击**确定**以关闭**DelegateArguments**对话框。

19. 将 <xref:System.Activities.Statements.Assign> 活动拖到 <xref:System.Activities.Statements.InvokeDelegate> 活动的水平线下。 <xref:System.Activities.Statements.Assign>创建活动时，和一个<xref:System.Activities.Statements.Sequence>自动创建活动以包含中的两个活动**正文**一部分**myforeach**活动。 需要序列，因为**正文**部分只能包含单个活动。 自动创建新<xref:System.Activities.Statements.Sequence>活动是.NET Framework 4.5 的新功能。

20. 设置**到**的属性<xref:System.Activities.Statements.Assign>活动**索引**。 设置**值**的属性**分配**活动**索引 + 1**。

   自定义**myforeach**活动调用一次用于传递到它通过每个值的任意活动**项**具有作为活动的输入集合中的值的集合。

## <a name="use-the-custom-activity-in-a-workflow"></a>使用工作流中的自定义活动

1.  生成项目，通过按**Ctrl**+**Shift**+**B**。

2.  在中**解决方案资源管理器**，打开**Workflow1.xaml**在设计器中。

3.  拖动**myforeach**活动从工具箱拖到设计器图面。 此活动是在与项目同名的工具箱的部分。

4.  设置**项**的属性**myforeach**活动**new Object [] {1，"abc"}**。

5.  拖动<xref:System.Activities.Statements.WriteLine>活动从**基元**部分中的工具箱拖到**Delegate: Body**一部分**myforeach**活动。

6.  设置**文本**的属性<xref:System.Activities.Statements.WriteLine>活动**argument.tostring （)**。

当执行工作流时，控制台将显示以下输出：

**1**
**abc**