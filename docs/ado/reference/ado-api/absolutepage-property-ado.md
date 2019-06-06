---
title: Свойство AbsolutePage (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AbsolutePage
helpviewer_keywords:
- AbsolutePage property [ADO]
ms.assetid: ddb58a35-ec3a-423c-a504-3c65e62c23d4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c87862f97a1fc00d625542c177d85e11d0a7ad45
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2019
ms.locfileid: "66699276"
---
# <a name="absolutepage-property-ado"></a>Свойство AbsolutePage (ADO)
Указывает, на какой странице находится текущей записи.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 32-разрядного кода, задает или возвращает **Long** значение от 1 до количество страниц в [записей](../../../ado/reference/ado-api/recordset-object-ado.md) объекта ([PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)), или возвращает одно из [PositionEnum ](../../../ado/reference/ado-api/positionenum.md) значения.  
  
 Для 64-разрядного кода используйте тип данных, который предоставляет для хранения 64-разрядное значение. Например, можно использовать либо **Long** или другое значение, которое может иметь длину 64-разрядной, например DBORDINAL. Не используйте **PositionEnum** значения, поскольку они ограничены длиной в 32-разрядной.  
  
## <a name="remarks"></a>Примечания  
 Это свойство может использоваться для идентификации номер страницы, на котором расположена текущая запись. Она использует [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) свойство для логического разделения строк общее число **записей** объект в последовательности страниц, каждая из которых имеет количество записей равно **PageSize** (за исключением последней страницы, которые могут иметь меньше записей). Поставщик должен поддерживать соответствующие функциональные возможности для этого свойства доступен.  
  
-   При получении или задании **примеры AbsolutePage** свойство, ADO использует [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) свойство и [PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) свойство друг с другом, как показано ниже:  
  
-   Чтобы получить **примеры AbsolutePage**, ADO сначала извлекает **примеры AbsolutePosition**, а затем делит его с **PageSize**.  
  
-   Чтобы задать **примеры AbsolutePage**, перемещает ADO **примеры AbsolutePosition** следующим образом: она умножает **PageSize** по новому **примеры AbsolutePage** значение, а затем добавляет 1 к значению. В результате текущую позицию в **записей** после успешной установки **примеры AbsolutePage** является первой записи на данной странице.  
  
 Как и **примеры AbsolutePosition** свойство, **примеры AbsolutePage** отсчитывается от 1, и равняется 1 при первой записи в текущей записи **записей**. Установите это свойство, чтобы перейти к первой записи, определенной страницы. Получить общее число страниц из **PageCount** свойство.  
  
## <a name="applies-to"></a>Объект применения  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры AbsolutePage, PageCount и PageSize свойства пример (Visual Basic)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Примеры AbsolutePage, PageCount и PageSize пример свойства (Visual C++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)   
 [Свойство PageSize (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)
