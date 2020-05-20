---
title: 'Альтернативы: использование инструкций SQL | Документация Майкрософт'
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
author: rothja
ms.author: jroth
ms.openlocfilehash: f1e80dd692b234b88d2b63ed0a43d956152e2e2b
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82761270"
---
# <a name="alternatives-using-sql-statements"></a>Варианты: с помощью инструкций SQL
Кроме того, ADO позволяет использовать команды в качестве альтернативы встроенным свойствам и методам для редактирования данных. В зависимости от поставщика все операции, упоминаемые в этом разделе, также можно выполнить путем передачи команд в источник данных. Например, инструкции SQL UPDATE можно использовать для изменения данных без использования свойства **value** **поля**. Инструкции SQL INSERT можно использовать для добавления новых записей в источник данных, а не для метода ADO **AddNew**. Дополнительные сведения о SQL или языке обработки данных поставщика см. в документации к источнику данных.  
  
 Например, можно передать SQL-строку, содержащую инструкцию DELETE, в базу данных, как показано в следующем коде:  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
