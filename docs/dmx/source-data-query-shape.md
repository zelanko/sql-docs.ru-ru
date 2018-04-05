---
title: ФИГУРЫ (ДАННЫХ DMX) | Документы Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: data-mining
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SHAPE
dev_langs:
- DMX
helpviewer_keywords:
- SHAPE statement
- multiple data sources
ms.assetid: b9526ec2-40bc-4bf5-b4e5-774f71075065
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 3156c9110567763d1566de58b6d08304b464e094
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="ltsource-data-querygt---shape"></a>&lt;запрос источника данных&gt; -ФИГУРЫ
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Комбинирует запросы от нескольких источников данных в одну иерархическую таблицу (являющуюся таблицей с вложенными таблицами), которая становится таблицей вариантов для модели интеллектуального анализа данных.  
  
 Полный синтаксис **ФИГУРЫ** команда описана в [!INCLUDE[msCoName](../includes/msconame-md.md)] Data Access Components (MDAC) средств разработки программного обеспечения (SDK).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SHAPE {<master query>}  
APPEND ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS <column table name>  
[  
     ({ <child table query> }   
     RELATE <master column> TO <child column>)   
          AS < column table name>  
...  
]       
```  
  
## <a name="arguments"></a>Аргументы  
 *главного запроса*  
 Запрос, возвращающий родительскую таблицу.  
  
 *запроса дочерней таблицы*  
 Запрос, возвращающий вложенную таблицу.  
  
 *основной столбец*  
 Столбец в родительской таблице для определения дочерних строк из результата запроса дочерней таблицы.  
  
 *дочерний столбец*  
 Столбец в дочерней таблице для определения родительской строки из результата главного запроса.  
  
 *Имя столбца таблицы*  
 Имя добавленного столбца в родительской таблице для вложенной таблицы.  
  
## <a name="remarks"></a>Remarks  
 Необходимо упорядочить запросы столбца, связанного с родительской и дочерней таблицей.  
  
## <a name="examples"></a>Примеры  
 Можно использовать следующий пример в [INSERT INTO &#40; расширений интеллектуального анализа данных &#41;](../dmx/insert-into-dmx.md) инструкции для обучения модели, содержащей вложенную таблицу. Две таблицы в **ФИГУРЫ** инструкции связаны через **OrderNumber** столбца.  
  
```  
SHAPE {  
    OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber  
    FROM vAssocSeqOrders ORDER BY OrderNumber')  
} APPEND (  
    {OPENQUERY([Adventure Works DW Multidimensional 2012],'SELECT OrderNumber, model FROM   
    dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')}  
  RELATE OrderNumber to OrderNumber)   
```  
  
## <a name="see-also"></a>См. также:  
 [&#60; запросом источника данных &#62;](../dmx/source-data-query.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции определения данных](../dmx/dmx-statements-data-definition.md)   
 [Расширения интеллектуального анализа данных &#40; расширений интеллектуального анализа данных &#41; Инструкции управления данными](../dmx/dmx-statements-data-manipulation.md)   
 [Справочник по расширениям интеллектуального анализа данных (расширения интеллектуального анализа данных)](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
