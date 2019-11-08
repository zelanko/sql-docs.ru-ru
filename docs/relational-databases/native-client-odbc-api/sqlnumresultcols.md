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
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c5ec47c112a41d579710a42c1913785d794f040c
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786038"
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для выполненных инструкций драйверу ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] нет необходимости обращаться к серверу для сообщения о числе столбцов результирующего набора. В этом случае функция **SQLNumResultCols** не вызывает обращения к серверу. Как и функция [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) с параметром [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), вызов функции **SQLNumResultCols** для подготовленных, но не выполненных инструкций приводит к обращению к серверу.  
  
 Если инструкция или пакет инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] возвращает несколько результирующих наборов строк, можно изменить число столбцов одного результирующего набора на число столбцов в другом наборе. Функция**SQLNumResultCols** должна вызываться для каждого набора. При изменении числа столбцов приложение должно осуществить повторную привязку значений данных перед выборкой результатов строк. Дополнительные сведения об обработке запросов, возвращающих несколько результирующих наборов, см. в разделе [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Улучшения в ядре СУБД, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] позволяют SQLNumResultCols получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значений, возвращаемых функцией SQLNumResultCols в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>См. также раздел  
   [функции SQLNumResultCols](https://go.microsoft.com/fwlink/?LinkId=59359)  
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
