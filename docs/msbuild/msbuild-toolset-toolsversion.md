---
title: "MSBuild 工具集 (ToolsVersion) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 多目标"
  - "MSBuild, 以特定的 .NET Framework 为目标"
  - "多目标 [MSBuild]"
  - "以特定的 .NET Framework 为目标 [MSBuild]"
ms.assetid: 40040ee7-4620-4043-a6d8-ccba921421d1
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# MSBuild 工具集 (ToolsVersion)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

MSBuild 使用任务、目标和工具的工具集以生成应用程序。  通常，MSBuild 工具集包括 microsoft.common.tasks 文件、microsoft.common.targets 文件以及编译器（如 csc.exe 和 vbc.exe）。  大多数工具集可用于将应用程序编译为多个版本的 .NET Framework 以及多个系统平台。  但 MSBuild 2.0 工具集仅可用于面向 .NET Framework 2.0。  
  
## ToolsVersion 特性  
 在项目文件中 [Project](../msbuild/project-element-msbuild.md) 元素的 `ToolsVersion` 特性中指定工具集。  下面的示例指定应使用 MSBuild 12.0 工具集来生成项目。  
  
```  
<Project ToolsVersion="12.0" ... </Project>  
```  
  
## ToolsVersion 特性的工作原理  
 当你在 Visual Studio 中创建项目或更新现有项目时，名为 `ToolsVersion` 的特性将自动包括在项目文件中，并且其值对应于包括在 Visual Studio 版本中的 MSBuild 版本。  有关详细信息，请参阅[面向特定的 .NET Framework 版本](../ide/targeting-a-specific-dotnet-framework-version.md)。  
  
 当 `ToolsVersion` 值在项目文件中定义时，MSBuild 将使用该值来确定在该项目中可用的工具集属性的值。  其中一个工具集属性为 `$(MSBuildToolsPath)`，该属性指定 .NET Framework 工具的路径。  仅该工具集属性（或 `$(MSBuildBinPath)`）是必需的。  
  
 从 Visual Studio 2013 开始，MSBuild 工具集版本号与 Visual Studio 版本号相同。  无论项目文件中指定哪个工具集版本，MSBuild 都会在 Visual Studio 中和命令行上默认使用该工具集。  使用 \/ToolsVersion 标志可重写此行为。  有关详细信息，请参阅[重写 ToolsVersion 设置](../msbuild/overriding-toolsversion-settings.md)。  
  
 在下面的示例中，MSBuild 将使用 `MSBuildToolsPath` 保留的属性查找 Microsoft.CSharp.targets 文件。  
  
```  
<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />  
```  
  
 可通过定义自定义工具集来修改 `MSBuildToolsPath` 的值。  有关详细信息，请参阅[标准和自定义工具集配置](../msbuild/standard-and-custom-toolset-configurations.md)。  
  
 当在命令行上生成解决方案并为 msbuild.exe 指定 `ToolsVersion` 时，所有项目及其项目到项目的依赖项均基于该 `ToolsVersion` 生成，即便解决方案中的每个项目都指定了自己的 `ToolsVersion` 也是如此。  若要针对每个项目定义 `ToolsVersion` 值，请参阅[重写 ToolsVersion 设置](../msbuild/overriding-toolsversion-settings.md)。  
  
 `ToolsVersion` 特性也用于项目移植。  例如，如果你在 Visual Studio 2010 中打开 Visual Studio 2008 项目，则该项目文件将更新以包括 ToolsVersion\=“4.0”。  如果你此时尝试在 Visual Studio 2008 中打开该项目，由于它不会识别已升级的 `ToolsVersion`，因此它会按照该特性设置为 3.5 的情况生成该项目。  
  
 Visual Studio 2010 和 Visual Studio 2012 使用的 ToolsVersion 为 4.0。  Visual Studio 2013 使用的 ToolsVersion 为 12.0。  在许多情况下，无需修改即可在 Visual Studio 的所有三个版本中打开该项目。  Visual Studio 始终会使用正确的工具集，但是会在使用的版本与项目文件中的版本不匹配时通知你。  在几乎所有情况下，此警告是良性的，因为工具集在大多数情况下都兼容。  
  
 子工具集（将在本主题后面部分介绍）允许 MSBuild 根据运行生成所在的上下文自动切换要使用的工具集。  例如，当 MSBuild 在 Visual Studio 2012 中运行时，它将使用比在 Visual Studio 2010 中运行时更新的工具集，而且你无需显式更改项目文件。  有关详细信息，请参阅[使自定义项目版本可区别](../misc/making-custom-projects-version-aware.md)。  
  
