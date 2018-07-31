---
title: С помощью драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6faaf05b-8b70-4ed2-9b44-eee5897f1cd0
caps.latest.revision: 54
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 03ea3e895fb7d70b392e0c25372536770308049d
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "38015825"
---
# <a name="using-the-jdbc-driver"></a>Использование драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В этом разделе приведены краткие указания, как установить простое соединение с базой данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] при помощи драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]. Прежде чем подключаться к базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], необходимо установить [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] на сервер или локальный компьютер, а также установить на локальный компьютер драйвер JDBC.  
  
## <a name="choosing-the-right-jar-file"></a>Выбор нужного JAR-файла  
 Microsoft JDBC Driver 6.4 для SQL Server предоставляет **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar**, и **mssql-jdbc-6.4.0.jre9.jar** библиотеки классов файлы, используемые в зависимости от вашей предпочтительные параметры среды выполнения Java (JRE).  
 
 Microsoft JDBC Driver 6.2 для SQL Server предоставляет **mssql-jdbc-6.2.1.jre7.jar**, и **mssql-jdbc-6.2.1.jre8.jar** использоваться в зависимости от своей основной среды выполнения Java файлы библиотек классов Параметры среды (JRE).  
  
  Драйверы Microsoft JDBC Driver for SQL Server версий 6.0 и 4.2 включают файлы библиотеки классов **sqljdbc41.jar** и **sqljdbc42.jar**, используемые в зависимости от параметров вашей среды выполнения Java (JRE).  
  
 Драйвер Microsoft JDBC Driver for SQL Server версии 4.1 включает файл библиотеки классов **sqljdbc41.jar**, используемый в зависимости от параметров вашей среды выполнения Java (JRE).  
    
 От выбора версии драйвера также зависит набор доступных функций. Дополнительные сведения о какие файлы JAR следует выбрать, см. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md).  
  
## <a name="setting-the-classpath"></a>Задание пути к классу  
 Драйвер JDBC не входит в пакет Java SDK. Если вы хотите использовать его, укажите в пути к классам файл **sqljdbc.jar**, **sqljdbc4.jar**, **sqljdbc41.jar** или **sqljdbc42.jar**. Если с помощью JDBC Driver 6.2 в пути к классу **mssql-jdbc-6.2.1.jre7.jar** или **mssql-jdbc-6.2.1.jre8.jar**. Если с помощью JDBC Driver 6.4 в пути к классу **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar** или **mssql-jdbc-6.4.0.jre9.jar**. Если запись для пути к классам отсутствует, приложение выдает общее исключение «Класс не найден».  
  
### <a name="for-microsoft-jdbc-driver-64"></a>Для драйвера Microsoft JDBC Driver 6.4
 **Mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar** или **mssql-jdbc-6.4.0.jre9.jar** файлы устанавливаются в следующий каталог:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.4.0.jre7.jar 
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.4.0.jre8.jar
 
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.4.0.jre9.jar
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Windows.  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.4 for SQL Server\sqljdbc_6.4\enu\mssql-jdbc-6.4.0.jre9.jar`  
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Unix/Linux.  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.4/enu/mssql-jdbc-6.4.0.jre9.jar`  
  
 Необходимо убедиться в том, что инструкция CLASSPATH содержит только одну [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], например mssql-jdbc-6.4.0.jre7.jar, mssql-jdbc-6.4.0.jre8.jar или mssql-jdbc-6.4.0.jre9.jar.   

### <a name="for-microsoft-jdbc-driver-62"></a>Для драйвера Microsoft JDBC Driver 6.2
 **Mssql-jdbc-6.2.1.jre7.jar** или **mssql-jdbc-6.2.1.jre8.jar** файлы устанавливаются в следующий каталог:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.2.1.jre7.jar 
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \mssql-jdbc-6.2.1.jre8.jar
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Windows.  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.2 for SQL Server\sqljdbc_6.2\enu\mssql-jdbc-6.2.1.jre8.jar`  
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Unix/Linux.  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.2/enu/mssql-jdbc-6.2.1.jre8.jar`  
  
 Необходимо убедиться в том, что инструкция CLASSPATH содержит только одну [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], например mssql-jdbc-6.2.1.jre7.jar или mssql-jdbc-6.2.1.jre8.jar.  

