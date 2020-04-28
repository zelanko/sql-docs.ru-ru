---
title: Свойство примеры absolutepage (ADO) | Документация Майкрософт
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
ms.openlocfilehash: 12b2e6c6f12fc06cb223551b55cb7f9a38df9ac3
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "67921835"
---
# <a name="absolutepage-property-ado"></a>Свойство AbsolutePage (ADO)
Указывает, на какой странице находится текущая запись.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Для 32-разрядного кода задает или возвращает значение **типа Long** от 1 до числа страниц в объекте [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ([PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)) или возвращает одно из значений [поситионенум](../../../ado/reference/ado-api/positionenum.md) .  
  
 Для 64-разрядного кода используйте тип данных, который обеспечивает хранение 64-разрядного значения. Например, можно использовать либо **длинное** , либо другое значение, которое может быть 64-разрядной длиной, например дбординал. Не используйте значения **поситионенум** , так как их длина ограничена 32-разрядной.  
  
## <a name="remarks"></a>Remarks  
 Это свойство можно использовать для указания номера страницы, на которой находится текущая запись. Он использует свойство [pageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) , чтобы логически разделить общее число наборов строк объекта **Recordset** на ряд страниц, каждый из которых имеет число записей, равное **pageSize** (за исключением последней страницы, в которой может быть меньше записей). Чтобы это свойство было доступно, поставщик должен поддерживать соответствующие функциональные возможности.  
  
-   При получении или установке свойства **примеры ABSOLUTEPAGE** ADO использует свойство [примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md) и свойство [pageSize](../../../ado/reference/ado-api/pagesize-property-ado.md) следующим образом:  
  
-   Чтобы получить **примеры absolutepage**, ADO сначала извлекает **примеры AbsolutePosition**, а затем делит его на **pageSize**.  
  
-   Чтобы задать **примеры absolutepage**, ADO перемещает **примеры AbsolutePosition** следующим образом: он умножает значение **pageSize** на новое, а затем добавляет 1 **к значению** . В результате текущим положением в **наборе записей** после успешной установки **примеры absolutepage** является первая запись на этой странице.  
  
 Как и свойство **примеры AbsolutePosition** , **примеры absolutepage** является 1 и равно 1, если текущая запись является первой записью в **наборе записей**. Задайте это свойство, чтобы перейти к первой записи определенной страницы. Получение общего числа страниц из свойства **PageCount** .  
  
## <a name="applies-to"></a>Применяется к  
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также:  
 [Примеры свойств примеры absolutepage, PageCount и PageSize (Visual Basic)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Пример свойств примеры absolutepage, PageCount и PageSize (Visual c++)](../../../ado/reference/ado-api/absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство примеры AbsolutePosition (ADO)](../../../ado/reference/ado-api/absoluteposition-property-ado.md)   
 [Свойство PageCount (ADO)](../../../ado/reference/ado-api/pagecount-property-ado.md)   
 [Свойство PageSize (ADO)](../../../ado/reference/ado-api/pagesize-property-ado.md)
