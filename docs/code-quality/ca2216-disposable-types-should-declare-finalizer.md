---
title: CA2216：可释放类型应声明终结器
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9362d7aea5f66be7a7faa237ab1f78853ac7fd6f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549293"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216：可释放类型应声明终结器

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|类别|Microsoft.Usage|
|是否重大更改|非重大更改|

## <a name="cause"></a>原因

实现的类型<xref:System.IDisposable?displayProperty=fullName>，且具有建议的非托管资源使用的字段，不实现终结器，如中所述<xref:System.Object.Finalize%2A?displayProperty=fullName>。

## <a name="rule-description"></a>规则说明

如果可释放类型包含以下类型的字段的，报告此规则的冲突：

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>如何解决冲突

若要修复此规则的冲突，请实现终结器调用你<xref:System.IDisposable.Dispose%2A>方法。

## <a name="when-to-suppress-warnings"></a>何时禁止显示警告

则可以安全地禁止显示此规则的警告，如果该类型不实现<xref:System.IDisposable>用于释放非托管的资源。

## <a name="example"></a>示例

下面的示例显示了与此规则冲突的类型。

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>相关的规则

[CA2115：使用本机资源时调用 GC.KeepAlive](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816：正确调用 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049：拥有本机资源的类型应可释放](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>请参阅

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [释放模式](/dotnet/standard/design-guidelines/dispose-pattern)