---
title: Соединение с SQL Server с помощью драйвера JDBC | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 94bcfbe3-f00e-4774-bda8-bb7577518fec
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2ceb6d9f5fca9a0ab6281b3caa4b95ceef5bc0b9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66789362"
---
# <a name="connecting-to-sql-server-with-the-jdbc-driver"></a>Соединение с SQL Server с помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Одной из самых основных операций, выполняемых с помощью драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], является установление соединения с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Взаимодействие с базой данных происходит через объект [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md), и в силу исключительно простой архитектуры драйвера JDBC практически все полезные операции выполняются через объект SQLServerConnection.  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает только порт IPv6, установите системное свойство java.net.preferIPv6Addresses, чтобы убедиться, что IPv6 используется для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вместо IPv4:  
  
```java
System.setProperty("java.net.preferIPv6Addresses", "true");  
```  
  
 В подразделах данного раздела приводится описание того, как устанавливается и используется соединение с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Формирование URL-адреса соединения](../../connect/jdbc/building-the-connection-url.md)|Описывает, как создать URL-адрес подключения к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Также описывает подключение к именованным экземплярам базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md)|Описывает различные свойства подключения и их применение при подключении к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Задание свойств источника данных](../../connect/jdbc/setting-the-data-source-properties.md)|Описывает, как использовать источники данных на платформе Java, в среде Enterprise Edition (Java EE).|  
|[Работа с соединением](../../connect/jdbc/working-with-a-connection.md)|Описывает различные способы создания экземпляра соединения с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|[Использование пулов соединений](../../connect/jdbc/using-connection-pooling.md)|Описывает, как драйвер JDBC поддерживает использование пулов соединений.|  
|[Использование зеркального отображения базы данных (JDBC)](../../connect/jdbc/using-database-mirroring-jdbc.md)|Описывает, как драйвер JDBC поддерживает использование зеркального отображения базы данных.|  
|[Поддержка высокой доступности и аварийного восстановления в драйвере JDBC](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)|Описывает разработку приложения, устанавливающего соединения с группой доступности AlwaysOn.|  
|[Использование встроенной проверки подлинности Kerberos для соединения с SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)|Обсуждает реализацию на языке Java приложений, соединяющихся с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при использовании встроенной проверки подлинности по протоколу Kerberos.|  
|[Подключение к базе данных SQL Azure](../../connect/jdbc/connecting-to-an-azure-sql-database.md)|Обсуждает вопросы подключения к базам данных в SQL Azure.|  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
