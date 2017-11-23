---
title: "Инструкция DRILLTHROUGH (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: DRILLTHROUGH
dev_langs: kbMDX
helpviewer_keywords:
- DRILLTHROUGH statement
- retrieving data
- data retrieval [MDX]
ms.assetid: dfa22755-0ed4-4bba-9c31-7ade26d9ebdb
caps.latest.revision: "37"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 47b26d23f9eb36edc7553c496b2143244b3ef0c5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mdx-data-manipulation---drillthrough"></a>Управление данными MDX - ДЕТАЛИЗАЦИИ
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Получает строки базовой таблицы, которые использовались для создания определенной ячейки или куба.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DRILLTHROUGH[MAXROWSUnsigned_Integer]   
      <MDX SELECT statement>   
      [RETURNSet_of_Attributes_and_Measures   
            [,Set_of_Attributes_and_Measures ...]  
      ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Unsigned_Integer*  
 Положительное целое значение.  
  
 *Инструкции многомерных Выражений SELECT*  
 Любая допустимая инструкция SELECT с многомерным выражением.  
  
 *Set_of_Attributes_and_Measures*  
 Список атрибутов и мер измерения, разделенный запятыми.  
  
## <a name="remarks"></a>Замечания  
 Сквозная детализация — это операция, в которой конечный пользователь выбирает одиночную ячейку из куба и извлекает результирующий набор из исходных данных для данной ячейки для получения более полной информации. По умолчанию результирующий набор сквозной детализации выводится из строк таблицы, на основе которых было вычислено значение выбранной ячейки куба. Для использования сквозной детализации конечными пользователями необходима поддержка этой возможности их клиентскими приложениями. В [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], результаты извлекаются прямо из хранилища MOLAP, если не запрашиваются секции или измерения ROLAP.  
  
> [!IMPORTANT]  
>  Безопасность сквозной детализации основана на общих свойствах безопасности, определенных на кубе. Если пользователь не может получить какие-то данные, используя многомерные выражения, сквозная детализация ограничит пользователя в точности таким же образом.  
  
 Многомерное выражение определяет требуемую ячейку. Значение, заданное параметром **MAXROWS** аргумент указывает максимальное число строк, которые должны быть возвращены в результирующем наборе строк.  
  
 По умолчанию максимально возвращаемое число строк — 10 000. Это означает, что если оставить **MAXROWS** не указан, будет возвращено 10 000 строк или меньше. Если это значение слишком мало для вашего сценария, можно задать **MAXROWS** более высокое значение, таких как `MAXROWS 20000`. Если оно слишком мало в целом, можно увеличить, изменив значение по умолчанию **OLAP\Query\DefaultDrillthroughMaxRows** свойства сервера. Дополнительные сведения об изменении этого свойства см. в разделе [свойства сервера в службах Analysis Services](../analysis-services/server-properties/server-properties-in-analysis-services.md).  
  
 Если не указано обратное, возвращенные столбцы включают в себя все атрибуты гранулярности всех измерений, связанных с группой заданной меры, кроме измерений «многие ко многим». Измерения куба начинаются с символа $ для отделения измерений от групп мер. **ВОЗВРАЩАЮТ** предложение используется для определения столбцов, возвращаемых запросом сквозной детализации. Следующие функции могут применяться для одного атрибута или меры по **ВОЗВРАЩАЮТ** предложения.  
  
 Name(имя_атрибута)  
 Возвращает имя указанного элемента атрибута.  
  
 UniqueName(имя_атрибута)  
 Возвращает уникальное имя указанного элемента атрибута.  
  
 Key(имя_атрибута[, N])  
 Возвращает ключ указанного элемента атрибута, где N определяет столбец в составном ключе (если он существует). Значение по умолчанию для N равно 1.  
  
 Caption(имя_атрибута)  
 Возвращает заголовок указанного элемента атрибута.  
  
 MemberValue(имя_атрибута)  
 Возвращает значение указанного элемента атрибута.  
  
 CustomRollup(имя_атрибута)  
 Возвращает пользовательскую свертку строк указанного элемента атрибута.  
  
 CustomRollupProperties(имя_атрибута)  
 Возвращает свойства пользовательской свертки строк указанного элемента атрибута.  
  
 UnaryOperator(имя_атрибута)  
 Возвращает унарный оператор указанного элемента атрибута.  
  
## <a name="example"></a>Пример  
 В следующем примере определяется ячейка для июля 2007 г. для меры Reseller Sales Amount (мера по умолчанию) для Australia. Предложение RETURN определяет дату каждой продажи, название модели продукта, имя служащего, объем продаж, размер налога и значение затрат на товар, которые лежат в основе возвращенной ячейки.  
  
```  
DRILLTHROUGH  
SELECT  
   ([Date].[Calendar].[Month].[July 2007])  
ON 0   
FROM [Adventure Works]  
WHERE [Geography].[Country].[Australia]  
RETURN   
  [$Date].[Date]  
  ,KEY([$Product].[Model Name])  
  ,NAME([$Employee].[Employee])  
  ,[Reseller Sales].[Reseller Sales Amount]  
  ,[Reseller Sales].[Reseller Tax Amount]  
  ,[Reseller Sales].[Reseller Standard Product Cost]  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции для манипулирования данными многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
