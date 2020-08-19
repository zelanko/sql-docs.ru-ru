---
description: SQLExecDirect
title: SQLExecDirect | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5870593158aa49b8025fb634d6b651422a00a1c9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88428266"
---
# <a name="sqlexecdirect"></a>SQLExecDirect
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Если атрибут инструкции SQL_SOPT_SS_PARAM_FOCUS не равен 0, SQLExecDirect будет возвращать SQL_ERROR и создавать диагностическую запись с SQLSTATE = HY024 и сообщением "Недопустимое значение атрибута, SQL_SOPT_SS_PARAM_FOCUS (во время выполнения должно быть равно нулю)". Дополнительные сведения об атрибуте SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
