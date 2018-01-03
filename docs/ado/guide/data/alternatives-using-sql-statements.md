---
title: "Альтернативы: С помощью инструкций SQL | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 00d771042d09ab9dc95a90debbaac94ac15301d5
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="alternatives-using-sql-statements"></a>Альтернативы: С помощью инструкций SQL
ADO также позволяет с помощью команд в качестве альтернативы его встроенные свойства и методы для изменения данных. В зависимости от поставщика, все операции, описанные в этом разделе также может выполняться путем передачи команды для источника данных. Например, можно использовать инструкции SQL UPDATE для изменения данных без использования **значение** свойство **поля**. Добавление новых записей в источник данных, а не метод ADO можно использовать инструкции SQL INSERT **AddNew**. Дополнительные сведения о SQL или языка обработки данных поставщика см. в документации источника данных.  
  
 Например можно передать строку SQL, содержащий инструкции DELETE в базе данных, как показано в следующем коде:  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
