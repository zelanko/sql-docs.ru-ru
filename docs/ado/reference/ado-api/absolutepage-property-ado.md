---
description: Свойство AbsolutePage (ADO)
title: Свойство примеры absolutepage (ADO) | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 1d735a8a61d4b62e6fa57427ecbee247d4589040
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88977245"
---
# <a name="absolutepage-property-ado"></a>Свойство AbsolutePage (ADO)
Указывает, на какой странице находится текущая запись.  
  
## <a name="settings-and-return-values"></a>Параметры и возвращаемые значения  
 Для 32-разрядного кода задает или возвращает значение **типа Long** от 1 до числа страниц в объекте [Recordset](./recordset-object-ado.md) ([PageCount](./pagecount-property-ado.md)) или возвращает одно из значений [поситионенум](./positionenum.md) .  
  
 Для 64-разрядного кода используйте тип данных, который обеспечивает хранение 64-разрядного значения. Например, можно использовать либо **длинное** , либо другое значение, которое может быть 64-разрядной длиной, например дбординал. Не используйте значения **поситионенум** , так как их длина ограничена 32-разрядной.  
  
## <a name="remarks"></a>Remarks  
 Это свойство можно использовать для указания номера страницы, на которой находится текущая запись. Он использует свойство [pageSize](./pagesize-property-ado.md) , чтобы логически разделить общее число наборов строк объекта **Recordset** на ряд страниц, каждый из которых имеет число записей, равное **pageSize** (за исключением последней страницы, в которой может быть меньше записей). Чтобы это свойство было доступно, поставщик должен поддерживать соответствующие функциональные возможности.  
  
-   При получении или установке свойства **примеры ABSOLUTEPAGE** ADO использует свойство [примеры AbsolutePosition](./absoluteposition-property-ado.md) и свойство [pageSize](./pagesize-property-ado.md) следующим образом:  
  
-   Чтобы получить **примеры absolutepage**, ADO сначала извлекает **примеры AbsolutePosition**, а затем делит его на **pageSize**.  
  
-   Чтобы задать **примеры absolutepage**, ADO перемещает **примеры AbsolutePosition** следующим образом: он умножает значение **pageSize** на новое, а затем добавляет 1 **к значению** . В результате текущим положением в **наборе записей** после успешной установки **примеры absolutepage** является первая запись на этой странице.  
  
 Как и свойство **примеры AbsolutePosition** , **примеры absolutepage** является 1 и равно 1, если текущая запись является первой записью в **наборе записей**. Задайте это свойство, чтобы перейти к первой записи определенной страницы. Получение общего числа страниц из свойства **PageCount** .  
  
## <a name="applies-to"></a>Применение  
 [Объект Recordset (ADO)](./recordset-object-ado.md)  
  
## <a name="see-also"></a>См. также  
 [Примеры свойств примеры absolutepage, PageCount и PageSize (Visual Basic)](./absolutepage-pagecount-and-pagesize-properties-example-vb.md)   
 [Пример свойств примеры absolutepage, PageCount и PageSize (Visual c++)](./absolutepage-pagecount-and-pagesize-properties-example-vc.md)   
 [Свойство примеры AbsolutePosition (ADO)](./absoluteposition-property-ado.md)   
 [Свойство PageCount (ADO)](./pagecount-property-ado.md)   
 [Свойство PageSize (ADO)](./pagesize-property-ado.md)