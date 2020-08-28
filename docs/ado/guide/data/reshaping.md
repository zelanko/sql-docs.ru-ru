---
description: Изменение формы данных
title: Изменение формы | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: ado
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
ms.openlocfilehash: 04c43b9fcca56959aec242f344da6ec81a825030
ms.sourcegitcommit: 18a98ea6a30d448aa6195e10ea2413be7e837e94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2020
ms.locfileid: "88979775"
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
  
 Вторая функция — включить доступ без разделов к существующим дочерним объектам **Recordset** с использованием синтаксиса Shape \<recordset reshape name> .  
  
> [!NOTE]
>  Нельзя добавлять столбцы к существующему **набору записей**, изменять параметризованный **набор записей** или объекты **набора записей** в любом промежуточном предложении COMPUTE или выполнять операции агрегирования для любого потомка **набора** записей из **набора записей** , для которого выполняется изменение формы. **Набор записей** , на который выполняется изменение формы, и Новая команда Shape должны использовать одно и то же [соединение](../../../ado/reference/ado-api/connection-object-ado.md).  
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
