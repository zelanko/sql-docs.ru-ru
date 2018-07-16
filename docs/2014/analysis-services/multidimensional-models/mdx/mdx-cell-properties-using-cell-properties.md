---
title: Свойства ячеек (многомерные Выражения) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- intrinsic cell properties [MDX]
- cells [MDX]
- cell properties [MDX]
- CELL PROPERTIES keyword
ms.assetid: a593c74d-8c5e-485e-bd92-08f9d22451d4
caps.latest.revision: 36
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7ba678db945252692d72901aab725224a6dfb503
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301224"
---
# <a name="using-cell-properties-mdx"></a>Свойства ячеек (многомерные выражения)
  Свойства ячеек в языке многомерных выражений содержат сведения о содержимом и формате ячеек многомерного источника данных, такого как куб.  
  
 В многомерных выражениях поддерживается ключевое слово CELL PROPERTIES инструкции многомерных выражений SELECT, которое служит для обращения к внутренним свойствам ячеек. Внутренние свойства ячеек чаще всего применяются для наглядного представления данных ячейки.  
  
## <a name="cell-properties-keyword-syntax"></a>Синтаксис ключевого слова CELL PROPERTIES  
 Используйте следующий синтаксис для `CELL PROPERTIES` ключевое слово многомерных выражений `SELECT` инструкции:  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
[<cell_props>]  
```  
  
 В следующей синтаксической конструкции демонстрируется формат значения `<cell_props>` и использование этим значением ключевого слова `CELL PROPERTIES` с одним или несколькими внутренними свойствами ячеек.  
  
```  
<cell_props> ::= CELL PROPERTIES <property> [, <property>...]  
```  
  
## <a name="supported-intrinsic-cell-properties"></a>Поддерживаемые внутренние свойства ячеек  
 В следующей таблице перечислены поддерживаемые внутренние свойства ячеек, используемые в качестве значений `<property>` .  
  
|Свойство|Описание|  
|--------------|-----------------|  
|`ACTION_TYPE`|Битовая маска, определяющая существующие типы действий над ячейкой. Это свойство может принимать одно из следующих значений:<br /><br /> **MDACTION_TYPE_URL**<br /><br /> **MDACTION_TYPE_HTML**<br /><br /> **MDACTION_TYPE_STATEMENT**<br /><br /> **MDACTION_TYPE_DATASET**<br /><br /> **MDACTION_TYPE_ROWSET**<br /><br /> **MDACTION_TYPE_COMMANDLINE**<br /><br /> **MDACTION_TYPE_PROPRIETARY**<br /><br /> **MDACTION_TYPE_REPORT**<br /><br /> **MDACTION_TYPE_DRILLTHROUGH**<br /><br /> <br /><br /> Примечание. Действия детализации не поддерживаются для запросов, содержащих набор в предложении WHERE.|  
|**BACK_COLOR**|Цвет фона при отображении свойства `VALUE` или `FORMATTED_VALUE`. Дополнительные сведения см. в разделе [Свойства ячеек FORE_COLOR и BACK_COLOR (многомерные выражения)](mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|`CELL_ORDINAL`|Порядковый номер ячейки в наборе данных.|  
|**FONT_FLAGS**|Битовая маска, определяющая стиль шрифта. Например, значение 5 соответствует комбинации полужирного (`MDFF_BOLD`) и подчеркнутого (`MDFF_UNDERLINE`) эффекты шрифта. Значение представляет собой результат побитовой операции OR над одной или несколькими следующими константами.<br /><br /> `MDFF_BOLD` = 1<br /><br /> `MDFF_ITALIC` = 2<br /><br /> `MDFF_UNDERLINE` = 4<br /><br /> `MDFF_STRIKEOUT` = 8|  
|**FONT_NAME**|Шрифт, используемый для отображения `VALUE` или `FORMATTED_VALUE` свойство.|  
|**FONT_SIZE**|Размер шрифта, используемого для отображения свойства `VALUE` или `FORMATTED_VALUE`.|  
|**FORE_COLOR**|Цвет переднего плана при отображении свойства `VALUE` или `FORMATTED_VALUE`. Дополнительные сведения см. в разделе [Свойства ячеек FORE_COLOR и BACK_COLOR (многомерные выражения)](mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|`FORMAT`|Совпадение с кодом `FORMAT_STRING`.|  
|`FORMAT_STRING`|Строка форматирования, используемая для создания `FORMATTED_VALUE` значение свойства. Дополнительные сведения см. в разделе [Содержание строки FORMAT_STRING (многомерные выражения)](mdx-cell-properties-format-string-contents.md).|  
|`FORMATTED_VALUE`|Символьная строка, представляющая собой форматированный вывод из `VALUE` свойство.|  
|`LANGUAGE`|Локаль, к которой будет применяться `FORMAT_STRING`. `LANGUAGE` обычно используется для конвертации валют.|  
|`UPDATEABLE`|Значение, определяющее возможность обновления ячейки. Это свойство может принимать одно из следующих значений:<br /><br /> `MD_MASK_ENABLED` (0x00000000) ячейку можно обновить.<br /><br /> `MD_MASK_NOT_ENABLED` (0x10000000) ячейку нельзя обновить.<br /><br /> `CELL_UPDATE_ENABLED` (0x00000001) ячейку можно обновить в наборе ячеек.<br /><br /> `CELL_UPDATE_ENABLED_WITH_UPDATE` (0x00000002) ячейку можно обновить с помощью инструкции update. Операция может не выполниться, если обновляемая конечная ячейка не доступна для записи.<br /><br /> `CELL_UPDATE_NOT_ENABLED_FORMULA` (0x10000001) ячейку нельзя обновить, так как в ячейку имеет вычисляемый элемент из ее координат; ячейка была извлечена с набором в предложении предложение. Ячейку можно обновить, даже если значение ячейки зависит от формулы или от вычисляемого элемента (например, если она обрабатывается статистической функцией). В этом случае итоговое значение ячейки может не соответствовать обновленному значению, поскольку на результат влияют вычисления.<br /><br /> `CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE` (0x10000002) ячейку нельзя обновить, поскольку не удалось обновить Несуммарные меры (count, min, max, число различных объектов, полуаддитивные).<br /><br /> `CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE` (0x10000003) ячейку нельзя обновить, поскольку не существует, так как он находится на пересечении меры и элемента измерения, не связанных с группой мер меры.<br /><br /> `CELL_UPDATE_NOT_ENABLED_SECURE` (0x10000005) ячейку нельзя обновить, поскольку она защищена.<br /><br /> `CELL_UPDATE_NOT_ENABLED_CALCLEVEL` (0x10000006) зарезервировано для будущего использования.<br /><br /> `CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE` (0x10000007) ячейку нельзя обновить по внутренним причинам.<br /><br /> `CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE` (0x10000009) ячейку нельзя обновить, поскольку обновление не поддерживается в модели интеллектуального анализа данных, косвенные, или измерением интеллектуального анализа данных.|  
|`VALUE`|Неформатированное значение ячейки.|  
  
 Только `CELL_ORDINAL`, `FORMATTED_VALUE`, и `VALUE` свойства ячейки являются обязательными. Все внутренние или предоставленные поставщиком свойства ячеек, включая их типы данных и поддержку поставщиками, определены в наборе строк схемы `PROPERTIES`. Дополнительные сведения о `PROPERTIES` набора строк схемы, см. в разделе [набор строк MDSCHEMA_PROPERTIES](../../schema-rowsets/ole-db-olap/mdschema-properties-rowset.md).  
  
 По умолчанию если `CELL PROPERTIES` ключевое слово не используется, возвращаются свойства ячеек `VALUE`, `FORMATTED_VALUE`, и `CELL_ORDINAL` (в таком порядке). Если `CELL PROPERTIES` используется ключевое слово, возвращаются свойства ячеек, явно перечисленные в ключевом слове.  
  
 В следующем примере показано использование `CELL PROPERTIES` ключевое слово в запрос многомерных Выражений:  
  
```  
SELECT  
   {[Measures].[Reseller Gross Profit]} ON COLUMNS,  
   {[Reseller].[Reseller Type].[Reseller Name].Members} ON ROWS  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORMAT_STRING, FORE_COLOR, BACK_COLOR  
