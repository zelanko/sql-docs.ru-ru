---
description: SQLEndTran
title: SQLEndTran | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLEndTran function
ms.assetid: 95cff841-c2d5-4e1e-a18d-f3d4696a5b85
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bd11be29813d5e399d21e35f95afb56507dc165d
ms.sourcegitcommit: 04cf7905fa32e0a9a44575a6f9641d9a2e5ac0f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/07/2020
ms.locfileid: "91810590"
---
# <a name="sqlendtran"></a>SQLEndTran
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  По умолчанию драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] закрывает связанный с инструкцией курсор в момент фиксации или отката транзакции функцией **SQLEndTran** . Серверные курсоры закрываются, если они не являются статическими. Когда **SQLEndTran** производит фиксацию или откат операции, поведение курсора, связанного с инструкцией, определяется значением определяемого драйвером соединения ODBC атрибута SQL_COPT_SS_PRESERVE_CURSORS, установленного при помощи функции [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md).  
  
## <a name="see-also"></a>См. также:  
 [Сведения о реализации API ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)   
 [Функция SQLEndTran](../../odbc/reference/syntax/sqlendtran-function.md)  
  
