---
title: ProjectOutputFile 元素 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 99f8173da22f631a1be74c18d4312f74958259e9
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118487"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 元素
  表示要部署到 SharePoint 项目项包含一个单独的项目的输出。  
  
## <a name="syntax"></a>语法  
  
```xml  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## <a name="type"></a>类型  
 **ProjectOutputFileType**  
  
## <a name="attributes-and-elements"></a>特性和元素
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|**ProjectId**|所需**xs: string**属性。<br /><br /> 有想要包括的输出的依赖项目的 GUID。 这对应于**ProjectGuid**相关的项目文件中的元素。|  
|**ProjectPath**|所需**xs: string**属性。<br /><br /> 相对路径，包括项目文件名称，相关项目具有你想要包括的输出。 此路径是相对于包含 SharePoint 项目项的 SharePoint 项目的根文件夹。|  
|**Target**|可选**xs: string**属性。<br /><br /> 若要部署的 SharePoint 服务器上，相对于部署根文件夹相关的项目输出路径。 部署根文件夹由指定的部署类型**类型**属性。<br /><br /> 有关详细信息，请参阅的说明**部署路径**并**Deployment Root**属性的 SharePoint 项目项中的[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)。|  
|**Type**|所需**xs: string**属性。<br /><br /> 要使用的输出的相关项目的部署类型。 有关可能的值的详细信息，请参阅的说明**部署类型**属性中的 SharePoint 项目项[开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)。|  
  
### <a name="child-elements"></a>子元素
 无。  
  
### <a name="parent-elements"></a>父元素
  
|元素|描述|  
|-------------|-----------------|  
|[文件](../sharepoint/files-element.md)|指定要部署到 SharePoint 时，包含与 SharePoint 项目项的文件。|  
  
## <a name="remarks"></a>备注  
 使用**ProjectOutputFile**要部署的 SharePoint 项目项中包含项目的输出元素。 可以指定一个不同的项目或包含的项目项的同一个项目。 有关详细信息，请参阅[提供在项目项中的打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)。  
  
## <a name="element-information"></a>元素信息
  
|||  
|-|-|  
|**命名空间**|http<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**架构名称**|SharePoint 项目项架构|  
|**验证文件**|ProjectItemModelSchema.xsd|  
|**可以为空**|否|  
  
## <a name="see-also"></a>请参阅
 [SharePoint 项目项架构参考](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [提供在项目项中的打包和部署信息](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [开发 SharePoint 解决方案](../sharepoint/developing-sharepoint-solutions.md)  
  
