---
title: Работа с соединением | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 400b4adb2b4812c1eed0397b93b1a1e08d0b5b39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-a-connection"></a>Работа с соединением
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В следующих разделах приведены примеры различных способов для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
> [!NOTE]  
>  При наличии проблем с подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с помощью драйвера JDBC, в разделе [Устранение неполадок подключения к](../../connect/jdbc/troubleshooting-connectivity.md) предложения по их устранению.  
  
## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>Создание соединения с помощью класса DriverManager  
 Самый простой способ создания подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных является загрузка драйвера JDBC и вызов метода getConnection класса DriverManager, как описано ниже:  
  
```  
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 По этой методике подключение к базе данных будет создано с помощью первого доступного драйвера из списка драйверов, способных успешно подсоединиться к данному URL-адресу.  
  
> [!NOTE]  
>  При использовании библиотеки классов sqljdbc4.jar приложениям не обязательно должны явно регистрировать или загружать с помощью метода Class.forName драйвер. При вызове метода getConnection класса DriverManager подходящий драйвер выбирается из набора зарегистрированных драйверов JDBC. Дополнительные сведения об использовании JDBC см. в разделе "Использование драйвера JDBC".  
  
## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>Создание соединения с помощью класса SQLServerDriver  
 Если вам нужно указать конкретный драйвер из списка драйверов для DriverManager, можно создать подключение к базе данных с помощью [подключения](../../connect/jdbc/reference/connect-method-sqlserverdriver.md) метод [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md) класса, как описано ниже:  
  
```  
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```  
  
## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>Создание соединения с помощью класса SQLServerDataSource  
 Если необходимо создать соединение с помощью [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) , можно использовать различные методы задания класса перед вызовом метода [getConnection](../../connect/jdbc/reference/getconnection-method.md) метода, как описано ниже:  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setUser("MyUserName");  
ds.setPassword("*****");  
ds.setServerName("localhost");  
ds.setPortNumber(1433);   
ds.setDatabaseName("AdventureWorks");  
Connection con = ds.getConnection();  
```  
  
## <a name="creating-a-connection-that-targets-a-very-specific-data-source"></a>Создание соединения, целью которого является конкретный источник данных  
 Создать подключение к базе данных, целью которого является конкретный источник данных, можно несколькими способами. Каждый способ зависит от свойств, задаваемых с помощью URL-адреса соединения.  
  
 Подключиться к экземпляру по умолчанию на удаленном сервере можно следующим образом:  
  
 `String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"`  
  
 Подключиться к конкретной точке на сервере можно следующим образом:  
  
 `String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"`  
  
 Подключиться к именованному экземпляру на сервере можно следующим образом:  
  
 `String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"`  
  
 Подключиться к конкретной базе данных на сервере можно следующим образом:  
  
 `String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"`  
  
 Дополнительные примеры URL-адреса соединения см. в разделе [построения URL-АДРЕСЕ соединения](../../connect/jdbc/building-the-connection-url.md).  
  
## <a name="creating-a-connection-with-a-custom-login-time-out"></a>Создание соединения с настраиваемым временем сохранения учетных данных  
 Если приходится подстраиваться под нагрузку сервера или сети, можно создать соединение с заданным временем сохранения учетных данных в секундах:  
  
 `String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"`  
  
## <a name="create-a-connection-with-application-level-identity"></a>Создание соединения с идентификацией на уровне приложения  
 Если для работы требуется ведение журнала и профилирование, то необходимо идентифицировать соединение по инициировавшему его приложению:  
  
 `String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"`  
  
## <a name="closing-a-connection"></a>Закрытие соединения  
 Подключение к базе данных можно явно закрыть путем вызова [закрыть](../../connect/jdbc/reference/close-method-sqlserverconnection.md) метод класса SQLServerConnection, как описано ниже:  
  
 `con.close();`  
  
 Это освободить ресурсы базы данных, которые использует объект SQLServerConnection или возврат соединения в пул соединений в сценариях с пулами.  
  
> [!NOTE]  
>  Вызова метода close будет также к откату любой запланированной транзакции.  
  
## <a name="see-also"></a>См. также  
 [Соединение с SQL Server с помощью драйвера JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
