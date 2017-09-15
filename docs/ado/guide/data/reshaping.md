---
title: "Изменение формы | Документы Microsoft"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d5264de973e4ed36cc24eb5c535576bdfa0a7228
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="reshaping"></a>Изменение формы
A **набора записей** создан с помощью предложения фигуры можно назначить команда *псевдоним* именем (обычно с ключевым словом AS). Псевдоним фигурные **записей** можно ссылаться в совершенно другой командой. То есть, можно повторно использовать, или *изменить форму*, ранее фигурные **записей** в новую команду фигуры. Для поддержки этой возможности, ADO предоставляет свойство, [изменить форму имени](../../../ado/reference/ado-api/reshape-name-property-dynamic-ado.md).  
  
 Изменение формы есть две основные функции. Первый способ связать существующий **записей** с новой родительской **записей**.  
  
## <a name="example"></a>Пример  
  
```  
rs1.Open "SHAPE {select * from Customers} " & _  
         "APPEND ({select * from Orders} AS chapOrders " & _  
         "RELATE CustomerID to CustomerID)", cn  
  
rs2.Open "SHAPE {select * from Employees} " & _  
         "APPEND (chapOrders RELATE EmployeeID to EmployeeID)", cn  
```  
  
 Вторая функция — для доступа к существующий дочерний объект не разбитого **набора записей** объекты, используя синтаксис «ФИГУРЫ \<записей переформирования имя >».  
  
> [!NOTE]
>  Невозможно добавить столбцы к существующему **набора записей**, изменить параметризованную форму **набора записей** или **набора записей** объекты в любые промежуточные предложение COMPUTE, или выполните статистические операции, для какого-либо **записей** потомком **записей** выполняется изменение формы. **Записей** преобразованию и новую фигуру команды должны использовать же [соединения](../../../ado/reference/ado-api/connection-object-ado.md).  
  
## <a name="see-also"></a>См. также:  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
