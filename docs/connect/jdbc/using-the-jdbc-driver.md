---
title: "С помощью драйвера JDBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6faaf05b-8b70-4ed2-9b44-eee5897f1cd0
caps.latest.revision: 54
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a067e98988c59de27e2c6a65775a337d58b23f9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-the-jdbc-driver"></a>Использование драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе приведены краткие указания по установлению простого соединения [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]. Перед подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] необходимо сначала установить на локальном компьютере или на сервере, и на локальном компьютере нужно установить драйвер JDBC.  
  
## <a name="choosing-the-right-jar-file"></a>Выбор нужного JAR-файла  
 6.2 драйвер JDBC Microsoft SQL Server предоставляет **mssql jdbc-6.2.1.jre7.jar**, и **mssql jdbc-6.2.1.jre8.jar** использоваться в зависимости от вашей предпочтительная среда выполнения Java файлы библиотек классов Параметры среды (JRE).  
  
  Microsoft JDBC Driver 6.0 и 4.2 для SQL Server предоставляют **sqljdbc41.jar**, и **sqljdbc42.jar** использоваться в зависимости от выбранных параметров среды выполнения Java (JRE) файлы библиотек классов.  
  
 Microsoft JDBC Driver 4.1 для SQL Server предоставляет **sqljdbc41.jar** файла библиотеки классов для использования в зависимости от выбранных параметров среды выполнения Java (JRE).  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 4.0 обеспечивает **sqljdbc.jar** и **sqljdbc4.jar** использоваться в зависимости от выбранных параметров среды выполнения Java (JRE) файлы библиотек классов.  
  
 От выбора версии драйвера также зависит набор доступных функций. Дополнительные сведения о какие файлы JAR следует выбрать см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="setting-the-classpath"></a>Задание пути к классу  
 Драйвер JDBC не входит в пакет Java SDK. Если вы хотите использовать его, необходимо задать в пути к классу **sqljdbc.jar** файла, **sqljdbc4.jar** файл **sqljdbc41.jar** файл, или  **sqljdbc42.JAR** файл. Если пути к классу указать с помощью 6.2 драйвера JDBC, **mssql jdbc-6.2.1.jre7.jar** или **mssql jdbc-6.2.1.jre8.jar**. Если запись для пути к классам отсутствует, приложение выдает общее исключение «Класс не найден».  
  
### <a name="for-microsoft-jdbc-driver-62"></a>Для драйвера Microsoft JDBC 6.2
 **Mssql jdbc-6.2.1.jre7.jar** или **mssql jdbc-6.2.1.jre8.jar** файлы устанавливаются в следующий каталог:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.2.1.jre7.jar 
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.2.1.jre8.jar
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Windows.  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.2 for SQL Server\sqljdbc_6.2\enu\mssql-jdbc-6.2.1.jre8.jar`  
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Unix/Linux.  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.2/enu/mssql-jdbc-6.2.1.jre8.jar`  
  
 Убедитесь, что инструкция CLASSPATH содержит только одну [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], например, mssql jdbc-6.2.1.jre7.jar или mssql jdbc-6.2.1.jre8.jar.  

### <a name="for-microsoft-jdbc-driver-40-41-42-and-60"></a>Для драйвера Microsoft JDBC 4.0, 4.2, 4.1 и 6.0
 Файл sqljdbc.jar file, sqljdbc4.jar file, sqljdbc41.jar или sqljdbc42.jar устанавливается в следующее расположение:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc4.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc41.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc42.jar  
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Windows.  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.0 for SQL Server\sqljdbc_4.2\enu\sqljdbc42.jar`  
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Unix/Linux.  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_4.2/enu/sqljdbc42.jar`  
  
 Убедитесь, что инструкция CLASSPATH содержит только одну [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], например sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar.  
  
> [!NOTE]  
>  В системах Windows имена каталогов, длина которых превышает оговоренный в соглашении об именовании размер 8.3, а также папки, имена которых содержат пробелы, могут вызвать проблемы с путями к классам. Если вы подозреваете таких проблем, следует временно переместить файл sqljdbc.jar, sqljdbc4.jar файл или файл sqljdbc41.jar в каталог с простым именем такие как `C:\Temp`, измените путь к классам и проверить, устранена ли проблема.  
  
### <a name="applications-that-are-run-directly-at-the-command-prompt"></a>Приложения, которые выполняются непосредственно в командной строке  
 Путь к классам настраивается в операционной системе. Добавьте sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в путь к классам в системе. Кроме того, можно указать путь к классам в командной строке Java, на котором работает приложение с помощью `java -classpath` параметр.  
  
### <a name="applications-that-run-in-an-ide"></a>Приложения, выполняющиеся в интегрированной среде разработки  
 Каждый поставщик интегрированных сред разработки предоставляет собственный метод установки classpath. Простое задание пути к классам в операционной системе не будет работать. Необходимо добавить sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в путь к классам интегрированной среды разработки.  
  
### <a name="servlets-and-jsps"></a>Сервлеты и JSP  
 Сервлеты и JSP выполняются в подсистеме сервлетов/JSP, например Tomcat. Путь к классам должен быть задан в соответствии с документацией подсистемы сервлетов и JSP. Простое задание пути к классам в операционной системе не будет работать. Некоторые подсистемы сервлетов/JSP предоставляют экраны настройки, которые можно использовать для задания пути к классам подсистемы. В этом случае необходимо добавить к существующему пути к классу подсистемы нужный JAR-файл драйвера JDBC и перезапустить подсистему. В остальных случаях можно развернуть драйвер, скопировав файл sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в определенный каталог (например, lib) во время установки подсистемы. Путь к классам драйвера подсистемы также можно задать в файле конфигурации конкретной подсистемы.  
  
### <a name="enterprise-java-beans"></a>Enterprise Java Beans  
 Компоненты Enterprise Java Beans (EJB) выполняются в контейнере EJB. Контейнеры EJB предоставляются различными поставщиками. Java-приложения работают в браузере, но загружаются с веб-сервера. Скопируйте sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в корень веб-сервера и укажите имя JAR-файл на вкладке архива HTML приложения, например, `<applet ... archive=sqljdbc.jar>`.  
  
## <a name="making-a-simple-connection-to-a-database"></a>Установление простого соединения с базой данных  
 В случае использования библиотеки классов sqljdbc.jar приложения сначала должны зарегистрировать драйвер следующим образом:  
  
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
>  Библиотеку классов sqljdbc4.JAR, sqljdbc41.jar или sqljdbc42.jar нельзя использовать с более старыми версиями среды выполнения Java. В разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) список версий JRE, поддерживаемых [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Дополнительные сведения о соединении с источниками данных и указать URL-адрес подключения см. в разделе [построения URL-АДРЕСЕ соединения](../../connect/jdbc/building-the-connection-url.md) и [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

