---
title: "Общие сведения о многомерных схем и данных | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multidimensional schemas and data
ms.assetid: ce37fa06-c581-4d80-9a9b-c3aa66408909
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf3e8d6bebd5860df9f52236eecf4d1f287a8f9d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="overview-of-multidimensional-schemas-and-data"></a>Общие сведения о многомерных схем и данных
## <a name="understanding-multidimensional-schemas"></a>Основные сведения о схемах многомерные  
 Объект центра метаданных ADO MD *куба*, который состоит из структурированный набор связанные измерения, иерархии, уровни и элементы.  
  
 Объект *измерения* является независимых категорией данных из многомерной базы данных, производный от вашей бизнес-сущности. Измерения обычно содержит элементы для использования в качестве критериев запроса для мер базы данных.  
  
 Объект *иерархии* представляет собой путь к статистической обработки измерения. Измерение может иметь нескольких уровнях гранулярности, имеющих родительско дочерних отношений. Определяет иерархию, как связаны эти уровни.  
  
 Объект *уровень* шаг статистической обработки в иерархии. Для измерений с несколькими уровнями сведения каждый слой представляет собой уровне.  
  
 Объект *член* — это элемент данных в измерении. Как правило создайте заголовок или описания измерения базы данных, использование членов.  
  
 Кубы, представляются [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) объектов в многомерных ADO Измерения, иерархии, уровни и элементы также представлены их соответствующие объекты ADO MD: [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md), и [ Член](../../../ado/reference/ado-md-api/member-object-ado-md.md).  
  
### <a name="dimensions"></a>Измерения  
 Измерения куба зависит от бизнес-сущности и типы данных для моделирования в базе данных. Как правило каждое измерение — это точка входа независимо или механизм выбора данных.  
  
 Например, куб, содержащий данные о продажах имеет следующих пяти измерений: менеджер по продажам, Geography, время, продукты и меры. Измерение мер содержит фактические данные о продажах значения, тогда как другие измерения представляют собой способы классификации и группировать данные о продажах значения.  
  
 Измерение «География» существует следующий набор элементов:  
  
```  
{All, North America, Europe, Canada, USA, UK, Germany, Canada-West,  
Canada-East, USA-NW, USA-SW, USA-NE, USA-SE, England, Scotland,   
Wales,Ireland, Germany-North, Germany-South, Ottawa, Toronto,   
Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston,   
Shreveport, Miami, Boston, New York, London, Dover, Glasgow,   
Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin,   
Hamburg, Munich, Stuttgart}  
```  
  
### <a name="hierarchies"></a>Иерархии  
 Иерархии определяют способами, в котором можно «накоплены» или сгруппированные уровнями измерения. Измерение может иметь более одной иерархии. Естественная иерархия применяется в измерении «География»:  
  
### <a name="levels"></a>Levels  
 В измерении Geography пример, на предыдущем рисунке показаны каждая ячейка представляет уровень в иерархии.  
  
 Каждый уровень имеет набор элементов, как показано ниже:  
  
-   Мира`= {All}`  
  
-   Континенты`= {North America, Europe}`  
  
-   Странах`= {Canada, USA, UK, Germany}`  
  
-   Области`= {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}`  
  
-   Городов`= {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}`  
  
### <a name="members"></a>Члены  
 Элементы на конечном уровне иерархии не имеющие дочерних элементов и элементов на корневом уровне не имеют родительского объекта. Все другие члены имеют по крайней мере один родительский элемент и по крайней мере один дочерний. Например частичное обход дерева иерархии в измерении «География» дает следующие родительско дочерних отношений:  
  
-   `{All} (parent of) {Europe, North America}`  
  
-   `{North America} (parent of) {Canada, USA}`  
  
-   `{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}`  
  
-   `{USA-NW} (parent of) {Boise, Seattle}`  
  
 Члены могут быть объединены по одной или нескольким иерархиям на измерение. Рассмотрим измерение времени там, где есть два способа свертки на уровне года от уровня дней:  
  
 Этот пример также демонстрирует других характеристик: некоторые элементы уровня Week неделя года иерархии не отображаются на любом уровне иерархии квартал года. Таким образом в иерархии не нужно указывать все элементы измерения.  
  
## <a name="see-also"></a>См. также:  
 [Объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (многомерные данные) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Программирование с использованием ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Использование ADO с ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)

