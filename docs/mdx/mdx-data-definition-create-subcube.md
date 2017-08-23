---
title: "Инструкция CREATE SUBCUBE (многомерные Выражения) | Документы Microsoft"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_SUBCUBE
- CREATE SUBCUBE
- CREATE
- SUBCUBE
dev_langs:
- kbMDX
helpviewer_keywords:
- subcubes [MDX]
- CREATE SUBCUBE statement
ms.assetid: 15b6ac4c-b68a-4f9f-b33c-f5f7c4a74535
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b7a444247915755ca1e9d002acf868a7d6eecc4f
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---create-subcube"></a>Определения данных многомерных Выражений — Создание вложенного КУБА
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
 В разделе [ВЫБЕРИТЕ оператор &#40; Многомерные Выражения &#41; ](../mdx/mdx-data-manipulation-select.md) для подробные сведения о синтаксисе инструкций Select и **НЕВИЗУАЛЬНЫЕ** предложения.  
  
## <a name="remarks"></a>Замечания  
 Если элементы по умолчанию исключаются из определения вложенного куба, то координаты изменяются соответствующим образом. Для атрибутов, которые могут быть статистически вычислены, элемент по умолчанию перемещается в элемент [Все]. Для атрибутов, которые не могут быть статистически вычислены, элемент по умолчанию перемещается в элемент, существующий во вложенном кубе. В следующей таблице приведен пример вложенного куба и комбинаций элемента по умолчанию.  
  
|Исходный элемент по умолчанию|Статистически вычисляемый|Подзапрос выборки|Измененный элемент по умолчанию|  
|-----------------------------|-----------------------|---------------|----------------------------|  
|Время.Год.Все|Да|{Время.Год.2003}|Изменений нет|  
|Время.год. [1997]|Да|{Время.Год.2003}|Время.Год.Все|  
|Время.год. [1997]|Нет|{Время.Год.2003}|Время.год. [2003]|  
|Время.год. [1997]|Да|{Время.Год.2003, Время.Год.2004}|Время.Год.Все|  
|Время.год. [1997]|Нет|{Время.Год.2003, Время.Год.2004}|Или Время.Год.[2003] или<br /><br /> Время.Год.[2004]|  
  
 Во вложенном кубе всегда существуют элементы [Все].  
  
 Объекты сеанса, созданные в контексте вложенного куба, сбрасываются при сбрасывании вложенного куба.  
  
 Дополнительные сведения о вложенных кубах см. в разделе [построение вложенных кубов в многомерных Выражений &#40; Многомерные Выражения &#41; ](../analysis-services/multidimensional-models/mdx/building-subcubes-in-mdx-mdx.md).  
  
## <a name="example"></a>Пример  
 В следующем примере создается вложенный куб, ограничивающий видимое пространство куба до элементов со страной Canada. Затем он использует **ЧЛЕНЫ** функция возвращает все элементы «Страна» уровня в пользовательской иерархии - возврат страной Canada.  
  
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
||All Products|Accessories|Clothing|  
|All Resellers|$2,031,079.39|$ 506 172,45|$ 1 524 906,93|  
|Value Added Reseller|$767,388.52|$ 175 002,81|$ 592 385,71|  
|Warehouse|$1,263,690.86|$ 331 169,64|$ 932 521,23|  
  
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
||All Products|Accessories|Clothing|  
|All Resellers|$ 80 450 596,98|$ 571 297,93|$ 1 777 840,84|  
|Value Added Reseller|$ 34 967 517,33|$ 175 002,81|$ 592 385,71|  
|Warehouse|$ 38 726 913,48|$ 331 169,64|$ 932 521,23|  
  
 [All Products] и [All Resellers], столбец и строка соответственно, содержат итоги всех элементов, а не только тех, что видимы.  
  
## <a name="see-also"></a>См. также:  
 [Ключевые понятия многомерных Выражений &#40; Службы Analysis Services &#41;](../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [Инструкции сценариев многомерных Выражений &#40; Многомерные Выражения &#41;](../mdx/mdx-scripting-statements-mdx.md)   
 [Инструкция DROP SUBCUBE &#40; Многомерные Выражения &#41;](../mdx/mdx-data-definition-drop-subcube.md)   
 [Инструкция SELECT &#40; Многомерные Выражения &#41;](../mdx/mdx-data-manipulation-select.md)  
  
  

