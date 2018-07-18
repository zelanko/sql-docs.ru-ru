---
title: Свойства ячеек (многомерные Выражения) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 481d89abac98dee1095e55a9890cea100f6c4db6
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023431"
---
# <a name="mdx-cell-properties---using-cell-properties"></a>Свойства ячеек MDX - свойства ячеек
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Свойства ячеек в языке многомерных выражений содержат сведения о содержимом и формате ячеек многомерного источника данных, такого как куб.  
  
 В многомерных выражениях поддерживается ключевое слово CELL PROPERTIES инструкции многомерных выражений SELECT, которое служит для обращения к внутренним свойствам ячеек. Внутренние свойства ячеек чаще всего применяются для наглядного представления данных ячейки.  
  
## <a name="cell-properties-keyword-syntax"></a>Синтаксис ключевого слова CELL PROPERTIES  
 Для указания ключевого слова **CELL PROPERTIES** в инструкции многомерных выражений **SELECT** используется следующий синтаксис.  
  
```  
SELECT [<axis_specification>  
       [, <axis_specification>...]]  
  FROM [<cube_specification>]  
[WHERE [<slicer_specification>]]  
[<cell_props>]  
```  
  
 В следующей синтаксической конструкции демонстрируется формат значения `<cell_props>` и использование этим значением ключевого слова **CELL PROPERTIES** с одним или несколькими внутренними свойствами ячеек.  
  
```  
<cell_props> ::= CELL PROPERTIES <property> [, <property>...]  
```  
  
## <a name="supported-intrinsic-cell-properties"></a>Поддерживаемые внутренние свойства ячеек  
 В следующей таблице перечислены поддерживаемые внутренние свойства ячеек, используемые в качестве значений `<property>` .  
  
