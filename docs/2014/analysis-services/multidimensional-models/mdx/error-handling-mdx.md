---
title: Ошибка обработки (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: bbbe021cbb65803f79a4aa0a92791441e22e9cb6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37332684"
---
# <a name="error-handling-mdx"></a>Обработка ошибок (многомерные выражения)
  Каждый куб может управлять способом обработки ошибок в скриптах многомерных выражений. Обработка ошибок осуществляется с помощью `ScriptErrorHandlingMode` перечислителя. Перечислитель может принимать следующие значения.  
  
 `IgnoreNone`  
 Ошибка на сервере возникает при обнаружении службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] любых ошибок в скрипте многомерных выражений.  
  
 `IgnoreAll`  
 Сервер игнорирует все команды с ошибками в скрипте многомерных выражений, включая синтаксические ошибки, ошибки разрешения имен и пр.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
