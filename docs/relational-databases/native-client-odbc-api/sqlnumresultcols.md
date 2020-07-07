---
title: SQLNumResultCols | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8fec604f795aacc9a65f6ebce97afec1a784c755
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86009202"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Для выполненных инструкций драйверу ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нет необходимости обращаться к серверу для сообщения о числе столбцов результирующего набора. В этом случае функция **SQLNumResultCols** не вызывает обращения к серверу. Как и функция [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) с параметром [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), вызов функции **SQLNumResultCols** для подготовленных, но не выполненных инструкций приводит к обращению к серверу.  
  
 Если инструкция или пакет инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] возвращает несколько результирующих наборов строк, можно изменить число столбцов одного результирующего набора на число столбцов в другом наборе. Функция**SQLNumResultCols** должна вызываться для каждого набора. При изменении числа столбцов приложение должно осуществить повторную привязку значений данных перед выборкой результатов строк. Дополнительные сведения об обработке запросов, возвращающих несколько результирующих наборов, см. в разделе [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Улучшения в ядре СУБД, начиная с, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] позволяют SQLNumResultCols получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, возвращаемых функцией SQLNumResultCols в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLNumResultCols](https://go.microsoft.com/fwlink/?LinkId=59359)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
