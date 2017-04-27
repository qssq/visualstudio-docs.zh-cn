---
title: "“选项”对话框 -&gt;“环境”-&gt;“快速启动” | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Environment.QuickLaunch"
  - "vs.quicklaunch"
helpviewer_keywords: 
  - "搜索 IDE"
  - "IDE，搜索"
ms.assetid: 4200f297-d065-4723-9a30-d91ff2e26c9d
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# “选项”对话框 -&gt;“环境”-&gt;“快速启动”
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

你可以使用**“快速启动”**快速搜索并执行 IDE 资产的操作，如选项、模板、菜单。  你不能使用**“快速启动”**搜索代码和符号。  **“快速启动”**搜索框位于菜单栏的右上角并且可以通过选择 Ctrl \+ Q 键进行访问。  只需在框中输入搜索字符串。  若要搜索包含 @ 的字符串，请使用“@@”。  
  
 默认情况下，安装 Visual Studio 时会启用**快速启动**。  在菜单栏中，可以通过依次选择**“工具”**、**“选项”**，显示或隐藏**“快速启动”**。  展开**“环境”**节点，然后选择**“快速启动”**。  选中或清除**“启用快速启动”**复选框。  你还可以启用或禁用此页上的搜索类别。  
  
## 类别列表  
 快速启动搜索结果以下面四个类别出现：**“最近使用的”**、**“菜单”**、**“选项”**和**“打开文档”**，同时还出现各类别的项数。  若要按类别遍历搜索结果，请选择 Ctrl\+Q 键以显示下一类别的所有结果。  在上一类别显示后，Ctrl\+Q 会显示每个类别的一些结果。  Ctrl\+Shift\+Q 可用于按相反的顺序在类别间导航。  若要查看某个类别下的所有搜索结果，请选择类别名称。  
  
 以下快捷方式可用于将搜索限于特定的类别。  
  
|类别|快捷键|快捷方式说明|  
|--------|---------|------------|  
|最近使用的|@mru<br /><br /> 例如，`@mru 字体`|显示最多五个你**最近使用的**项。|  
|菜单|@menu<br /><br /> 例如，`@mru 字体`|将搜索限定为菜单项。|  
|选项|@opt<br /><br /> 例如，`@opt 字体`|将搜索限定为**“选项”**对话框中的设置。|  
|文档|@doc<br /><br /> 例如，`@doc 字体`|将搜索限定为打开的文档的文件名称和路径（按搜索条件），但不搜索文件内的文本。|  
  
> [!NOTE]
>  你可以更改**“选项”**对话框中**“键盘”**页的**常规**上的快捷键。  
  
## 显示以前的结果  
 默认情况下，搜索会话之间不保留你输入的搜索词。  如果你搜索某一个词，将光标移动到**“快速启动”**区域外，然后返回，则搜索字符串将被清除。  若要保留搜索结果，请转到**“选项”**对话框，选择**“快速启动”**，然后选择**“快速启动激活时显示上一次搜索的搜索结果。”**复选框。  下一次搜索时，停留在快速启动区域内，然后返回，则快速启动将保留上次使用的搜索词并显示搜索结果。  
  
 有关使用**“快速启动”**的最新提示和技巧，请参阅 [Visual Studio 博客](http://go.microsoft.com/fwlink/?LinkId=236054)。  
  
## 请参阅  
 [常规用户界面元素 \(Visual Studio\)](../../ide/reference/general-user-interface-elements-visual-studio.md)   
 [“选项”对话框 \-\>“环境”](../../ide/reference/environment-options-dialog-box.md)