```  
  
 Свойства ячеек не возвращаются Многомерными запросами, возвращающими плоские наборы строк; в этом случае каждая ячейка представляется так, как если единственным `FORMATTED_VALUE` свойство ячейки были возвращены.  
  
## <a name="setting-cell-properties"></a>Настройка свойств ячеек  
 Свойства ячейки могут задаваться в службах [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] в различных элементах интерфейса. Например, свойство «Строка форматирования» может быть задано для обычных мер на вкладке «Структура куба» конструктора измерений в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Это же свойство можно задать для вычисляемых мер, определенных на кубе, на вкладке «Вычисления» конструктора кубов. Здесь же определяется строка форматирования для вычисляемых мер, определенных в предложении WITH запроса. В следующем запросе описывается задание свойств ячейки в вычисляемой мере:  
  
```  
WITH MEMBER MEASURES.CELLPROPERTYDEMO AS [Measures].[Internet Sales Amount]  
, FORE_COLOR=RGB(0,0,255)  
, BACK_COLOR=IIF([Measures].[Internet Sales Amount]>7000000, RGB(255,0,0), RGB(0,255,0))  
, FONT_SIZE=10  
, FORMAT_STRING='#,#.000'  
SELECT MEASURES.CELLPROPERTYDEMO ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS ON 1  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORE_COLOR, BACK_COLOR, FONT_SIZE  
```  
  
## <a name="see-also"></a>См. также  
 [Основные принципы запросов многомерных Выражений &#40;служб Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
