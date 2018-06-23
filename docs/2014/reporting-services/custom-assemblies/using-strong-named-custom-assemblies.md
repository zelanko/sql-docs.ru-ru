---
title: Использование пользовательских сборок со строгими именами | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
caps.latest.revision: 34
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 002445779b68832a9ff68eb35e5dfb4237f854c5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096350"
---
# <a name="using-strong-named-custom-assemblies"></a>Использование пользовательских сборок со строгими именами
  Строгое имя идентифицирует сборку и включает текстовое имя сборки, четырехкомпонентный номер версии, сведения о культуре (если они указаны), открытый ключ и цифровую подпись, хранящуюся в манифесте сборки. Строгое имя уникальным образом определяет сборку в среде CLR и гарантирует целостность двоичных файлов.  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>Использование атрибута AllowPartiallyTrustedCallersAttribute  
 Чтобы использовать с отчетами сборки со строгими именами, необходимо разрешить вызов сборки со строгим именем из частично доверенного кода. Для этого используется атрибут **AllowPartiallyTrustedCallers** сборки. С помощью атрибута **AllowPartiallyTrustedCallersAttribute** можно разрешить вызов сборок со строгими именами в выражениях отчетов из конструктора отчетов или с сервера отчетов. Чтобы разрешить вызов сборок со строгими именами из частично доверенного кода, добавьте в файл атрибутов сборки следующий атрибут уровня сборки.  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 Атрибут **AllowPartiallyTrustedCallersAttribute** действует только при применении сборкой со строгим именем на уровне сборки. Дополнительные сведения о применении атрибутов на уровне сборки см. в разделе "Применение атрибутов" документации по пакету SDK [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)].  
  
> [!CAUTION]  
>  Если присутствует атрибут **AllowPartiallyTrustedCallersAttribute**, то стандартная проверка безопасности **FullTrustLinkDemand** блокируется, что позволяет вызывать сборку из любой другой частично доверенной сборки. Все виды проверки безопасности, в том числе декларативные атрибуты безопасности уровня класса или уровня метода, необходимо указывать явно.  
  
## <a name="see-also"></a>См. также  
 [Использование пользовательских сборок с отчетами](using-custom-assemblies-with-reports.md)  
  
  