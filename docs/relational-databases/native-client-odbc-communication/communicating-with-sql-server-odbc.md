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
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e24660402f2278f1d71f0729281e0009029936da
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47707142"
---
# <a name="communicating-with-sql-server-odbc"></a>Взаимодействие с SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Для приложений ODBC для связи с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], оно должно выделить дескриптор среды и соединения, а также подключения к источнику данных. После установки соединения приложение может отправлять запросы на сервер и обрабатывать любые результирующие наборы. После завершения использования источника данных приложение отсоединяется от источника и освобождает дескриптор соединения. Когда приложение освободит все дескрипторы соединения, оно освобождает дескриптор среды.  
  
 Приложение может соединяться с любым количеством источников данных. Приложение может использовать различные сочетания драйверов и источников данных, один драйвер и различные источники данных, или даже один драйвер для многих соединений к одному и тому же источнику данных.  
  
 Вы можете скачать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы собственного клиента ODBC из [загрузки SQL Server](http://go.microsoft.com/fwlink/?LinkId=62796) на портале MSDN.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Выделение дескриптора среды](../../relational-databases/native-client-odbc-communication/allocating-an-environment-handle.md)  
  
-   [Выделение дескриптора соединения](../../relational-databases/native-client-odbc-communication/allocating-a-connection-handle.md)  
  
-   [Источники данных ODBC SQL Server Native Client](../../relational-databases/native-client-odbc-communication/sql-server-native-client-odbc-data-sources.md)  
  
-   [Подключение к источнику данных &#40;ODBC&#41;](../../relational-databases/native-client-odbc-communication/connecting-to-a-data-source-odbc.md)  
  
-   [Отключение от источника данных](../../relational-databases/native-client-odbc-communication/disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../../relational-databases/native-client-odbc-api/sqlsetenvattr.md)  
  
  
