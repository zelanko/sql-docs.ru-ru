---
description: SQLRowCount
title: SQLRowCount | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLRowCount function
ms.assetid: 967ed3d4-3d31-4485-ac92-027076ebc829
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 81d32f5f577d9c594556c477620e89435cf66226
ms.sourcegitcommit: 4d370399f6f142e25075b3714e5c2ce056b1bfd0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91869136"
---
# <a name="sqlrowcount"></a>SQLRowCount
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Если для выполнения инструкции привязаны массивы значений параметров, то функция **SQLRowCount** возвращает значение SQL_ERROR, если любое из значений параметров создаст ошибочное условие при выполнении инструкции. Через аргумент *RowCountPtr* функции значение возвращено не будет.  
  
 Приложение может воспользоваться атрибутом инструкции SQL_ATTR_PARAMS_PROCESSED_PTR для получения количества параметров, обработанных до возникновения ошибки.  
  
 Кроме этого, приложение может использовать массив значений состояния, привязанный с помощью атрибута инструкции SQL_ATTR_PARAM_STATUS_PTR, для получения массива смещений вызвавших ошибку строк параметров. Чтобы выяснить действительное число обработанных строк, приложение может просмотреть этот массив.  
  
 При [!INCLUDE[tsql](../../includes/tsql-md.md)] выполнении инструкции INSERT, Update, DELETE или MERGE с предложением OUTPUT SQLRowCount не возвращает количество строк, затронутых до тех пор, пока не будут потреблены все строки результирующего набора, сформированного предложением OUTPUT. Чтобы сконсуме эти строки, вызовите SQLFetch или SQLFetchScroll. Склресултколс возвращает значение-1, пока не будут использованы все строки результатов. После того как SQLFetch или SQLFetchScroll возвращает SQL_NO_DATA, приложение должно вызвать SQLRowCount, чтобы определить число затронутых строк перед вызовом SQLMoreResults для перехода к следующему результату.  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLRowCount](../../odbc/reference/syntax/sqlrowcount-function.md)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
