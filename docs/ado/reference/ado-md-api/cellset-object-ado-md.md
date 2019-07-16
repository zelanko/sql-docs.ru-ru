---
title: Объект Cellset (многомерные Объекты ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9524e9801f284d3dff3125b850cdd1fd32a361a3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928647"
---
# <a name="cellset-object-ado-md"></a>Объект Cellset (многомерные объекты ADO)
Представляет результаты из многомерного запроса. Это коллекция ячеек, выбираются из кубов или других наборов ячеек.  
  
## <a name="remarks"></a>Примечания  
 Данные в **набора ячеек** извлекается с использованием прямого доступа-массив. Вы можете выполнить детализацию до конкретный элемент, чтобы получить данные о этого члена. Например, следующий код возвращает заголовок первого элемента в первой позиции по оси первого набора ячеек с именем `cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Примечания  
 Нет понятия текущей ячейки в наборе ячеек. Вместо этого [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство извлекает определенный [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md) объекта из набора ячеек. Аргументы **элемент** свойство определяет, какая ячейка извлекается. Можно указать уникальный порядковый номер ячейки. Также можно получить ячейки с помощью их номера позиции по каждой оси набора ячеек. Дополнительные сведения о получении ячеек см. в разделе [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство.  
  
 С помощью коллекций, методы и свойства **набора ячеек** объекта, можно сделать следующее:  
  
-   Связать открытое соединение с **Cellset** объекта, задав его [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) свойство.  
  
-   Выполнения и получения результатов многомерных запросов с [откройте](../../../ado/reference/ado-md-api/open-method-ado-md.md) метод.  
  
-   Получить **ячейки** из **Cellset** с [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство.  
  
-   Возвращать [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) объекты, определяющие **Cellset** с [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) коллекции.  
  
-   Получить сведения об измерениях, используемое для фильтрации данных в **Cellset** с [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) свойство.  
  
-   Вернуть или задать запрос, используемый для определения **Cellset** с [источника](../../../ado/reference/ado-md-api/source-property-ado-md.md) свойство.  
  
-   Возвращает текущее состояние **Cellset** (открытым, закрытым, выполнение, или подключения) с [состояние](../../../ado/reference/ado-md-api/state-property-ado-md.md) свойство.  
  
-   Закройте открытую **Cellset** с [закрыть](../../../ado/reference/ado-md-api/close-method-ado-md.md) метод.  
  
-   Получить сведения о поставщике о **набора ячеек** с помощью стандартных ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также  
 [Пример объекта Cellset (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Коллекция axes (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Объект Cell (многомерные Объекты ADO)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
