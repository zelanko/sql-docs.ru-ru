---
title: Назначение хранилища (ru) Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 067abcfc8aa5bfd781e6656e3ced9f9e1e573e5f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297874"
---
# <a name="assigning-storage"></a>Назначение хранилища
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Приложение может назначить хранилище для результатов перед выполнением инструкции SQL или после него. Если приложение сначала подготавливает или выполняет инструкцию SQL, оно может запросить о результирующем наборе перед назначением хранилища для результатов. Например, если результирующий набор неизвестен, приложение должно получить количество столбцов, прежде чем им можно будет назначить хранилище.  
  
 Чтобы связать хранилище для столбца данных, приложение вызывает [S'LBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)и передает его:  
  
-   Тип данных, в который будут преобразованы данные.  
  
-   Адрес выходного буфера для данных.  
  
     Приложение должно выделить этот буфер, причем буфер должен иметь достаточный размер для данных в той форме, в которую они будут преобразованы.  
  
-   Длину выходного буфера.  
  
     Это значение пропускается, если возвращаемые данные имеют фиксированную длину в C, например целое число, вещественное число или структура данных.  
  
-   Адрес буфера хранения, в который возвращается определенное число байтов доступных данных.  
  
 Приложение также может привязать столбцы результирующего набора к массивам переменных программы, обеспечивая поддержку получения строк результирующего набора поблочно. Существуют два различных типа привязки массивов.  
  
-   Привязка на уровне столбца завершается, когда каждый столбец привязан к собственному массиву переменных.  
  
     Связывание по-колонке определяется, вызывая [S'LSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с *набором attribute,* чтобы SQL_ATTR_ROW_BIND_TYPE и *ValuePtr,* установленным для SQL_BIND_BY_COLUMN. Все массивы должны содержать одинаковое количество элементов.  
  
-   Привязка на уровне строки завершается, когда все параметры в инструкции SQL привязаны как единое целое к массиву структур, которые содержат отдельные переменные для параметров.  
  
     Связывание по гребню определяется путем вызова **S'LSetStmtAttr** с *набором attribute,* чтобы SQL_ATTR_ROW_BIND_TYPE и *ValuePtr* установлен размер структуры, держащей переменные, которые будут получать столбцы набора результатов.  
  
 Приложение также указывает для атрибута SQL_ATTR_ROW_ARRAY_SIZE значение, равное количеству элементов в массивах столбцов или строк, и устанавливает значения SQL_ATTR_ROW_STATUS_PTR и SQL_ATTR_ROWS_FETCHED_PTR.  
  
## <a name="see-also"></a>См. также:  
 [Результаты обработки &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
