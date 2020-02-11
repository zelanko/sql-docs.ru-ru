---
title: УДАЛИТЬ СТРУКТУРУ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ (DMX) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d5c94ec01ff5f11d2b7f663f09de0a7c1527f343
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68074082"
---
# <a name="drop-mining-structure-dmx"></a>DROP MINING STRUCTURE (расширения интеллектуального анализа данных)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Удаляет из базы данных указанную структуру интеллектуального анализа данных. Все модели интеллектуального анализа данных, связанные с этой структурой, также удаляются из базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP MINING STRUCTURE <structure>  
```  
  
## <a name="arguments"></a>Аргументы  
 *дереве*  
 Идентификатор структуры.  
  
## <a name="examples"></a>Примеры  
 Следующий пример удаляет из базы данных структуру интеллектуального анализа данных New Mailing.  
  
```  
DROP MINING STRUCTURE [New Mailing]  
```  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41; DDL](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
