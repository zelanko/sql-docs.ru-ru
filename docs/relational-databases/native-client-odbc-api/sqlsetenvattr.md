---
description: SQLSetEnvAttr
title: SQLSetEnvAttr | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLSetEnvAttr function
ms.assetid: d4114571-feca-4330-b2e4-7bfd1050b812
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4b6bcc13a62a052e31777b1fa4044a9c5ba56c96
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88420798"
---
# <a name="sqlsetenvattr"></a>SQLSetEnvAttr
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  [Справочник по программированию ODBC](https://go.microsoft.com/fwlink/?LinkId=45250) определяет способ, с помощью которого драйверы ODBC должны интерпретировать спецификации атрибута **SQLSetEnvAttr** в приложениях, разработанных с использованием API ODBC 2.*x* или ODBC 3.*x* . Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] соответствует следующим правилам.  
  
 Один из атрибутов, управляемых функцией **SQLSetEnvAttr** , указывает, нужно ли использовать пул соединений. Если пул соединений используется с ODBC-драйвером собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то параметр *DriverCompletion* должен быть установлен в значение SQL_DRIVER_NOPROMPT при подключении к [SQLDriverConnect](../../relational-databases/native-client-odbc-api/sqldriverconnect.md) или **SQLConnect**.  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLSetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=59369)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
