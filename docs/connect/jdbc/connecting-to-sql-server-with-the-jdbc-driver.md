---
title: "Подключение к SQL Server с помощью драйвера JDBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 94bcfbe3-f00e-4774-bda8-bb7577518fec
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1ebc9542e5683eb58c198745892916893f284822
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-to-sql-server-with-the-jdbc-driver"></a>Соединение с SQL Server с помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Один из самых основных операций, выполняемых с помощью [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] является установление соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Взаимодействие с базой данных происходит через [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) объекта, и за простой архитектуры драйвера JDBC практически все полезные операции выполняются через объект SQLServerConnection.  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] — прослушивает только порт IPv6, установите системное свойство java.net.preferIPv6Addresses, чтобы убедиться в том, что IPv6 используется вместо IPv4 для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
```  
System.setProperty("java.net.preferIPv6Addresses", "true");  
```  
  
 В этом разделе описываются способы сделать и работать с подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Построение URL-адрес подключения](../../connect/jdbc/building-the-connection-url.md)|Описывает, как URL-адрес для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Также описывает подключение к именованным экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.|  
|[Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md)|Описывает различные свойства соединения и как они могут использоваться при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.|  
|[Установка свойств источника данных](../../connect/jdbc/setting-the-data-source-properties.md)|Описывает, как использовать источники данных на платформе Java, в среде Enterprise Edition (Java EE).|  
|[Работа с соединением](../../connect/jdbc/working-with-a-connection.md)|Описывает различные способы создания экземпляра соединения с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных.|  
|[Использование пулов соединений](../../connect/jdbc/using-connection-pooling.md)|Описывает, как драйвер JDBC поддерживает использование пулов соединений.|  
|[Использование зеркального отображения базы данных &#40; JDBC &#41;](../../connect/jdbc/using-database-mirroring-jdbc.md)|Описывает, как драйвер JDBC поддерживает использование зеркального отображения базы данных.|  
|[Драйвер JDBC поддерживает высокий уровень доступности и аварийного восстановления](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)|Описывает разработку приложения, устанавливающего соединения с группой доступности AlwaysOn.|  
|[С помощью встроенной проверки подлинности Kerberos для подключения к SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)|Обсуждает реализацию на языке Java приложений для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью встроенной проверки подлинности Kerberos.|  
|[Подключение к базе данных Azure SQL](../../connect/jdbc/connecting-to-an-azure-sql-database.md)|Обсуждает вопросы подключения к базам данных в SQL Azure.|  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

