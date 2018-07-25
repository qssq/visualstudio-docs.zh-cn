---
title: 使用针对 Visual Studio 的 Node.js 工具创建 Vue.js 应用
description: 可以使用 Vue.js 框架在 Visual Studio 中创建 Node.js 应用程序
ms.custom: ''
ms.date: 07/06/2018
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
ms.openlocfilehash: 67b3a5a1a382b6768d25ce2b0550197fc09643fa
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924777"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>使用针对 Visual Studio 的 Node.js 工具创建 Vue.js 应用程序

Visual Studio 2017 包括对 [Vue.js](https://vuejs.org/) 框架的改进支持，这将在通过 Vue.js、JavaScript 和 TypeScript 创建应用程序时改善开发体验。

Visual Studio 中有以下新功能支持 Vue.js 应用程序开发：

* 对 .vue 文件中的脚本、样式和模板块的支持
* 在 .vue 文件上识别 `lang` 属性
* Vue.js 项目和文件模板

## <a name="prerequisites"></a>系统必备

* 必须安装 Visual Studio 2017 版本 15.8 预览版 3 或更高版本，且有“Node.js 开发”工作负载。

    > [!IMPORTANT]
    > 本文需要的功能仅从 Visual Studio 2017 版本 15.8 预览版 3 开始提供。

    如果尚未安装 Visual Studio，请转到 [Visual Studio 下载](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)页免费安装。

    如果需要安装工作负载，但已有 Visual Studio，则单击“新建项目”对话框左窗格中的“打开 Visual Studio 安装程序”链接（选择“文件” > “新建” > “项目”）。 Visual Studio 安装程序启动。 选择“Node.js 开发”工作负载，然后选择“修改”。

* 若要创建 ASP.NET Core 项目，必须有 ASP.NET 且安装 Web 开发和 .NET Core 跨平台开发工作负载。

* 须安装 Node.js 运行时。

    如果未安装，请从 [Node.js](https://nodejs.org/en/download/) 网站安装 LTS 版本。 一般情况下，Visual Studio 会自动检测已安装的 Node.js 运行时。 如果没有检测到已安装的运行时，则可在“属性”页配置项目以引用已安装的运行时。 （创建项目后，右键单击项目节点并选择“属性”）。

## <a name="create-a-vuejs-project-using-a-template"></a>使用模板创建 Vue.js 项目

可以使用新的 Vue.js 模板创建新的项目。 使用模板是最简单的入门方法。 有关详细步骤，请参阅[使用 Visual Studio 创建第一个 Vue.js 应用](../javascript/quickstart-vuejs-with-nodejs.md)。

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>使用 ASP.NET Core 和 Vue CLI 创建 Vue.js 项目

Vue.js 提供官方 CLI，快速搭建项目基架。 如果想要使用 CLI 创建应用程序，请按照本文步骤设置开发环境。

> [!IMPORTANT]
> 这些步骤假定你已有一些 Vue.js 框架经验。 如果没有，请访问 [Vue.js](https://vuejs.org/) 了解有关框架的详细信息。

### <a name="create-a-new-aspnet-core-project"></a>创建新的 ASP.NET Core 项目

在此示例中，使用空的 ASP.NET Core 应用程序 (C#)。 但是，可以选择不同的项目和编程语言。

#### <a name="create-an-empty-project"></a>创建一个空项目

1. 打开 Visual Studio，然后在主菜单中选择“文件” > “新建” > “项目”。

1. 在“Visual C#” > “Web”下，选择“ASP.NET Core Web 应用程序”，然后单击“确定”。

    如果没有看到“ASP.NET Core Web 应用程序”项目模板，则必须先安装“ASP.NET 和 Web 开发”工作负载和“.NET Core”开发工作负载。 若要安装工作负载，单击“新建项目”对话框左窗格中的“打开 Visual Studio 安装程序”链接（选择“文件” > “新建” > “项目”）。 Visual Studio 安装程序启动。 选择所需工作负载。

1. 选择“空”，然后单击“确定”。

    Visual Studio 创建项目，该项目将在解决方案资源管理器（右窗格）中打开。

#### <a name="configure-the-project-startup-file"></a>配置项目启动文件

* 打开文件 ./Startup.cs，并将以下行添加到配置方法：

    ```csharp
    app.UseDefaultFiles() // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>安装 vue CLI

若要安装 vue-cli npm 模块，请打开命令提示符并键入适用于版本 3.0（目前为 beta 版本）的 `npm install --g vue-cli` 或 `npm install -g @vue/cli`。

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>使用 vue CLI 搭建新客户端应用程序基架

1. 转到命令提示符，并将当前目录更改为项目根文件夹。

1. 系统提示回答其他问题时，请键入 `vue init webpack ClientApp` 并按照步骤执行操作。

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>修改 webpack 配置将生成的文件输出到 wwwroot

* 打开文件 ./ClientApp/config/index.js，并将 `build.index` 和 `build.assetsRoot` 更改为 wwwroot 路径：

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a>每次触发生成时，指示项目生成 ClientApp

1. 在 Visual Studio 中，转到“项目” > “属性” > “生成事件”。

1. 在“预生成事件命令行”上，键入 `npm --prefix ./ClientApp run build`。

#### <a name="configure-webpacks-output-module-names"></a>配置 webpack 的输出模块名称

* 打开文件 ./ClientApp/build/webpack.base.conf.js，并将以下属性添加到输出属性：

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>使用 Vue CLI 添加 TypeScript 支持

这些步骤需要当前仍处于 beta 版本的 vue-cli 3.0。

1. 转到命令提示符，并将当前目录更改为项目根文件夹。

1. 键入 `vue create ClientApp`，然后选择“手动选择功能”。

1. 选择“Typescript”，然后选择其他所需的选项。

1. 执行剩余步骤并对问题做出响应。

#### <a name="configure-a-vuejs-project-for-typescript"></a>为 TypeScript 配置 Vue.js 项目

1. 打开文件 ./ClientApp/tsconfig.json，并将 `noEmit:true` 添加到编译器选项。

    通过设置此选项，可以避免每次在 Visual Studio 中生成时干扰项目。

1. 接下来，在 ./ClientApp/ 中创建 vue.config.js 文件，并添加以下代码。

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    前面的代码配置 webpack 并设置 wwwroot 文件夹。

#### <a name="build-with-vue-cli-30"></a>使用 vue-cli 3.0 生成

vue-cli 3.0 出现未知问题阻止自动执行生成过程。 每次尝试刷新 wwwroot 文件夹时，需要在 ClientApp 文件夹上运行命令 `npm run build`。

## <a name="limitations"></a>限制

* `lang` 属性仅支持 JavaScript 和 TypeScript 语言。 接受的值为：js、jsx、ts 和 tsx。
* `lang` 属性不适用于模板或样式标记。
* 因其预处理的特性，所以不支持在 .vue 文件中调试脚本块。
* TypeScript 不会将 .vue 文件识别为模块。 需要一个包含如下所示代码的文件，告知 TypeScript .vue 文件的外观（vue-cli 3.0 模板已包括此文件）。

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* 使用 vue-cli 3.0 时，无法在项目属性上将命令 `npm run build` 作为预生成的事件运行。

## <a name="see-also"></a>请参阅
https://vuejs.org/v2/guide - Vue 入门指南。  
https://github.com/vuejs/vue-cli - Vue CLI 项目。  
https://webpack.js.org/configuration/ - Webpack 配置文档。