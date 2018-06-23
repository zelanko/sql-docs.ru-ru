---
title: Назначение хранилища | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: eb77a63cb3522d86b40742780e44a141dc0a6c15
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187756"
---
# <a name="assigning-storage"></a>Назначение хранилища
  Приложение может назначить хранилище для результатов перед выполнением инструкции SQL или после него. Если приложение сначала подготавливает или выполняет инструкцию SQL, оно может запросить о результирующем наборе перед назначением хранилища для результатов. Например, если результирующий набор неизвестен, приложение должно получить количество столбцов, прежде чем им можно будет назначить хранилище.  
  
 Чтобы связать хранилище со столбцом данных, приложение вызывает [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)и передает его:  
  
-   Тип данных, в который будут преобразованы данные.  
  
-   Адрес выходного буфера для данных.  
  
     Приложение должно выделить этот буфер, причем буфер должен иметь достаточный размер для данных в той форме, в которую они будут преобразованы.  
  
-   Длину выходного буфера.  
  
     Это значение пропускается, если возвращаемые данные имеют фиксированную длину в C, например целое число, вещественное число или структура данных.  
  
-   Адрес буфера хранения, в который возвращается определенное число байтов доступных данных.  
  
 Приложение также может привязать столбцы результирующего набора к массивам переменных программы, обеспечивая поддержку получения строк результирующего набора поблочно. Существуют два различных типа привязки массивов.  
  
-   Привязка на уровне столбца завершается, когда каждый столбец привязан к собственному массиву переменных.  
  
     Привязка на уровне столбца указывается путем вызова [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) с *атрибута* значение SQL_ATTR_ROW_BIND_TYPE и *ValuePtr* имеющим значение sql_bind_bind_by_column. Все массивы должны содержать одинаковое количество элементов.  
  
-   Привязка на уровне строки завершается, когда все параметры в инструкции SQL привязаны как единое целое к массиву структур, которые содержат отдельные переменные для параметров.  
  
     Привязка на уровне строки указывается путем вызова **SQLSetStmtAttr** с *атрибута* значение SQL_ATTR_ROW_BIND_TYPE и *ValuePtr* равным размеру структуры хранения столбцы набора переменных, которые будут получать результат.  
  
 Приложение также указывает для атрибута SQL_ATTR_ROW_ARRAY_SIZE значение, равное количеству элементов в массивах столбцов или строк, и устанавливает значения SQL_ATTR_ROW_STATUS_PTR и SQL_ATTR_ROWS_FETCHED_PTR.  
  
## <a name="see-also"></a>См. также  
 [Обработка результатов &#40;ODBC&#41;](processing-results-odbc.md)  
  
  