---
title: С помощью драйвера JDBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6faaf05b-8b70-4ed2-9b44-eee5897f1cd0
caps.latest.revision: 54
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: 03423c0e7d1c95ce193f915c8e80db90b0c237fc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MTE
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-the-jdbc-driver"></a>С помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе приведены краткие указания по установлению простого соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]. Перед подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] необходимо сначала установить на локальном компьютере или на сервере, и на локальном компьютере нужно установить драйвер JDBC.  
  
## <a name="choosing-the-right-jar-file"></a>Выбор нужного JAR-файла  
 6.4 драйвера Microsoft JDBC для SQL Server предоставляет **mssql jdbc-6.4.0.jre7.jar**, **mssql jdbc-6.4.0.jre8.jar**, и **mssql jdbc-6.4.0.jre9.jar** библиотеки классов файлы, используемые в зависимости от выбранных параметров среды выполнения Java (JRE).  
 
 6.2 драйвер JDBC Microsoft SQL Server предоставляет **mssql jdbc-6.2.1.jre7.jar**, и **mssql jdbc-6.2.1.jre8.jar** использоваться в зависимости от вашей предпочтительная среда выполнения Java файлы библиотек классов Параметры среды (JRE).  
  
  Microsoft JDBC Driver 6.0 и 4.2 для SQL Server предоставляют **sqljdbc41.jar**, и **sqljdbc42.jar** использоваться в зависимости от выбранных параметров среды выполнения Java (JRE) файлы библиотек классов.  
  
 Microsoft JDBC Driver 4.1 для SQL Server предоставляет **sqljdbc41.jar** файла библиотеки классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE).  
    
 Выбор также определяет доступные функции. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="setting-the-classpath"></a>Задание пути к классам  
 Драйвер JDBC не является частью пакета SDK для Java. Если вы хотите использовать его, необходимо задать в пути к классу **sqljdbc.jar** файла, **sqljdbc4.jar** файл **sqljdbc41.jar** файл, или  **sqljdbc42.JAR** файл. Если пути к классу указать с помощью 6.2 драйвера JDBC, **mssql jdbc-6.2.1.jre7.jar** или **mssql jdbc-6.2.1.jre8.jar**. Если пути к классу указать с помощью 6.4 драйвера JDBC, **mssql jdbc-6.4.0.jre7.jar**, **mssql jdbc-6.4.0.jre8.jar** или **mssql jdbc-6.4.0.jre9.jar**. Если путь к классам отсутствует запись, приложение вызовет общее исключение «Класс не найден».  
  
### <a name="for-microsoft-jdbc-driver-64"></a>Для драйвера Microsoft JDBC 6.4.
 **Mssql jdbc-6.4.0.jre7.jar**, **mssql jdbc-6.4.0.jre8.jar** или **mssql jdbc-6.4.0.jre9.jar** файлы устанавливаются в следующий каталог:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.4.0.jre7.jar 
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.4.0.jre8.jar
 
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.4.0.jre9.jar
  
 Ниже приведен пример инструкции CLASSPATH, используемой для приложения Windows:  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.4 for SQL Server\sqljdbc_6.4\enu\mssql-jdbc-6.4.0.jre9.jar`  
  
 Ниже приведен пример инструкции CLASSPATH, используемой для приложения Unix/Linux:  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.4/enu/mssql-jdbc-6.4.0.jre9.jar`  
  
 Убедитесь, что инструкция CLASSPATH содержит только одну [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], например mssql, jdbc, 6.4.0.jre7.jar, mssql jdbc-6.4.0.jre8.jar или mssql jdbc-6.4.0.jre9.jar.   

### <a name="for-microsoft-jdbc-driver-62"></a>Для драйвера Microsoft JDBC 6.2
 **Mssql jdbc-6.2.1.jre7.jar** или **mssql jdbc-6.2.1.jre8.jar** файлы устанавливаются в следующий каталог:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.2.1.jre7.jar 
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.2.1.jre8.jar
  
 Ниже приведен пример инструкции CLASSPATH, используемой для приложения Windows:  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.2 for SQL Server\sqljdbc_6.2\enu\mssql-jdbc-6.2.1.jre8.jar`  
  
 Ниже приведен пример инструкции CLASSPATH, используемой для приложения Unix/Linux:  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.2/enu/mssql-jdbc-6.2.1.jre8.jar`  
  
 Убедитесь, что инструкция CLASSPATH содержит только одну [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], например, mssql jdbc-6.2.1.jre7.jar или mssql jdbc-6.2.1.jre8.jar.  