## 工具集实现  
 通过选择组成某个工具集的各种工具、目标以及任务的路径来实现该工具集。  MSBuild 定义的工具集中的工具来自以下源：  
  
-   .NET Framework 文件夹。  
  
-   其他托管工具。  
  
 这些托管工具包括 ResGen.exe 和 TlbImp.exe。  
  
 MSBuild 提供了两种方式来访问工具集：  
  
-   使用工具集属性  
  
-   使用 <xref:Microsoft.Build.Utilities.ToolLocationHelper> 方法  
  
 工具集属性指定工具的路径。  MSBuild 使用项目文件中的 `ToolsVersion` 属性的值以查找相应的注册表项，然后使用该注册表项中的信息来设置工具集属性。  例如，如果 `ToolsVersion` 的值为 `12.0`，则 MSBuild 将根据以下注册表项设置工具集属性：HKLM\\Software\\Microsoft\\MSBuild\\ToolsVersions\\12.0。  
  
 这些是工具集属性：  
  
-   `MSBuildToolsPath` 指定 MSBuild 二进制文件的路径。  
  
-   `SDK40ToolsPath` 为 MSBuild 4.x（可以是 4.0 或 4.5）指定其他托管工具的路径。  
  
-   `SDK35ToolsPath` 为 MSBuild 3.5 指定其他托管工具的路径。  
  
 或者，可以通过调用 <xref:Microsoft.Build.Utilities.ToolLocationHelper> 类的方法以编程方式确定工具集。  此类包括以下方法：  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFramework%2A> 返回 .NET Framework 文件夹的路径。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkFile%2A> 返回 .NET Framework 文件夹中文件的路径。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdk%2A> 返回托管工具文件夹的路径。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToDotNetFrameworkSdkFile%2A> 返回某个文件的路径，该文件通常位于托管工具文件夹中。  
  
-   <xref:Microsoft.Build.Utilities.ToolLocationHelper.GetPathToBuildTools%2A> 返回生成工具的路径。  
  
### 子工具集  
 如本主题前面所述，MSBuild 使用注册表项来指定基本工具的路径。  如果该注册表项具有一个子项，则 MSBuild 将使用它来指定包含其他工具的子工具集的路径。  在这种情况下，通过合并在这两个项中定义的属性定义对工具集进行定义。  
  
> [!NOTE]
>  如果工具集属性名称发生冲突，则为子项路径定义的值会覆盖为根项路径定义的值。  
  
 若存在 `VisualStudioVersion` 生成属性，则子工具集将变为活动状态。  此属性可能会采用以下值之一：  
  
-   “10.0”表示 .NET Framework 4 子工具集  
  
-   “11.0”表示 .NET Framework 4.5 子工具集  
  
-   “12.0”表示 .NET Framework 4.5.1 子工具集  
  
 子工具集 10.0 和 11.0 应与 ToolsVersion 4.0 一起使用。  在更高版本中，子工具集版本和 ToolsVersion 应匹配。  
  
 在生成期间，MSBuild 将自动确定并设置 `VisualStudioVersion` 属性的默认值（如果尚未定义）。  
  
 MSBuild 为 `ToolLocationHelper` 方法提供重载，它们可将 `VisualStudioVersion` 枚举值添加为参数  
  
 在 .NET Framework 4.5 中引入了子工具集。  
  
## 请参阅  
 [标准和自定义工具集配置](../msbuild/standard-and-custom-toolset-configurations.md)   
 [多目标](../msbuild/msbuild-multitargeting-overview.md)