### <a name="for-microsoft-jdbc-driver-41-42-and-60"></a>Для драйвера Microsoft JDBC Driver 6.0, 4.1 и 4.2
 Файл sqljdbc.jar file, sqljdbc4.jar file, sqljdbc41.jar или sqljdbc42.jar устанавливается в следующее расположение:  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc4.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc41.jar  
  
 \<*каталог установки*> \sqljdbc_\<*версии*>\\<*языка*> \sqljdbc42.jar  
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Windows.  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.0 for SQL Server\sqljdbc_4.2\enu\sqljdbc42.jar`  
  
 Далее представлен пример инструкции CLASSPATH, используемой для приложения Unix/Linux.  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_4.2/enu/sqljdbc42.jar`  
  
 Инструкция должна содержать только один драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], то есть sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar либо sqljdbc42.jar.  
  
> [!NOTE]  
>  В системах Windows имена каталогов, длина которых превышает оговоренный в соглашении об именовании размер 8.3, а также папки, имена которых содержат пробелы, могут вызвать проблемы с путями к классам. Если вы подозреваете такие проблемы, временно переместите файл sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в каталог с простым именем, например `C:\Temp`, измените путь к классам и проверьте, устранило ли это проблему.  
  
### <a name="applications-that-are-run-directly-at-the-command-prompt"></a>Приложения, которые выполняются непосредственно в командной строке  
 Путь к классам настраивается в операционной системе. Добавьте sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в путь к классам в системе. Вы также можете указать путь к классам в командной строке Java при запуске приложения, используя параметр `java -classpath`.  
  
### <a name="applications-that-run-in-an-ide"></a>Приложения, выполняющиеся в интегрированной среде разработки  
 Каждый поставщик интегрированных сред разработки предоставляет собственный метод установки classpath. Простое задание пути к классам в операционной системе не будет работать. Необходимо добавить sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в путь к классам интегрированной среды разработки.  
  
### <a name="servlets-and-jsps"></a>Сервлеты и JSP  
 Сервлеты и JSP выполняются в подсистеме сервлетов/JSP, например Tomcat. Путь к классам должен быть задан в соответствии с документацией подсистемы сервлетов и JSP. Простое задание пути к классам в операционной системе не будет работать. Некоторые подсистемы сервлетов/JSP предоставляют экраны настройки, которые можно использовать для задания пути к классам подсистемы. В этом случае необходимо добавить к существующему пути к классу подсистемы нужный JAR-файл драйвера JDBC и перезапустить подсистему. В остальных случаях можно развернуть драйвер, скопировав файл sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в определенный каталог (например, lib) во время установки подсистемы. Путь к классам драйвера подсистемы также можно задать в файле конфигурации конкретной подсистемы.  
  
### <a name="enterprise-java-beans"></a>Enterprise Java Beans  
 Компоненты Enterprise Java Beans (EJB) выполняются в контейнере EJB. Контейнеры EJB предоставляются различными поставщиками. Java-приложения работают в браузере, но загружаются с веб-сервера. Скопируйте sqljdbc.jar, sqljdbc4.jar или sqljdbc41.jar в корень веб-сервера и укажите имя JAR-файла в параметре "archive" HTML-тега "applet", например: `<applet ... archive=sqljdbc.jar>`.  
  
## <a name="making-a-simple-connection-to-a-database"></a>Установление простого соединения с базой данных  
 В случае использования библиотеки классов sqljdbc.jar приложения сначала должны зарегистрировать драйвер следующим образом:  
  
 `Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");`  
  
 После загрузки драйвера можно установить соединение с помощью URL-адрес соединения и метод getConnection класса DriverManager:  
  
```  
String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
   "databaseName=AdventureWorks;user=MyUserName;password=*****;";  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 В JDBC API 4.0 метод DriverManager.getConnection усовершенствован и автоматически загружает драйверы JDBC. Таким образом, приложениям не требуется вызывать метод Class.forName для регистрации или загрузки драйвера при использовании библиотеки классов sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar.  
  
 При вызове метода getConnection класса DriverManager подходящий драйвер выбирается из набора зарегистрированных драйверов JDBC. файл sqljdbc4.JAR, sqljdbc41.jar или sqljdbc42.jar включает файл «META-INF/services/java.sql.Driver», который содержит **com.microsoft.sqlserver.jdbc.SQLServerDriver** качестве зарегистрированного драйвера. Существующие приложения, которые загружают драйверы с помощью метода Class.forName, продолжат работать, не требуя изменений.  
  
> [!NOTE]  
>  Библиотеку классов sqljdbc4.JAR, sqljdbc41.jar или sqljdbc42.jar нельзя использовать с более старыми версиями среды выполнения Java. См. в разделе [требования к системе для драйвера JDBC](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md) список версий JRE, поддерживаемых [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].  
  
 Дополнительные сведения о том, как подключаться к источникам данных и указать URL-адрес подключения см. в разделе [построения URL-АДРЕСЕ соединения](../../connect/jdbc/building-the-connection-url.md) и [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
