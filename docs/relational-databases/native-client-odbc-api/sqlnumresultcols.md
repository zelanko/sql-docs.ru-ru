---
title: SQLNumResultCols | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLNumResultCols function
ms.assetid: f79d8b3c-521e-4e50-a564-21d73ae5767b
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: dddc0fdfe3af66c27c2d08667813902d6d7d8c29
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlnumresultcols"></a>SQLNumResultCols
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Для выполненных инструкций [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента нет необходимости обращаться к серверу для сообщения число столбцов в результирующем наборе. В этом случае функция **SQLNumResultCols** не вызывает обращения к серверу. Как [SQLDescribeCol](../../relational-databases/native-client-odbc-api/sqldescribecol.md) и [SQLColAttribute](../../relational-databases/native-client-odbc-api/sqlcolattribute.md), вызов **SQLNumResultCols** для подготовленных, но не выполненных инструкций приводит к обращению к серверу.  
  
 Если инструкция или пакет инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] возвращает несколько результирующих наборов строк, можно изменить число столбцов одного результирующего набора на число столбцов в другом наборе. Функция**SQLNumResultCols** должна вызываться для каждого набора. При изменении числа столбцов приложение должно осуществить повторную привязку значений данных перед выборкой результатов строк. Дополнительные сведения об обработке несколько результирующих наборов возвращает см. в разделе [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Усовершенствования в компоненте database engine, начиная с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] разрешить SQLNumResultCols получать более точные описания ожидаемых результатов. Эти более точные результаты могут отличаться от значения, возвращаемые методом SQLNumResultCols в предыдущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения см. в разделе [Metadata Discovery](../../relational-databases/native-client/features/metadata-discovery.md).  
  
## <a name="see-also"></a>См. также  
 [SQLNumResultCols, функция](http://go.microsoft.com/fwlink/?LinkId=59359)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
