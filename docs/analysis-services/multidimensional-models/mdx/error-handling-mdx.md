---
title: Обработка ошибок (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 66afc408e71bdbbeb9752aa8377a237fa3c5f7c4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="error-handling-mdx"></a>Обработка ошибок (многомерные выражения)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Каждый куб может управлять способом обработки ошибок в скриптах многомерных выражений. Обработка ошибок осуществляется с помощью перечислителя **ScriptErrorHandlingMode** . Перечислитель может принимать следующие значения.  
  
 **IgnoreNone**  
 Ошибка на сервере возникает при обнаружении службами [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] любых ошибок в скрипте многомерных выражений.  
  
 **IgnoreAll**  
 Сервер игнорирует все команды с ошибками в скрипте многомерных выражений, включая синтаксические ошибки, ошибки разрешения имен и пр.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
