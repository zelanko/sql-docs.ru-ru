---
title: "Обработка ошибок (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
caps.latest.revision: "26"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8679c6d912e6dab8fa89f4f67ddfa9070c04460f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="error-handling-mdx"></a>Обработка ошибок (многомерные выражения)
  Каждый куб может управлять способом обработки ошибок в скриптах многомерных выражений. Обработка ошибок осуществляется с помощью перечислителя **ScriptErrorHandlingMode** . Перечислитель может принимать следующие значения.  
  
 **IgnoreNone**  
 Ошибка на сервере возникает при обнаружении службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] любых ошибок в скрипте многомерных выражений.  
  
 **IgnoreAll**  
 Сервер игнорирует все команды с ошибками в скрипте многомерных выражений, включая синтаксические ошибки, ошибки разрешения имен и пр.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
