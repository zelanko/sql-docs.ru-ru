---
title: "Изменение формы | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reshaping previously shaped Recordset [ADO]
- data shaping [ADO], reshaping
ms.assetid: b1c965b7-3dad-4de6-9e0e-502ca8785be3
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6c15ec2a356fa1d9593de20f301fcdce44585445
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
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
  
## <a name="see-also"></a>См. также  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)
