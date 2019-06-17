---
title: Ошибка обработки (многомерные Выражения) | Документация Майкрософт
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5d6679e264ee15fd6a1ba038d3c6492aec07c81c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62802714"
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
  
  
