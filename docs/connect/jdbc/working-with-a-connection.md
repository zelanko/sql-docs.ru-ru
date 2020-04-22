---
title: Работа с подключением JDBC
description: Примеры различных способов соединения с базой данных SQL Server с помощью класса SQLServerConnection драйвера Microsoft JDBC Driver for SQL Server.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1253c2ec5822fef83d6da71279752202f2d93ebd
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81631954"
---
# <a name="working-with-a-connection"></a>Работа с подключением

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В следующих разделах приведены примеры различных способов соединения с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью класса [SQLServerConnection](reference/sqlserverconnection-class.md) драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].

> [!NOTE]  
> При возникновении неполадок с соединением с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью драйвера JDBC см. раздел [Профилактика подключений](troubleshooting-connectivity.md), где можно найти сведения по их устранению.

## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>Установка подключения с использованием класса DriverManager

Простейший способ соединения с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — загрузка драйвера JDBC и вызов метода getConnection класса DriverManager:

```java
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```

По этой методике подключение к базе данных будет создано с помощью первого доступного драйвера из списка драйверов, способных успешно подсоединиться к данному URL-адресу.

> [!NOTE]  
> При использовании библиотеки классов sqljdbc4.jar приложениям не обязательно явно регистрировать или загружать драйвер с помощью метода Class.forName. При вызове метода getConnection класса DriverManager подходящий драйвер выбирается из набора зарегистрированных драйверов JDBC. Дополнительные сведения об использовании JDBC см. в разделе "Использование драйвера JDBC".

## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>Установка подключения с использованием класса SQLServerDriver

Если нужно указать конкретный драйвер из списка драйверов для DriverManager, то можно создать подключение к базе данных с помощью метода [connect](reference/connect-method-sqlserverdriver.md) класса [SQLServerDriver](reference/sqlserverdriver-class.md):

```java
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```

## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>Установка подключения с использованием класса SQLServerDataSource

При необходимости создать соединение с помощью класса [SQLServerDataSource](reference/sqlserverdatasource-class.md) можно использовать различные методы задания класса, после чего вызывается метод [getConnection](reference/getconnection-method.md):

```java
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setUser("MyUserName");  
ds.setPassword("*****");  
ds.setServerName("localhost");  
ds.setPortNumber(1433);
ds.setDatabaseName("AdventureWorks");  
Connection con = ds.getConnection();  
```

## <a name="creating-a-connection-that-targets-a-specific-data-source"></a>Установка подключения, предназначенного для конкретного источника данных

Создать подключение к базе данных, целью которого является конкретный источник данных, можно несколькими способами. Каждый способ зависит от свойств, задаваемых с помощью URL-адреса соединения.

Подключиться к экземпляру по умолчанию на удаленном сервере можно следующим образом:

```java
String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"
```

Подключиться к конкретному порту на сервере можно следующим образом:

```java
String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"
```

Подключиться к именованному экземпляру на сервере можно следующим образом:

```java
String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"
```

Подключиться к конкретной базе данных на сервере можно следующим образом:

```java
String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"
```

Дополнительные примеры URL-адресов подключений см. в статье о [создании URL-адреса подключения](building-the-connection-url.md).

## <a name="creating-a-connection-with-a-custom-login-timeout"></a>Установка подключения с настраиваемым временем сохранения учетных данных

Если приходится подстраиваться под нагрузку сервера или сети, можно создать соединение с заданным временем сохранения учетных данных в секундах:

```java
String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"
```

## <a name="create-a-connection-with-application-level-identity"></a>Установка подключения с идентификацией на уровне приложения

Если для работы требуется ведение журнала и профилирование, то необходимо идентифицировать соединение по инициировавшему его приложению:

```java
String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"
```

## <a name="closing-a-connection"></a>Закрытие подключения

Подключение к базе данных можно явно закрыть путем вызова метода [close](reference/close-method-sqlserverconnection.md) класса SQLServerConnection:

```java
con.close();
```

Освобождение ресурсов базы данных, используемых объектом SQLServerConnection, или возврат соединения в пул соединений в сценариях с пулами.

> [!NOTE]  
> Вызов метода close также приведет к откату любой ожидающей выполнения транзакции.

## <a name="see-also"></a>См. также раздел

[Подключение к SQL Server с помощью JDBC Driver](connecting-to-sql-server-with-the-jdbc-driver.md)
