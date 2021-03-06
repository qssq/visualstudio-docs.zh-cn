---
title: -Command (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /command switch
- /command Devenv switch
ms.assetid: 13c20cd6-f09d-400a-8b7b-ecc266a32cef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c21402c3b2b71372aaf170c68c65777eba4e95bf
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
ms.locfileid: "33703741"
---
# <a name="command-devenvexe"></a>/Command (devenv.exe)
在启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 集成开发环境 (IDE) 后执行指定的命令。

## <a name="syntax"></a>语法

```cmd
devenv /command CommandName
```

## <a name="arguments"></a>自变量
 `CommandName`（必需）。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 命令或其别名的完整名称括在双引号内。 有关命令和别名语法的详细信息，请参阅 [Visual Studio 命令](../../ide/reference/visual-studio-commands.md)。

## <a name="remarks"></a>备注
 启动完成后，IDE 将执行已命名的命令。 如果使用此开关，IDE 将不会在启动时显示 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 起始页。

 如果外接程序公开了某个命令，则可以使用此开关从命令行启动此外接程序。 有关详细信息，请参阅[如何：使用外接程序管理器控制外接程序](http://msdn.microsoft.com/Library/4f60444a-cb48-4cdb-8df4-941f6419aeeb)。

## <a name="example"></a>示例
 此示例将启动 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 并自动运行宏“打开收藏夹文件”。

```cmd
devenv /command "Macros.MyMacros.Module1.OpenFavoriteFiles"
```

## <a name="see-also"></a>请参阅

- [Devenv 命令行开关](../../ide/reference/devenv-command-line-switches.md)
- [Visual Studio 命令别名](../../ide/reference/visual-studio-command-aliases.md)