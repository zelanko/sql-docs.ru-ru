---
title: Изменение формы | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
author: rothja
ms.author: jroth
ms.openlocfilehash: e0328b7a09f18cde0043cfbcc21d2dceb4893442
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82760940"
---
# <a name="reshaping"></a>Изменение формы данных
**Набору записей** , созданному предложением команды Shape, может быть присвоено имя *псевдонима* (обычно с ключевым словом AS). Псевдоним **набора записей** в форме может быть указан в совершенно другой команде. Это значит, что можно повторно использовать или *перерисовать*ранее сформированный **набор записей** в новой команде Shape. Для поддержки этой функции ADO предоставляет свойство, а также [изменение имени формы](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md).  
  
 Изменение формы имеет две основные функции. Первый заключается в связывании существующего **набора записей** с новым родительским **набором записей**.  
  
## <a name="example"></a>Пример  
  
```  
rs1.Open "SHAPE {select * from Customers} " & _  
         "APPEND ({select * from Orders} AS chapOrders " & _  
         "RELATE CustomerID to CustomerID)", cn  
  
rs2.Open "SHAPE {select * from Employees} " & _  
         "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn  
```  
  
 Вторая функция — включить неразбитый на разделы доступ к существующим дочерним объектам **Recordset** , используя синтаксис "Shape \< Recordset my Shape Name>".  
  
> [!NOTE]
>  Нельзя добавлять столбцы к существующему **набору записей**, изменять параметризованный **набор записей** или объекты **набора записей** в любом промежуточном предложении COMPUTE или выполнять операции агрегирования для любого потомка **набора** записей из **набора записей** , для которого выполняется изменение формы. **Набор записей** , на который выполняется изменение формы, и Новая команда Shape должны использовать одно и то же [соединение](../../../ado/reference/ado-api/connection-object-ado.md).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