### <a name="for-microsoft-jdbc-driver-41-42-and-60"></a>Для драйвера Microsoft JDBC Driver 6.0, 4.1 и 4.2
 Файл sqljdbc.jar, файл sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar файла устанавливаются в следующий каталог:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc4.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc41.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc42.jar  
  
 Ниже приведен пример инструкции CLASSPATH, используемой для приложения Windows:  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.0 for SQL Server\sqljdbc_4.2\enu\sqljdbc42.jar`  
  
 Ниже приведен пример инструкции CLASSPATH, используемой для приложения Unix/Linux:  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_4.2/enu/sqljdbc42.jar`  
  
 Убедитесь, что инструкция CLASSPATH содержит только одну [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], например sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar.  
  
> [!NOTE]  
>  В системах Windows имена каталогов длиной более об именовании 8.3 или имена папок, содержащие пробелы, может вызвать проблемы с путями к классу. Если вы подозреваете таких проблем, следует временно переместить файл sqljdbc.jar, sqljdbc4.jar файл или файл sqljdbc41.jar в каталог с простым именем такие как `C:\Temp`, измените путь к классам и проверить, устранена ли проблема.  
  
### <a name="applications-that-are-run-directly-at-the-command-prompt"></a>Приложения, которые выполняются непосредственно в командной строке  
 Путь к классам настраивается в операционной системе. Добавьте sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в путь к классам системы. Кроме того, можно указать путь к классам в командной строке Java, на котором работает приложение с помощью `java -classpath` параметр.  
  
### <a name="applications-that-run-in-an-ide"></a>Приложения, которые выполняются в интегрированной среде разработки  
 Каждый поставщик интегрированных сред разработки предоставляет другой метод установки classpath в его разработки. Простое задание пути к классам в операционной системе не будет работать. Необходимо добавить sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в путь к классам интегрированной среды разработки.  
  
### <a name="servlets-and-jsps"></a>Сервлеты и JSP  
 Сервлеты и JSP выполняются в подсистемы сервлетов и JSP, например Tomcat. Путь к классам должен быть установлен в соответствии с документацией подсистемы сервлетов и JSP. Простое задание пути к классам в операционной системе не будет работать. Некоторые подсистемы сервлетов/JSP предоставляют экраны настройки, которые можно использовать для задания пути к классам подсистемы. В этом случае необходимо добавить в правильный файл JAR драйвера JDBC для существующего пути к классу подсистемы и перезапустите модуль. В остальных случаях можно развернуть драйвер, скопировав файл sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в определенный каталог, например, lib во время установки подсистемы. Путь к классам драйвера подсистемы также можно указать в файле конфигурации ядра.  
  
### <a name="enterprise-java-beans"></a>Enterprise Java Beans  
 Enterprise Java Beans (EJB) выполняются в контейнере EJB. Контейнеры EJB предоставляются различными поставщиками. Java-приложения работают в браузере, но загружаются с веб-сервера. Скопируйте sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в корень веб-сервера и укажите имя JAR-файл на вкладке архива HTML приложения, например, `<applet ... archive=sqljdbc.jar>`.  
  
## <a name="making-a-simple-connection-to-a-database"></a>Создание простого подключения к базе данных  
 Использовании библиотеки классов sqljdbc.jar приложения сначала должны зарегистрировать драйвер следующим образом:  
  
 `Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");`  
  
 После загрузки драйвера можно установить соединение с помощью URL-адрес соединения и метод getConnection класса DriverManager:  
  
```  
String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
   "databaseName=AdventureWorks;user=MyUserName;password=*****;";  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 В JDBC API 4.0 метод DriverManager.getConnection усовершенствован автоматически загружает драйверы JDBC. Таким образом приложения не требуется вызывать метод Class.forName для регистрации или загрузки драйвера при использовании sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar библиотеки классов.  
  
 При вызове метода getConnection класса DriverManager подходящий драйвер выбирается из набора зарегистрированных драйверов JDBC. файл sqljdbc4.JAR, sqljdbc41.jar или sqljdbc42.jar содержит файл «META-INF/services/java.sql.Driver», который содержит **com.microsoft.sqlserver.jdbc.SQLServerDriver** качестве зарегистрированного драйвера. Существующие приложения, которые загружают драйверы с помощью метода Class.forName, будут продолжать работать без изменений.  
  
> [!NOTE]  
>  Библиотека классов sqljdbc4.JAR, sqljdbc41.jar или sqljdbc42.jar не может использоваться с более старыми версиями среды выполнения Java (JRE). В разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) список версий JRE, поддерживаемых [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Дополнительные сведения о соединении с источниками данных и указать URL-адрес подключения см. в разделе [построения URL-АДРЕСЕ соединения](../../connect/jdbc/building-the-connection-url.md) и [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
