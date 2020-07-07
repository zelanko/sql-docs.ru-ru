---
title: И изменения, внесенные в журнал | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- logged vs. nonlogged modifications [SQL Server Native Client]
- columns [ODBC]
- ODBC data types, image columns
- nonlogged vs. logged modifications
- ODBC data types, text columns
- image columns [ODBC]
ms.assetid: 20aa5b27-4a2c-46e7-8356-beb0eebf4b7e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6c6e4d9a0dc937f7f4dd41e1c2acb32354a5b8e0
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86011203"
---
# <a name="logged-vs-unlogged-modifications"></a>Изменения с ведением журнала и без ведения журнала
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Приложение может запрашивать, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента не регистрирует изменения типа **Text**, **ntext**и **Image** . Однако этот режим следует использовать очень осторожно. Его следует использовать только в тех случаях, когда данные типа **Text**, **ntext**или **Image** не являются критически важными, а владельцы данных готовы выдавать возможность восстанавливать данные для повышения производительности.  
  
 Ведение журнала изменений типа **Text**, **ntext**и **Image** контролируется путем вызова [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) с параметром *атрибута* , для которого задано значение SQL_SOPT_SS_ TEXTPTR_LOGGING и *ValuePtr* задано значение либо SQL_TL_ON, либо SQL_TL_OFF.  
  
## <a name="see-also"></a>См. также  
 [Управление столбцами text и image](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
