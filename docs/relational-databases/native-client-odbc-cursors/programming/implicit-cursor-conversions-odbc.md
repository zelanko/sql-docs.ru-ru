---
title: Неявные конверсии Курсора (ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ced726893b0f287db6b1fec7c8d16c6b844eea2b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298384"
---
# <a name="implicit-cursor-conversions-odbc"></a>Неявные преобразования курсора (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Приложения могут запросить тип курсора через [S'LSetStmtAttr,](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) а затем выполнить выписку s'L, которая не поддерживается серверными курсорами запрашиваемого типа. Звонок на **S'LExecute** или **S'LExecDirect** возвращается SQL_SUCCESS_WITH_INFO и **s'LGetDiagRec** возвращается:  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 Приложение может определить, какой тип курсора в настоящее время используется, позвонив в **SQL_CURSOR_TYPE.** Преобразование типа курсора применяется только к одной инструкции. Следующее **выполнение sLExecDirect** или **S'LExecute** будет выполнено с использованием исходных настроек курсора оператора.  
  
## <a name="see-also"></a>См. также:  
 [Курзор Программирование Подробности &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
