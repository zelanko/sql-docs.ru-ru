---
title: Общие сведения о многомерных схемах и данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- multidimensional schemas and data
ms.assetid: ce37fa06-c581-4d80-9a9b-c3aa66408909
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70bd6f1867d48a9c96f5759d95c2a08a22714d8a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47811162"
---
# <a name="overview-of-multidimensional-schemas-and-data"></a>Общие сведения о многомерных схемах и данных
## <a name="understanding-multidimensional-schemas"></a>Основные сведения о многомерных схемах  
 Объект метаданных central в интерфейсе ADO MD *куба*, который состоит из набора структурированных связанные измерения, иерархии, уровни и элементы.  
  
 Объект *измерения* является независимым категорией данных из многомерной базы данных, производный от вашей бизнес-сущности. Измерение обычно содержит элементы для использования в качестве критериев запроса для мер базы данных.  
  
 Объект *иерархии* представляет собой путь к статистической обработки измерения. Измерение может иметь нескольких уровнях гранулярности, имеющих родительско дочерних отношений. Иерархии определяет, как связаны эти уровни.  
  
 Объект *уровень* является одним из этапов статистической обработки в иерархии. Для измерений с помощью нескольких уровней информации каждом слое находится на уровне.  
  
 Объект *член* представляет собой элемент данных в измерении. Как правило к созданию заголовка или описания измерения базы данных при помощи элементов.  
  
 Кубы, представляются [CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) объектов в многомерных моделей ADO Измерения, иерархии, уровни и элементы представляются также с их соответствующих объектов ADO MD: [измерения](../../../ado/reference/ado-md-api/dimension-object-ado-md.md), [иерархии](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md), [уровень](../../../ado/reference/ado-md-api/level-object-ado-md.md), и [ Член](../../../ado/reference/ado-md-api/member-object-ado-md.md).  
  
### <a name="dimensions"></a>Измерения  
 Измерения куба зависит от бизнес-сущности и типы данных, которые нужно моделировать в базе данных. Как правило каждое измерение — это точка входа независимых или механизм для выбора данных.  
  
 Например, куб, содержащий данные о продажах имеет следующих пяти измерений: менеджеров по продажам, Geography, время, продукты и меры. Измерение мер содержит значения фактические данные о продажах, тогда как другие измерения представляют собой способы классифицировать и группировать данные о продажах значения.  
  
 Измерение «География» имеет следующий набор элементов:  
  
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
 Иерархии определяют способами, в которой уровни измерения можно «накоплены» или группирования. Измерение может иметь более одной иерархии. Естественная иерархия существует в измерении Geography:  
  
### <a name="levels"></a>Levels  
 В этом измерении географии пример, изображенного на предыдущем рисунке каждая ячейка представляет уровень в иерархии.  
  
 Каждый уровень имеет набор элементов, как показано ниже:  
  
-   Всему миру `= {All}`  
  
-   Континенты `= {North America, Europe}`  
  
-   Странах `= {Canada, USA, UK, Germany}`  
  
-   Регионы `= {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}`  
  
-   Города `= {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}`  
  
### <a name="members"></a>Члены  
 Члены, на конечном уровне иерархии имеют нет дочерних элементов и элементов на корневом уровне не имеют родительского объекта. Все другие члены имеют по крайней мере один родительский элемент и по крайней мере один дочерний элемент. Например частичного обхода дерева иерархии в измерении Geography получаются следующие родительско дочерних отношений:  
  
-   `{All} (parent of) {Europe, North America}`  
  
-   `{North America} (parent of) {Canada, USA}`  
  
-   `{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}`  
  
-   `{USA-NW} (parent of) {Boise, Seattle}`  
  
 Члены могут быть объединены по одной или нескольким иерархиям, на измерение. Рассмотрим измерение времени там, где существует два способа для свертки до уровня Year уровня дней:  
  
 Этот пример также иллюстрирует другой характеристика: некоторые члены уровня Week год неделя иерархии не отображаются на любом уровне иерархии квартал года. Таким образом в иерархии не нужно указывать все элементы измерения.  
  
## <a name="see-also"></a>См. также  
 [Объектная модель ADO MD](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (многомерные данные) (многомерные Объекты ADO)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [Программирование с использованием ADO MD](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [Использование ADO с ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [Работа с многомерными данными](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
