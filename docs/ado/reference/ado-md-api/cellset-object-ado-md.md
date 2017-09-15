---
title: "Объект набора ячеек (ADO MD) | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- Cellset
helpviewer_keywords:
- Cellset object [ADO MD]
ms.assetid: 5e2452c0-cac0-49b2-8099-836c35794d50
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f53e9ec68a4375a9c8d07dc3937750c2e7ba3d46
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="cellset-object-ado-md"></a>Объект набора ячеек (ADO MD)
Представляет результаты многомерного запроса. Представляет коллекцию ячеек, выбранных из кубов или других наборов ячеек.  
  
## <a name="remarks"></a>Замечания  
 Данные в **ячеек** получаются с помощью прямого доступа-массив. Вы можете выполнить детализацию до конкретный элемент, чтобы получить данные о таких членов. Например, следующий код возвращает заголовок первого элемента в первой позиции на первой оси набора ячеек с именем `cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Замечания  
 Нет отсутствует понятие текущей ячейки в наборе ячеек. Вместо этого [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство извлекает определенный [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md) объект из набора ячеек. Аргументы **элемент** определения свойства ячейки, которая извлекается. Можно указать уникальный порядковый номер ячейки. Можно также получить ячейки с помощью их положение номера каждой оси набора ячеек. Дополнительные сведения о получении ячеек см. в разделе [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство.  
  
 С коллекциями, методы и свойства **ячеек** объекта, можно сделать следующее:  
  
-   Связать открытое соединение с **ячеек** , задавая его [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) свойство.  
  
-   Выполнение и получения результатов многомерных запросов с [откройте](../../../ado/reference/ado-md-api/open-method-ado-md.md) метод.  
  
-   Получить **ячейки** из **ячеек** с [элемент](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) свойство.  
  
-   Вернуть [оси](../../../ado/reference/ado-md-api/axis-object-ado-md.md) объектами, которые определяют **ячеек** с [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) коллекции.  
  
-   Получить сведения об измерениях, используемое для фильтрации данных в **ячеек** с [FilterAxis](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) свойство.  
  
-   Возвращать или указать запрос, используемый для определения **ячеек** с [источника](../../../ado/reference/ado-md-api/source-property-ado-md.md) свойство.  
  
-   Возвращает текущее состояние **ячеек** (открытым, закрытым, выполняется или соединение) с [состояние](../../../ado/reference/ado-md-api/state-property-ado-md.md) свойство.  
  
-   Закройте открытую **ячеек** с [закрыть](../../../ado/reference/ado-md-api/close-method-ado-md.md) метод.  
  
-   Получить сведения о поставщике, о **ячеек** с помощью стандартных ADO [свойства](../../../ado/reference/ado-api/properties-collection-ado.md) коллекции.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Коллекция axes (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Объект ячейки (ADO MD)](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Объект соединения (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Коллекция свойств (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
