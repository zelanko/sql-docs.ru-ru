---
title: Обработка ошибок (многомерные выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 611e7636f9a5cd6393da4a8412b6c02bcc9ddaf8
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "66074678"
---
# <a name="error-handling-mdx"></a>Обработка ошибок (многомерные выражения)
  Каждый куб может управлять способом обработки ошибок в скриптах многомерных выражений. Обработка ошибок осуществляется с помощью перечислителя `ScriptErrorHandlingMode`. Перечислитель может принимать следующие значения.  
  
 `IgnoreNone`  
 Заставляет сервер вызывать ошибку при [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] обнаружении любой ошибки в скрипте многомерных выражений.  
  
 `IgnoreAll`  
 Сервер игнорирует все команды с ошибками в скрипте многомерных выражений, включая синтаксические ошибки, ошибки разрешения имен и пр.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
