---
title: 在无需解决方案或项目的情况下在 Visual Studio 中编写 JavaScript 代码
description: Visual Studio 支持创建代码，而无需依赖于项目文件或解决方案文件
ms.custom: ''
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 7d56030b78abe57c80d816881991b9819ed6456b
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924737"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>在 Visual Studio 中开发 JavaScript 和 TypeScript 代码，而无需解决方案或项目

Visual Studio 2017 引入了[开发代码而无需项目或解决方案](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md)的功能，这样便可打开代码的文件夹并立即开始使用丰富的编辑器支持，如 IntelliSense、搜索、重构、调试等。
除了这些功能，针对 Visual Studio 的 Node.js 工具还支持生成 TypeScript 文件、管理 npm 包和运行 npm 脚本。

若要开始，请从打开 Visual Studio 时出现的“开始”页中选择“打开文件夹”，或者从工具栏选择“文件” > “打开” > “文件夹”。 解决方案资源管理器显示文件夹中的所有文件，你可以打开任何文件以开始编辑。 在后台，Visual Studio 对文件编制索引，启用 npm、生成和调试功能。

> [!IMPORTANT]
> 本文所述的很多功能（包括 npm 集成）均要求 Visual Studio 2017 版本 15.8 预览版 3。

## <a name="npm-integration"></a>npm 集成

如果打开的文件夹包含 package.json 文件，可以右键单击 package.json，显示特定于 npm 的上下文菜单（快捷菜单）。 

![解决方案资源管理器中的 npm 菜单](../javascript/media/solution-explorer-npm-ctx.png) 

在快捷菜单中，可以管理由 npm 安装的包，如同使用项目文件时[管理 npm 包](npm-package-management.md)一样。

此外，菜单还允许运行 package.json 中 `scripts` 元素定义的脚本。 这些脚本将使用 `PATH` 环境变量上提供的 Node.js 版本。 脚本在新窗口中运行。 这是执行生成或运行脚本的好办法。

## <a name="build-and-debug"></a>生成和调试

### <a name="packagejson"></a>package.json
如果文件夹中的 package.json 指定 `main` 元素，“调试”命令将出现在 package.json 的右击快捷菜单中。 单击此项将启动 node.exe，使用指定脚本作为其参数。

### <a name="javascript-files"></a>JavaScript 文件
右键单击文件并从快捷菜单中选择“调试”，可以调试 JavaScript 文件。 这将启动 node.exe，使用该 JavaScript 文件作为其参数。

### <a name="typescript-files-and-tsconfigjson"></a>TypeScript 文件和 tsconfig.json
如果文件夹中没有任何 tsconfig.json，可以右键单击 TypeScript 文件，查看快捷菜单命令来生成和调试该文件。 使用这些命令时，使用 tsc.exe 通过默认选项来进行生成或调试。 （需要生成文件，才可进行调试。）

> [!NOTE]
> 生成 TypeScript 代码时，我们使用 `C:\Program Files (x86)\Microsoft SDKs\TypeScript` 中安装的最新版本。

如果文件夹中存在 tsconfig.json 文件，可以右键单击 TypeScript 文件，查看菜单命令来调试该 TypeScript 文件。 仅当 tsconfig.json 中未指定任何 `outFile` 时，该选项才出现。 如果指定了 `outFile`，可以右键单击 tsconfig.json 并选择正确选项来调试该文件。 `tsconfig.json` 文件还提供生成选项，可借此指定编译器选项。

> [!NOTE]
> 若要了解 tsconfig.json 的详细信息，可查找 [tsconfig.json TypeScript 手册页](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)。