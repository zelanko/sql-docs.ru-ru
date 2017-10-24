---
title: "Альтернативы: С помощью инструкций SQL | Документы Microsoft"
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
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6c1d1da58832a1fbbc133c17f58d940d46f5c6e1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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

