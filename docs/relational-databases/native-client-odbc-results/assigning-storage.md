---
title: "Назначение хранилища | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-results
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: b15ef1ebc3e6f947f361c52444b2587ff79d2fec
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="assigning-storage"></a>Назначение хранилища
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Приложение может назначить хранилище для результатов перед выполнением инструкции SQL или после него. Если приложение сначала подготавливает или выполняет инструкцию SQL, оно может запросить о результирующем наборе перед назначением хранилища для результатов. Например, если результирующий набор неизвестен, приложение должно получить количество столбцов, прежде чем им можно будет назначить хранилище.  
  
 Чтобы связать хранилище со столбцом данных, приложение вызывает [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)и передает его:  
  
-   Тип данных, в который будут преобразованы данные.  
  
-   Адрес выходного буфера для данных.  
  
     Приложение должно выделить этот буфер, причем буфер должен иметь достаточный размер для данных в той форме, в которую они будут преобразованы.  
  
-   Длину выходного буфера.  
  
     Это значение пропускается, если возвращаемые данные имеют фиксированную длину в C, например целое число, вещественное число или структура данных.  
  
-   Адрес буфера хранения, в который возвращается определенное число байтов доступных данных.  
  
 Приложение также может привязать столбцы результирующего набора к массивам переменных программы, обеспечивая поддержку получения строк результирующего набора поблочно. Существуют два различных типа привязки массивов.  
  
-   Привязка на уровне столбца завершается, когда каждый столбец привязан к собственному массиву переменных.  
  
     Привязка на уровне столбца указывается путем вызова [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с *атрибута* значение SQL_ATTR_ROW_BIND_TYPE и *ValuePtr* имеющим значение sql_bind_bind_by_column. Все массивы должны содержать одинаковое количество элементов.  
  
-   Привязка на уровне строки завершается, когда все параметры в инструкции SQL привязаны как единое целое к массиву структур, которые содержат отдельные переменные для параметров.  
  
     Привязка на уровне строки указывается путем вызова **SQLSetStmtAttr** с *атрибута* значение SQL_ATTR_ROW_BIND_TYPE и *ValuePtr* равным размеру структуры хранения столбцы набора переменных, которые будут получать результат.  
  
 Приложение также указывает для атрибута SQL_ATTR_ROW_ARRAY_SIZE значение, равное количеству элементов в массивах столбцов или строк, и устанавливает значения SQL_ATTR_ROW_STATUS_PTR и SQL_ATTR_ROWS_FETCHED_PTR.  
  
## <a name="see-also"></a>См. также:  
 [Результаты обработки &#40; ODBC &#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
