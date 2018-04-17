---
title: Взаимодействие с SQL Server (ODBC) | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-communication
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 2563840e867c8732d91510305076f801c0d25ed9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="communicating-with-sql-server-odbc"></a>Взаимодействие с SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Для приложения ODBC для взаимодействия с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], оно должно выделить дескриптор среды и соединения, а также подсоединиться к источнику данных. После установки соединения приложение может отправлять запросы на сервер и обрабатывать любые результирующие наборы. После завершения использования источника данных приложение отсоединяется от источника и освобождает дескриптор соединения. Когда приложение освободит все дескрипторы соединения, оно освобождает дескриптор среды.  
  
 Приложение может соединяться с любым количеством источников данных. Приложение может использовать различные сочетания драйверов и источников данных, один драйвер и различные источники данных, или даже один драйвер для многих соединений к одному и тому же источнику данных.  
  
 Вы можете загрузить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы собственного клиента ODBC из [загрузки SQL Server](http://go.microsoft.com/fwlink/?LinkId=62796) на сайте MSDN.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Выделение дескриптора среды](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [Выделение дескриптора соединения](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [Источники данных ODBC SQL Server Native Client](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [Соединение с источником данных &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [Отключение от источника данных](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  
