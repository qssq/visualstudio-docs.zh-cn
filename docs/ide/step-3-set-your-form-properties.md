---
title: 步骤 3：设置窗体属性
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d4bf7645f3143aa9c8b7b73361f2ba454dbb323
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748499"
---
# <a name="step-3-set-your-form-properties"></a>步骤 3：设置窗体属性
接下来，使用“属性”窗口更改窗体的外观。

 ![视频链接](../data-tools/media/playvideo.gif)有关本主题的视频版本，请观看[教程 1：在 Visual Basic 中创建图片查看器 - 视频 1](http://go.microsoft.com/fwlink/?LinkId=205209) 或[教程 1：在 C# 中创建图片查看器 - 视频 1](http://go.microsoft.com/fwlink/?LinkId=205199)。 这些视频使用 Visual Studio 的早期版本，因此在一些菜单命令和其他用户界面元素上略有差异。 但是，概念和过程与当前版本的 Visual Studio 大同小异。

## <a name="to-set-your-form-properties"></a>设置窗体属性

1.  确保你查看的是 Windows 窗体设计器。 在 Visual Studio 集成开发环境 (IDE) 中，选择“Form1.cs [设计]”选项卡（或 Visual Basic 中的“Form1.vb [设计]”）。

2.  选择“Form1”窗体中的任意位置以将其选定。 查看“属性”窗口，该窗口此时应显示窗体的属性。 窗体具有各种属性。 例如，可以设置前景色和背景色、窗体顶部显示的标题文本、窗体的大小和其他属性。

    > [!NOTE]
    >  如果“属性”窗口未出现，请通过选择工具栏上的正方形“停止调试”按钮来停止程序或直接关闭窗口。 如果程序已停止，且仍未显示“属性”窗口，请在菜单栏上选择“视图” > 和“属性窗口”。

3.  选中窗体后，在“属性”窗口中找到“Text”属性。 根据列表排序的方式，您可能需要向下滚动。 选择“Text”，键入“图片查看器”，然后按 Enter。  此时，窗体的标题栏中将显示文本“图片查看器”，并且“属性”窗口的外观应与下图类似。

     ****![“属性”窗口](../ide/media/express_edittextproperty.png)
“属性”窗口

    > [!NOTE]
    >  可以通过“按分类顺序”视图或“字母顺序”视图对属性进行排序。 可通过使用“属性”窗口上的按钮在这两类视图之间进行切换。 在本教程中，通过“字母顺序”视图查找属性会更加轻松。

4.  返回“Windows 窗体设计器”。 选择窗体右下角的拖动手柄，此拖动手柄是位于窗体右下角的白色小正方形，如下所示。

     ![拖动图柄](../ide/media/express_bottomrt_drag.png)拖动图柄

     拖动手柄以调整窗体的大小，使其更宽且更高一些。

5.  查看“属性”窗口，你会发现“Size”属性已更改。 每次重设窗体的大小时，“Size”属性都会更改。 尝试拖动窗体的手柄以将其大小调整为大约 550 x 350（无需精确），这个大小应适合于此项目。 或者，可以直接在“Size”属性中输入值，然后按 Enter。

6.  重新运行程序。 记住，您可以使用以下任何一种方法来运行程序。

    -   选择 F5。

    -   在菜单栏上，依次选择“调试” > “开始调试”。

    -   在工具栏上，选择“开始调试”按钮，如下所示。

         ****![“开始调试”工具栏按钮](../ide/media/express_icondebug.png)
“开始调试”工具栏按钮

     与之前的操作一样，IDE 会生成并运行程序，并且将显示一个窗口。

7.  在转到下一个步骤之前，请停止程序，因为 IDE 不允许您在程序处于运行状态时更改程序。 记住，您可以使用以下任何一种方法来停止程序。

    -   在工具栏上，选择“停止调试”按钮。

    -   在菜单栏上，依次选择“调试” > “停止调试”。

    -   选择“Form1”窗口上角的 X 按钮。

## <a name="to-continue-or-review"></a>继续或查看

-   若要转到下一个教程步骤，请参阅[步骤 4：使用 TableLayoutPanel 控件设置窗体的布局](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)。

-   若要返回上一个教程步骤，请参阅[步骤 2：运行程序](../ide/step-2-run-your-program.md)。
