---
title: УДАЛЕНИЕ СТРУКТУРЫ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ (DMX) | Документы Microsoft
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b83de343e94c9263ba1ca6c6c8f09be90f3793b2
ms.sourcegitcommit: 8f0faa342df0476884c3238e36ae3d9634151f87
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34841787"
---
# <a name="drop-mining-structure-dmx"></a>DROP MINING STRUCTURE (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Удаляет из базы данных указанную структуру интеллектуального анализа данных. Все модели интеллектуального анализа данных, связанные с этой структурой, также удаляются из базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP MINING STRUCTURE <structure>  
```  
  
## <a name="arguments"></a>Аргументы  
 *Структура*  
 Идентификатор структуры.  
  
## <a name="examples"></a>Примеры  
 Следующий пример удаляет из базы данных структуру интеллектуального анализа данных New Mailing.  
  
```  
DROP MINING STRUCTURE [New Mailing]  
```  
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;расширений интеллектуального анализа данных&#41; инструкции обработки данных](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
