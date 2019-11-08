---
title: Взаимодействие с SQL Server (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, communicating with SQL Server
- ODBC applications, communicating with SQL Server
- ODBC, communicating with SQL Server
ms.assetid: cca3dcf0-2a7e-465a-84de-7ce055360eb6
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ce03a5f15e03193d708f30377996cca796eeeaa1
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73785000"
---
# <a name="communicating-with-sql-server-odbc"></a>Взаимодействие с SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для взаимодействия приложения ODBC с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]необходимо выделить среду и дескрипторы соединения и подключиться к источнику данных. После установки соединения приложение может отправлять запросы на сервер и обрабатывать любые результирующие наборы. После завершения использования источника данных приложение отсоединяется от источника и освобождает дескриптор соединения. Когда приложение освободит все дескрипторы соединения, оно освобождает дескриптор среды.  
  
 Приложение может соединяться с любым количеством источников данных. Приложение может использовать различные сочетания драйверов и источников данных, один драйвер и различные источники данных, или даже один драйвер для многих соединений к одному и тому же источнику данных.  
  
 Вы можете скачать примеры ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на странице [загрузки SQL Server](https://go.microsoft.com/fwlink/?LinkId=62796) на сайте MSDN.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Выделение дескриптора среды](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [Выделение дескриптора соединения](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [Источники данных ODBC SQL Server Native Client](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [Соединение с источником &#40;данных ODBC&#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [Отключение от источника данных](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>См. также раздел  
 [SQL Server Native Client &#40; &#41; ODBC](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  
