---
title: УДАЛИТЬ СТРУКТУРУ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ (DMX) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 607f8f18688f9a16b2f80131e728031b3ca78608
ms.sourcegitcommit: 205de8fa4845c491914902432791bddf11002945
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "86971762"
---
# <a name="drop-mining-structure-dmx"></a>DROP MINING STRUCTURE (расширения интеллектуального анализа данных)
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

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
  
## <a name="see-also"></a>См. также  
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41; DDL](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
