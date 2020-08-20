---
description: '&lt;запрос источника данных &gt; — форма'
title: SHAPE (РАСШИРЕНИЯ ИНТЕЛЛЕКТУАЛЬНОГО АНАЛИЗА ДАННЫХ) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 16fff086514facbb8197d8d6f27b72b81f67c2e2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500811"
---
# <a name="ltsource-data-querygt---shape"></a>&lt;запрос источника данных &gt; — форма
[!INCLUDE[ssas](../includes/applies-to-version/ssas.md)]

  Комбинирует запросы от нескольких источников данных в одну иерархическую таблицу (являющуюся таблицей с вложенными таблицами), которая становится таблицей вариантов для модели интеллектуального анализа данных.  
  
 Полный синтаксис команды **Shape** описан в [!INCLUDE[msCoName](../includes/msconame-md.md)] пакете средств разработки программного обеспечения (SDK) для компонентов доступа к данным (MDAC).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SHAPE {<primary query>}  
APPEND ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <primary column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Аргументы  
 *первичный запрос*  
 Запрос, возвращающий родительскую таблицу.  
  
 *запрос дочерней таблицы*  
 Запрос, возвращающий вложенную таблицу.  
  
 *первичный столбец*  
 Столбец в родительской таблице для определения дочерних строк из результата запроса дочерней таблицы.  
  
 *дочерний столбец*  
 Столбец в дочерней таблице, который определяет родительскую строку из результата первичного запроса.  
  
 *имя таблицы столбцов*  
 Имя добавленного столбца в родительской таблице для вложенной таблицы.  
  
## <a name="remarks"></a>Комментарии  
 Необходимо упорядочить запросы столбца, связанного с родительской и дочерней таблицей.  
  
## <a name="examples"></a>Примеры  
 Для обучения модели, содержащей вложенную таблицу, можно использовать следующий пример в инструкции [INSERT в &#40;DMX&#41;](../dmx/insert-into-dmx.md) . Две таблицы в инструкции **Shape** связаны с помощью столбца **OrderNumber** .  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>См. также  
 [&#62;запроса источника данных&#60;](../dmx/source-data-query.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41; DDL](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40;инструкции расширений интеллектуального анализа данных&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
