---
title: "Выделение дескриптора среды | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-communication
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, environment handles
- ODBC applications, connections
- handles [SQL Server Native Client]
- environment handles [SQLNCLI]
ms.assetid: 15c1b428-ea6d-4672-894c-f0e289e2da3f
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1f7f5442bc8cb3a6e5443d25e196b0e4567bba3c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="allocating-an-environment-handle"></a>Выделение дескриптора среды
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Прежде чем в приложении появится возможность вызвать какую-либо функцию ODBC, необходимо инициализировать среду ODBC и выделить дескриптор среды. Это — глобальный дескриптор контекста и заполнитель для других дескрипторов в ODBC. Это делается путем вызова **SQLAllocHandle** с *HandleType* параметр значение SQL_HANDLE_ENV и *InputHandle* установленным в значение SQL_NULL_HANDLE.  
  
 После выделения дескриптора среды приложение должно установить атрибуты среды, чтобы указать, какая версия вызовов функций ODBC будет использоваться. Для использования ODBC 3. *x* , вызовите функцию [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md) с *атрибута* параметр значение SQL_ATTR_ODBC_VERSION и *ValuePtr* значение SQL_OV_ ODBC3.  
  
## <a name="see-also"></a>См. также:  
 [Взаимодействие с SQL Server &#40; ODBC &#41;](../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
  
