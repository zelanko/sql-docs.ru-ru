---
title: Справочник по интерфейса (SPI) ODBC службы поставщика | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6e3d83f0aa27641c9dde164f51319a0e78d456ba
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47848722"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>Справочник по интерфейсу службы доступа (SPI) ODBC
В большинстве случаев ODBC определен интерфейс программирования (API). Функции в API, которые могут вызываться приложениями, и они должны быть реализованы внутри диспетчера драйверов и драйвер.  
  
 С появлением функция объединения соединений с учетом драйвера ODBC реализует интерфейс поставщика службы (SPI). Функции в SPI используются для обмена данными между диспетчера драйверов и драйверов. SPI функции реализуются с помощью драйвера; Диспетчер драйверов не предоставляет функции SPI к приложениям. Приложения не должны напрямую вызывать эти функции.  
  
 Включить sqlspi.h для разработки драйвера ODBC.  
  
 Этот раздел содержит следующие разделы  
  
-   [SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>См. также  
 [Разработка драйвера ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Разработка драйвера ODBC с поддержкой пула подключений](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [Организация пулов соединений диспетчера драйверов](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
