---
title: Объект набора ячеек (объекты данных ActiveX (MD)) | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67928647"
---
# <a name="cellset-object-ado-md"></a>Объект Cellset (многомерные объекты ADO)
Представляет результаты многомерного запроса. Это коллекция ячеек, выбранных из кубов или других наборы ячеек.  
  
## <a name="remarks"></a>Remarks  
 Данные в наборе **ячеек** извлекаются с помощью прямого доступа к массиву, подобного. Можно выполнить детализацию до определенного элемента, чтобы получить данные об этом элементе. Например, следующий код возвращает заголовок первого элемента в первой на первой оси в наборе ячеек с именем `cst`:  
  
```  
cst.Axes(0).Positions(0).Members(0).Caption  
```  
  
## <a name="remarks"></a>Remarks  
 Отсутствует понятие текущей ячейки в наборе ячеек. Вместо этого свойство [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) извлекает конкретный объект [ячейки](../../../ado/reference/ado-md-api/cell-object-ado-md.md) из набора ячеек. Аргументы свойства **Item** определяют, какая ячейка извлекается. Можно указать уникальное порядковое значение ячейки. Можно также извлечь ячейки, используя номера их позиций вдоль каждой оси набора ячеек. Дополнительные сведения о получении ячеек см. в описании свойства [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) .  
  
 С помощью коллекций, методов и свойств объекта набора **ячеек** можно выполнять следующие действия.  
  
-   Свяжите открытое соединение с объектом набора **ячеек** , задав свойство [ActiveConnection](../../../ado/reference/ado-md-api/activeconnection-property-ado-md.md) .  
  
-   Выполнение и получение результатов многомерного запроса с помощью метода [Open](../../../ado/reference/ado-md-api/open-method-ado-md.md) .  
  
-   Извлечение **ячейки** из набора **ячеек** со свойством [Item](../../../ado/reference/ado-md-api/item-property-ado-md-cellset.md) .  
  
-   Возвращает объекты [осей](../../../ado/reference/ado-md-api/axis-object-ado-md.md) , определяющие набор **ячеек** с коллекцией [осей](../../../ado/reference/ado-md-api/axes-collection-ado-md.md) .  
  
-   Получите сведения об измерениях, используемых для фильтрации данных в наборе **ячеек** с помощью свойства [филтераксис](../../../ado/reference/ado-md-api/filteraxis-property-ado-md.md) .  
  
-   Возвращает или задает запрос, используемый для определения набора **ячеек** с [исходным](../../../ado/reference/ado-md-api/source-property-ado-md.md) свойством.  
  
-   Возврат текущего состояния набора **ячеек** (открытие, закрытие, исполнение или соединение) со свойством [State](../../../ado/reference/ado-md-api/state-property-ado-md.md) .  
  
-   Закройте открытый набор **ячеек** с помощью метода [Close](../../../ado/reference/ado-md-api/close-method-ado-md.md) .  
  
-   Получение сведений о наборе **ячеек** со стандартной коллекцией [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) ADO для конкретного поставщика.  
  
 Этот раздел содержит следующий раздел.  
  
-   [Свойства, методы и события](../../../ado/reference/ado-md-api/cellset-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>См. также:  
 [Пример набора ячеек (Visual Basic)](../../../ado/reference/ado-md-api/cellset-example-vb.md)   
 [Коллекция осей (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)   
 [Объект Cell (объекты данных ActiveX (MD))](../../../ado/reference/ado-md-api/cell-object-ado-md.md)   
 [Объект Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