|property|Описание|  
|--------------|-----------------|  
|**ACTION_TYPE**|Битовая маска, определяющая существующие типы действий над ячейкой. Это свойство может принимать одно из следующих значений:<br /><br /> **MDACTION_TYPE_URL**<br /><br /> **MDACTION_TYPE_HTML**<br /><br /> **MDACTION_TYPE_STATEMENT**<br /><br /> **MDACTION_TYPE_DATASET**<br /><br /> **MDACTION_TYPE_ROWSET**<br /><br /> **MDACTION_TYPE_COMMANDLINE**<br /><br /> **MDACTION_TYPE_PROPRIETARY**<br /><br /> **MDACTION_TYPE_REPORT**<br /><br /> **MDACTION_TYPE_DRILLTHROUGH**<br /><br /> <br /><br /> Примечание. Действия детализации не поддерживаются для запросов, содержащих набор в предложении WHERE.|  
|**BACK_COLOR**|Цвет фона при отображении свойства **VALUE** или **FORMATTED_VALUE**. Дополнительные сведения см. в разделе [Свойства ячеек FORE_COLOR и BACK_COLOR (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|**CELL_ORDINAL**|Порядковый номер ячейки в наборе данных.|  
|**FONT_FLAGS**|Битовая маска, определяющая стиль шрифта. Значение представляет собой результат побитовой операции OR над одной или несколькими следующими константами.<br /><br /> **MDFF_BOLD** = 1<br /><br /> **MDFF_ITALIC** = 2<br /><br /> **MDFF_UNDERLINE** = 4<br /><br /> **MDFF_STRIKEOUT** = 8<br /><br /> <br /><br /> Например, значение 5 соответствует комбинации полужирного (**MDFF_BOLD**) и подчеркнутого (**MDFF_UNDERLINE**) стилей.|  
|**FONT_NAME**|Название шрифта, используемого для отображения свойства **VALUE** или **FORMATTED_VALUE** .|  
|**FONT_SIZE**|Размер шрифта, используемого для отображения свойства **VALUE** или **FORMATTED_VALUE** .|  
|**FORE_COLOR**|Цвет переднего плана для отображения свойства **VALUE** или **FORMATTED_VALUE**. Дополнительные сведения см. в разделе [Свойства ячеек FORE_COLOR и BACK_COLOR (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md).|  
|**FORMAT**|То же, что и **FORMAT_STRING**.|  
|**FORMAT_STRING**|Строка формата, с помощью которой создается значение свойства **FORMATTED_VALUE**. Дополнительные сведения см. в разделе [Содержание строки FORMAT_STRING (многомерные выражения)](../../../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md).|  
|**FORMATTED_VALUE**|Символьная строка, представляющая собой форматированный вывод свойства **VALUE** .|  
|**LANGUAGE**|Локаль, к которой будет применяться **FORMAT_STRING** . **LANGUAGE** обычно используется для конвертации валют.|  
|**UPDATEABLE**|Значение, определяющее возможность обновления ячейки. Это свойство может принимать одно из следующих значений:|  
||**MD_MASK_ENABLED** (0x00000000)   Ячейку можно обновить.|  
||**MD_MASK_NOT_ENABLED** (0x10000000)   Ячейку нельзя обновить.|  
||**CELL_UPDATE_ENABLED** (0x00000001)   Ячейку можно обновить в наборе ячеек.|  
||**CELL_UPDATE_ENABLED_WITH_UPDATE** (0x00000002)   Ячейку можно обновить при помощи инструкции обновления. Операция может не выполниться, если обновляемая конечная ячейка не доступна для записи.|  
||**CELL_UPDATE_NOT_ENABLED_FORMULA** (0x10000001)   Ячейку нельзя обновить, поскольку одна из ее координат является вычисляемым элементом; ячейка была извлечена вместе с набором в предложении WHERE. Ячейку можно обновить, даже если значение ячейки зависит от формулы или от вычисляемого элемента (например, если она обрабатывается статистической функцией). В этом случае итоговое значение ячейки может не соответствовать обновленному значению, поскольку на результат влияют вычисления.|  
||**CELL_UPDATE_NOT_ENABLED_NONSUM_MEASURE** (0x10000002) Ячейку нельзя обновить, поскольку нельзя обновлять несуммарные меры (количество, минимум, максимум, число различных объектов, полуаддитивные показатели).|  
||**CELL_UPDATE_NOT_ENABLED_NACELL_VIRTUALCUBE** (0x10000003)   Ячейку нельзя обновить, так как она не существует, поскольку находится на пересечении меры и элемента измерения, не связанного с группой мер данной меры.|  
||**CELL_UPDATE_NOT_ENABLED_SECURE** (0x10000005)    Ячейку нельзя обновить, поскольку она защищена.|  
||**CELL_UPDATE_NOT_ENABLED_CALCLEVEL** (0x10000006) Зарезервировано для будущего использования.|  
||**CELL_UPDATE_NOT_ENABLED_CANNOTUPDATE** (0x10000007)   Ячейку нельзя обновить по внутренним причинам.|  
||**CELL_UPDATE_NOT_ENABLED_INVALIDDIMENSIONTYPE** (0x10000009)   Ячейку нельзя обновить, поскольку обновление не поддерживается моделью интеллектуального анализа, косвенным измерением или измерением интеллектуального анализа данных.|  
|**VALUE**|Неформатированное значение ячейки.|  
  
 Для работы с ячейками требуются только свойства ячеек **CELL_ORDINAL**, **FORMATTED_VALUE**и **VALUE** . Все внутренние или предоставленные поставщиком свойства ячеек, включая их типы данных и поддержку поставщиками, определены в наборе строк схемы **PROPERTIES** . Дополнительные сведения о наборе строк схемы **PROPERTIES** см. в разделе [Набор строк MDSCHEMA_PROPERTIES](../../../analysis-services/schema-rowsets/ole-db-olap/mdschema-properties-rowset.md).  
  
 По умолчанию, если не используется ключевое слово **CELL PROPERTIES** , возвращаются свойства ячеек **VALUE**, **FORMATTED_VALUE**и **CELL_ORDINAL** (именно в этом порядке). Если используется ключевое слово **CELL PROPERTIES** , возвращаются свойства ячеек, явно перечисленные в ключевом слове.  
  
 В следующем примере иллюстрируется использование ключевого слова **CELL PROPERTIES** в многомерном запросе.  
  
```  
SELECT  
   {[Measures].[Reseller Gross Profit]} ON COLUMNS,  
   {[Reseller].[Reseller Type].[Reseller Name].Members} ON ROWS  
FROM [Adventure Works]  
CELL PROPERTIES VALUE, FORMATTED_VALUE, FORMAT_STRING, FORE_COLOR, BACK_COLOR  
```  
  
 Свойства ячеек не возвращаются многомерными запросами, возвращающими плоские наборы строк; в этом случае каждая ячейка представляется так, как если бы возвращалось лишь свойство ячейки **FORMATTED_VALUE** .  
  
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
 [Основные принципы запросов многомерных Выражений & #40; Службы Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
