---
title: "Использование пулов соединений | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 699d4e8a-34bf-4c60-b0d5-4a10dad6084a
caps.latest.revision: "30"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8b0125330ff44030e354423b105710fc6806f337
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="using-connection-pooling"></a>Использование пулов соединений
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Обеспечивает поддержку платформы Java Enterprise Edition (Java EE) организация пулов соединений. В драйвере JDBC реализованы необходимые интерфейсы JDBC 3.0, что позволяет драйверу участвовать в любой реализации пулов соединений, предоставляемой поставщиками ПО промежуточного слоя и совместимой с JDBC 3.0. ПО промежуточного слоя, например серверы приложений Java EE, часто предоставляет соответствующие стандарту средства работы с пулами соединений. Драйвер JDBC сможет участвовать в соединениях из пула в таких средах.  
  
> [!NOTE]  
>  Драйвер JDBC поддерживает пулы соединений Java EE, однако не предоставляет собственную реализацию работы с пулом. Драйверу необходимо, чтобы управление соединениями осуществлялось серверами приложений Java сторонних разработчиков.  
  
## <a name="remarks"></a>Замечания  
 Далее представлены классы для реализации пулов соединений.  
  
|Class|Реализации|Description|  
|-----------|----------------|-----------------|  
|COM.Microsoft.SqlServer.JDBC. SQLServerXADataSource|javax.sql.ConnectionPoolDataSource и javax.sql.XADataSource|Мы рекомендуем использовать [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) класса для всех задач сервера Java EE требуется, так как он реализует все интерфейсы пулов JDBC 3.0 и XA.|  
|COM.Microsoft.SqlServer.JDBC. SQLServerConnectionPoolDataSource|javax.sql.ConnectionPoolDataSource|Этот класс представляет фабрику соединений, которая позволяет серверу приложений Java EE заполнять пул соединений физическими соединениями. Если конфигурация поставщика Java EE подразумевает необходимость класса, реализующего javax.sql.ConnectionPoolDataSource, укажите имя класса, как [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md). Как правило, рекомендуется использовать [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) вместо этого класса, так как он реализует интерфейсы пулов, и интерфейсы XA и проверена в несколько конфигураций сервера Java EE.|  
  
 Чтобы получить максимальную выгоду от использования пулов, в коде приложений JDBC всегда следует явно закрывать соединения. Если приложение явно закрывает соединение, реализация пулов может немедленно повторно использовать это соединение. Если соединение не закрыто, другие приложения не могут его использовать. Приложения могут использовать `finally` конструкцию, чтобы убедиться в том, что соединения закрываются даже при возникновении исключения.  
  
> [!NOTE]  
>  В текущей версии драйвер JDBC не вызывает хранимую процедуру sp_reset_connection, когда соединение возвращается в пул. Драйверу необходимо, чтобы сервера приложений Java сторонних разработчиков возвращали соединения в исходное состояние.  
  
## <a name="see-also"></a>См. также:  
 [Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
