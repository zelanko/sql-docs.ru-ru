---
title: Взаимодействие с SQL Server (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 915884866ce58346fa1257b6746c35b4f5cddc40
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085324"
---
# <a name="communicating-with-sql-server-odbc"></a>Взаимодействие с SQL Server (ODBC)
  Для приложений ODBC для связи с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], оно должно выделить дескриптор среды и соединения, а также подключения к источнику данных. После установки соединения приложение может отправлять запросы на сервер и обрабатывать любые результирующие наборы. После завершения использования источника данных приложение отсоединяется от источника и освобождает дескриптор соединения. Когда приложение освободит все дескрипторы соединения, оно освобождает дескриптор среды.  
  
 Приложение может соединяться с любым количеством источников данных. Приложение может использовать различные сочетания драйверов и источников данных, один драйвер и различные источники данных, или даже один драйвер для многих соединений к одному и тому же источнику данных.  
  
 Вы можете скачать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы собственного клиента ODBC из [загрузки SQL Server](http://go.microsoft.com/fwlink/?LinkId=62796) на портале MSDN.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Выделение дескриптора среды](allocating-an-environment-handle.md)  
  
-   [Выделение дескриптора соединения](allocating-a-connection-handle.md)  
  
-   [Источники данных ODBC SQL Server Native Client](../../integration-services/connection-manager/data-sources.md)  
  
-   [Подключение к источнику данных &#40;ODBC&#41;](connecting-to-a-data-source-odbc.md)  
  
-   [Отключение от источника данных](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>См. также  
 [Собственный клиент SQL Server &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
