---
title: Инструкция CREATE CUBE (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: f137e8c377c94a60fdcfd8f1534069cef4b28f66
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68887435"
---
# <a name="mdx-data-definition---create-subcube"></a>Определение данных многомерных выражений — CREATE SUBCUBE


  Переопределяет пространство заданного куба или вложенного куба на указанный вложенный куб. Изменяет видимое пространство куба для последующих операций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
CREATE SUBCUBE Cube_Name AS Select_Statement  
                                                  | NON VISUAL ( Select_Statement )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Cube_Name*  
 Допустимое строковое выражение, обозначающее имя куба или перспективы, подлежащей ограничению. Это выражение становится именем вложенного куба.  
  
 *Select_Statement*  
 Допустимое многомерное выражение SELECT, не содержащее предложений WITH, NON EMPTY и HAVING и не запрашивающее свойства измерений и ячеек.  
  
 Подробное описание синтаксиса инструкций SELECT и **НЕвизуального** предложения см. в разделе [инструкция SELECT &#40;&#41;многомерных выражений](../mdx/mdx-data-manipulation-select.md) .  
  
## <a name="remarks"></a>Remarks  
 Если элементы по умолчанию исключаются из определения вложенного куба, то координаты изменяются соответствующим образом. Для атрибутов, которые могут быть статистически вычислены, элемент по умолчанию перемещается в элемент [Все]. Для атрибутов, которые не могут быть статистически вычислены, элемент по умолчанию перемещается в элемент, существующий во вложенном кубе. В следующей таблице приведен пример вложенного куба и комбинаций элемента по умолчанию.  
  
|Исходный элемент по умолчанию|Статистически вычисляемый|Подзапрос выборки|Измененный элемент по умолчанию|  
|-----------------------------|-----------------------|---------------|----------------------------|  
|Время.Год.Все|Да|{Время.Год.2003}|Без изменения.|  
|Time. year. [1997]|Да|{Время.Год.2003}|Время.Год.Все|  
|Time. year. [1997]|Нет|{Время.Год.2003}|Time. year. [2003]|  
|Time. year. [1997]|Да|{Время.Год.2003, Время.Год.2004}|Время.Год.Все|  
|Time. year. [1997]|Нет|{Время.Год.2003, Время.Год.2004}|Или Время.Год.[2003] или<br /><br /> Время.Год.[2004]|  
  
 Во вложенном кубе всегда существуют элементы [Все].  
  
 Объекты сеанса, созданные в контексте вложенного куба, сбрасываются при сбрасывании вложенного куба.  
  
 Дополнительные сведения о вложенных кубах см. [в разделе Создание вложенных кубов в многомерных выражениях &#40;многомерных выражениях&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx).  
  
## <a name="example"></a>Пример  
 В следующем примере создается вложенный куб, ограничивающий видимое пространство куба до элементов со страной Canada. Затем она использует функцию **Members** для возврата всех элементов уровня Country определяемой пользователем иерархии Geography — возврат только страны Канады.  
  
```  
CREATE SUBCUBE [Adventure Works] AS  
   SELECT [Geography].[Country].&[Canada] ON 0  
   FROM [Adventure Works]  
  
SELECT [Geography].[Country].[Country].MEMBERS ON 0  
   FROM [Adventure Works]  
  
```  
  
 В следующем примере создается вложенный куб, ограничивающий видимое пространство куба до элементов {Accessories, Clothing} в Products.Category и {[Value Added Reseller], [Warehouse]} в Resellers.[Business Type].  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works]`  
  
 Запрос вложенного куба для всех элементов в Products.Category и Resellers.[Business Type] со следующими многомерными выражениями:  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Выдаются следующие результаты:  
  
|||||  
|-|-|-|-|  
||Все продукты|Accessories|Clothing|  
|All Resellers|$2 031 079,39|$ 506 172,45|$ 1 524 906,93|  
|Value Added Reseller|$767 388,52|$ 175 002,81|$ 592 385,71|  
|Warehouse|$1 263 690,86|$ 331 169,64|$ 932 521,23|  
  
 В результате удаления и повторного создания вложенного куба с помощью предложения NON VISUAL создается вложенный куб, хранящий верные итоги для всех элементов в Products.Category и Resellers.[Business Type] независимо от того, являются ли они видимыми или нет.  
  
 `CREATE SUBCUBE [Adventure Works] AS`  
  
 `NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 Выполнение такого же запроса многомерного выражения, приведенного выше.  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 Выдаются следующие различные результаты:  
  
|||||  
|-|-|-|-|  
||Все продукты|Accessories|Clothing|  
|All Resellers|$ 80 450 596,98|$ 571 297,93|$ 1 777 840,84|  
|Value Added Reseller|$ 34 967 517,33|$ 175 002,81|$ 592 385,71|  
|Warehouse|$ 38 726 913,48|$ 331 169,64|$ 932 521,23|  
  
 [All Products] и [All Resellers], столбец и строка соответственно, содержат итоги всех элементов, а не только тех, что видимы.  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия в Analysis Services &#40;многомерных выражений&#41;](https://docs.microsoft.com/analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services)   
 [Инструкции скриптов многомерных выражений &#40;многомерные выражения&#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Инструкция DROP CUBE &#40;&#41;многомерных выражений](../mdx/mdx-data-definition-drop-subcube.md)   
 [Инструкция SELECT (многомерные выражения)](../mdx/mdx-data-manipulation-select.md)  
  
  
