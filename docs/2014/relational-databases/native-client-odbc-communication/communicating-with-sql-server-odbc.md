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
ms.openlocfilehash: 5bf07f4e83cb58966b384a4bf0f523b7a1dd3881
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63032880"
---
# <a name="communicating-with-sql-server-odbc"></a>Взаимодействие с SQL Server (ODBC)
  Чтобы приложение ODBC было взаимодействовать с экземпляром [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], оно должно выделить среду и дескрипторы соединения и подключиться к источнику данных. После установки соединения приложение может отправлять запросы на сервер и обрабатывать любые результирующие наборы. После завершения использования источника данных приложение отсоединяется от источника и освобождает дескриптор соединения. Когда приложение освободит все дескрипторы соединения, оно освобождает дескриптор среды.  
  
 Приложение может соединяться с любым количеством источников данных. Приложение может использовать различные сочетания драйверов и источников данных, один драйвер и различные источники данных, или даже один драйвер для многих соединений к одному и тому же источнику данных.  
  
 Вы можете скачать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы ODBC для собственного клиента на странице [загрузки SQL Server](https://go.microsoft.com/fwlink/?LinkId=62796) на сайте MSDN.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Выделение дескриптора среды](allocating-an-environment-handle.md)  
  
-   [Выделение дескриптора соединения](allocating-a-connection-handle.md)  
  
-   [Источники данных ODBC собственного клиента SQL Server](../../integration-services/connection-manager/data-sources.md)  
  
-   [Подключение к источнику данных &#40;ODBC&#41;](connecting-to-a-data-source-odbc.md)  
  
-   [Отсоединение от источника данных](disconnecting-from-a-data-source.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md)   
 [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)  
  
  
