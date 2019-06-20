---
title: 'Альтернатива: С помощью инструкций SQL | Документация Майкрософт'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c85f6ec6ce130d6bcb10db5f137a16f0cd102475
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701063"
---
# <a name="alternatives-using-sql-statements"></a>Альтернатива: использование инструкций SQL
ADO также позволяет с помощью команд в качестве альтернативы его встроенные свойства и методы для изменения данных. В зависимости от поставщика, все операции, описанные в этом разделе может также быть выполнено путем передачи команды к источнику данных. Например, можно использовать инструкции SQL UPDATE для изменения данных без использования **значение** свойство **поле**. Инструкции SQL INSERT может использоваться для добавления новых записей в источник данных, а не метод ADO **AddNew**. Дополнительные сведения о SQL или языка обработки данных поставщика см. в документации источника данных.  
  
 Например можно передать строку SQL, содержащий инструкции DELETE с базой данных, как показано в следующем коде:  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
