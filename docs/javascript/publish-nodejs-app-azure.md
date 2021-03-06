---
title: 将 Node.js 应用发布到 Linux 应用服务
description: 可以将 Visual Studio 中创建的 Node.js 应用程序发布到 Azure 上的 Linux 应用服务
ms.custom: ''
ms.date: 06/10/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: cf96610abcd0cc18bdaab6177980ca04e0232642
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924767"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>将 Node.js 应用程序发布到 Azure（Linux 应用服务）

本教程指导你完成创建简单 Node.js 应用程序并将其发布到 Azure 的任务。

将 Node.js 应用程序发布到 Azure 时，提供几个选项。 其中包括 Azure 应用服务、运行所选 OS 的 VM、用于 Kubernetes 管理的 Azure 容器服务 (AKS)、使用 Docker 的容器实例等等。 有关各选项的详细信息，请参阅[计算](https://azure.microsoft.com/product-categories/compute/)。

对于本教程，将应用部署到 [Linux 应用服务](/azure/app-service/containers/app-service-linux-intro)。
Linux 应用服务部署 Linux Docker 容器来运行 Node.js 应用程序（不同于 Windows 应用服务，后者在 Windows 上 IIS 后运行 Node.js 应用程序）。

本教程从随针对 Visual Studio 的 Node.js 工具安装的一个模板开始，演示如何创建 Node.js 应用程序，并将代码推动到 GitHub 上的存储库，然后通过 Azure Web 门户预配 Azure 应用服务，以便可以从 GitHub 存储库进行部署。 若要使用命令行来预配 Azure 应用服务并从本地 Git 存储库推送代码，请参阅[创建 Node.js 应用](/azure/app-service/containers/quickstart-nodejs)。

在本教程中，你将了解：
> [!div class="checklist"]
> * 创建 Node.js 项目
> * 为代码创建 GitHub 存储库
> * 创建 Azure 上的 Linux 应用服务
> * 部署到 Linux

## <a name="create-a-nodejs-project-to-run-in-azure"></a>创建要在 Azure 中运行的 Node.js 项目

1. 使用“文件” > “新建项目”对话框，创建新的 TypeScript Express 应用。

    ![创建新的 TypeScript Express 应用](../javascript/media/azure-ts-express-app.png)

2. 按 F5 来生成并运行应用，确保一切按预期运行。

3. 选择“文件” > “添加到源代码管理”，创建项目的本地 Git 存储库。

    此时，采用 Express 框架且以 TypeScript 编写的 Node.js 应用正常工作并签入到本地源代码管理。

4. 根据需要编辑项目，再继续到下一步骤。

## <a name="push-code-from-visual-studio-to-github"></a>将代码从 Visual Studio 推送到 GitHub

设置用于 Visual Studio 的 GitHub：

1. 使用“工具” > “扩展和更新”，确保安装和启用[适用于 Visual Studio 的 GitHub 扩展](https://visualstudio.github.com/)。

2. 从菜单中选择“视图” > “其他窗口” > “GitHub”。

    GitHub 窗口随即打开。

3. 如果在 GitHub 窗口中没有看到“开始操作”按钮，请单击“文件” > “添加到源代码管理”并等待 UI 更新。

    ![打开 GitHub 窗口](../javascript/media/azure-github-get-started.png)

4. 单击“开始操作”。

    如果已连接到 GitHub，工具箱将显示，类似于下图。

    ![GitHub 存储库设置](../javascript/media/azure-github-publish.png)

5. 填写字段使新存储库得以发布，然后单击“发布”。

    几分钟后会显示一个横幅，指出“已成功创建存储库”。

    下一步部分中，将学习如何从此存储库发布到 Linux 上 Azure 应用服务。

## <a name="create-a-linux-app-service-in-azure"></a>创建 Azure 中的 Linux 应用服务

1. 登录到 [Azure 门户](https://portal.azure.com)。

2. 从左侧服务列表中选择“应用服务”，然后单击“添加”。

3. 如果要求，请创建新的资源组和应用服务计划来托管新应用。

4. 确保将“OS”设为“Linux”，将“运行时堆栈”设为所需 Node.js 版本，如图所示。

    ![创建 Linux 应用服务](../javascript/media/azure-create-appservice-annotated.png)

5. 单击“创建”以创建应用服务。

    部署可能需要几分钟的时间。

6. 部署后，请转到“应用程序设置”部分，添加一个名为 `SCM_SCRIPT_GENERATOR_ARGS`、值为 `--node` 的设置。

    ![应用程序设置](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > 应用服务部署过程使用一组试探法来确定要尝试和运行哪种类型的应用程序。 如果在已部署的内容中检测到 .sln 文件，则假设正在部署基于 MSBuild 的项目。 上面添加的设置将覆盖此逻辑，并显式指定这是 Node.js 应用程序。 如果没有此设置，当 .sln 文件属于正部署到应用服务的存储库时，Node.js 应用程序将部署失败。

7. 部署后，打开应用服务，并选择“部署选项”。

    ![部署选项](../javascript/media/azure-deployment-options.png)

8. 单击“选择源”，选择“GitHub”，然后配置任何所需的权限。

    ![GitHub 权限](../javascript/media/azure-choose-source.png)

9. 选择要发布的存储库和分支，并选择“确定”。

    ![发布到 Linux 应用服务](../javascript/media/azure-repo-and-branch.png)

    同步时“部署选项”页将出现。

    ![部署并与 GitHub 同步](../javascript/media/azure-deployment-options-sync.png)

    完成同步后，将出现一个复选标记。

    站点现在运行来自 GitHub 存储库的 Node.js 应用程序，可通过为 Azure 应用服务创建的 URL 进行访问（默认情况下为 Azure 应用服务提供的名称后跟“.azurewebsites.net”）。

## <a name="modify-your-app-and-push-changes"></a>修改应用并推送更改

1. 在 `app.use('/users', users);` 行之后，将此处显示的代码添加到 app.ts。 这会在 URL /api 处添加 REST API。

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. 生成代码并进行本地测试，然后将其签入并推送到 GitHub。

    在 Azure 门户中，需要一些时间来检测 GitHub 存储库中的更改，然后开始再次同步部署。 它看上去类似于下图。

    ![修改和同步](../javascript/media/azure-changes-detected.png)

3. 部署完成后，导航到公共站点并向 URL 追加 /api。 返回 JSON 响应。

## <a name="troubleshooting"></a>疑难解答

* 如果 node.exe 进程发生故障（也就是说出现未处理的异常），容器将重新启动。
* 容器启动时，它通过各种试探法来找出如何启动 Node.js 进程。 可在 [generateStartupCommand.js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js) 看到实现的详细信息。
* 可以通过 SSH 连接到正在运行的容器进行调查。 这可以通过 Azure 门户轻松实现。 选择应用服务，向下滚动工具列表直至“开发工具”部分下的“SSH”。
* 若要帮助进行故障排除，请转到应用服务的“诊断日志”设置，并将“Docker 容器日志记录”设置从“关”改为“文件系统”。 日志创建在 /home/LogFiles/_docker.log* 中，并且可以通过 SSH 或 FTP 在框上进行访问。
* 可向站点分配自定义域名，而不是默认分配的 *.azurewebsites.net URL。 有关更多详细信息，请参阅主题[映射自定义域](/azure/app-service/app-service-web-tutorial-custom-domain)。
* 最好先部署到过渡站点进行进一步测试，再移动到生产环节。 有关如何配置此项的详细信息，请参阅主题[创建过渡环境](/azure/app-service/web-sites-staged-publishing)。
* 有关更多常问问题，请参阅 [Linux 上应用服务的常见问题解答](/azure/app-service/containers/app-service-linux-faq)。

## <a name="next-steps"></a>后续步骤

本教程中，你学习了如何创建 Linux 应用服务并将 Node.js 应用程序部署到该服务。 你可能想要详细了解 Linux 应用服务。

> [!div class="nextstepaction"]
> [Linux 应用服务](/azure/app-service/containers/app-service-linux-intro)
