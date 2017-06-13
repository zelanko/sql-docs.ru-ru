---
title: "Использование пользовательских сборок со строгими именами | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3c024efb9f8531ed9b87b0e2b7d7b22489a76dcf
ms.contentlocale: ru-ru
ms.lasthandoff: 06/13/2017

---
# <a name="using-strong-named-custom-assemblies"></a>Использование пользовательских сборок со строгими именами
  Строгое имя идентифицирует сборку и включает текстовое имя сборки, четырехкомпонентный номер версии, сведения о культуре (если они указаны), открытый ключ и цифровую подпись, хранящуюся в манифесте сборки. Строгое имя уникальным образом определяет сборку в среде CLR и гарантирует целостность двоичных файлов.  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>Использование атрибута AllowPartiallyTrustedCallersAttribute  
 Чтобы использование сборок со строгими именами в отчетах, необходимо разрешить сборку вызываться кодом с частичным доверием с использованием сборки со строгими именами **AllowPartiallyTrustedCallers** атрибута. Можно использовать **AllowPartiallyTrustedCallersAttribute** разрешающее сборки со строгими именами, для вызова конструктора отчетов или сервере отчетов в выражениях отчета. Чтобы разрешить вызов сборок со строгими именами из частично доверенного кода, добавьте в файл атрибутов сборки следующий атрибут уровня сборки.  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 **AllowPartiallyTrustedCallersAttribute** вступает в силу только при использовании сборки со строгим именем на уровне сборки. Дополнительные сведения о применении атрибутов на уровне сборки см. в разделе «Применение атрибутов» в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] документации по пакету SDK.  
  
> [!CAUTION]  
>  Когда **AllowPartiallyTrustedCallersAttribute** присутствует, значение по умолчанию **FullTrustLinkDemand** предотвращаются проверок безопасности, что сборка может быть вызван из любого другого частично доверенной сборки. Все виды проверки безопасности, в том числе декларативные атрибуты безопасности уровня класса или уровня метода, необходимо указывать явно.  
  
## <a name="see-also"></a>См. также:  
 [Использование пользовательских сборок с отчетами](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  
