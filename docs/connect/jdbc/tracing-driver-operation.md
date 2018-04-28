---
title: Трассировка операций драйвера | Документы Microsoft
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
ms.topic: article
ms.assetid: 723aeae7-6504-4585-ba8b-3525115bea8b
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ea02f1c06e942933fa7add21888447664e3608f3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="tracing-driver-operation"></a>Трассировка операций драйвера
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Поддерживает использование трассировки (или ведение журнала), помогающие решать проблемы с драйвером JDBC при использовании в приложении. Чтобы включить использование трассировки, драйвер JDBC использует API-интерфейсы ведения журнала в java.util.logging, который предоставляет набор классов для создания объектов средство ведения журнала и LogRecord.  
  
> [!NOTE]  
>  Для собственного компонента (sqljdbc_xa.dll), который включен в комплект драйвера JDBC, трассировка включается стандартом BID. Сведения о BID см. в разделе [трассировка доступа к данным в SQL Server](http://go.microsoft.com/fwlink/?LinkId=70042).  
  
 При разработке приложения, можно выполнять вызовы объектов средства ведения журнала, которые в свою очередь создают объекты LogRecord, которые затем передаются объекты обработчика для обработки. Средство ведения журнала и обработчик объектами обоих уровней ведения журнала, и при необходимости фильтры ведения журнала для регулирования какие LogRecords обрабатываются. Когда операции ведения журнала завершены, объекты обработчика могут также использовать модуль форматирования объекты для публикации информации журнала.  
  
 По умолчанию, среда java.util.logging записывает выходные данные в файл. Файл журнала с выходными данными должен иметь разрешения записи для контекста, в рамках которого работает драйвер JDBC.  
  
> [!NOTE]  
>  Дополнительные сведения об использовании различных объектов ведения журнала для отслеживания программ см. в разделе API-интерфейсы ведения журнала Java документации на веб-сайте Sun Microsystems.  
  
 В следующих разделах приводится описание уровней ведения журнала и категорий, которые могут быть занесены в журнал, а также включение трассировки в приложении.  
  
## <a name="logging-levels"></a>Уровни ведения журнала  
 Каждое создаваемое сообщение журнала имеет связанный уровень ведения журнала. Уровень ведения журнала определяет важность сообщения журнала, который определяется **уровень** класса в java.util.logging. Включение ведения журнала на одном уровне также включает ведение журнала на всех более высоких уровнях. В данном разделе приводится описание уровней ведения журнала как для открытых категорий ведения журнала, так и для внутренних. Дополнительные сведения о категориях ведения журнала см. в подразделе "Категории ведения журнала" данного раздела.  
  
 В следующей таблице приводится описание каждого из доступных уровней ведения журнала для открытых категорий ведения журнала.  
  
|Название|Описание|  
|----------|-----------------|  
|SEVERE|Указывает серьезный сбой и имеет самый высокий уровень ведения журнала. В драйвере JDBC этот уровень используется для выдачи ошибок и исключений.|  
|WARNING|Указывает на возможную проблему.|  
|INFO|Предоставляет информационные сообщения.|  
|CONFIG|Предоставляет сообщения о конфигурации. Обратите внимание, что драйвер JDBC в настоящий момент не предоставляет сообщений о конфигурации.|  
|FINE|Обеспечивает базовую информацию об отслеживании, включая все исключения, возникшие по вине открытых методов.|  
|FINER|Предоставляет подробные данные трассировки, включая все входные и выходные точки открытых методов с типами данных связанных параметров, а также все открытые свойства для открытых классов. Кроме того, входные параметры, выходные параметры и возвращаемые значения метода, за исключением CLOB, BLOB, NCLOB, Reader, \<поток > значение типы возвращаемых значений.|  
|FINEST|Обеспечивает наивысший уровень детализации данных трассировки. Это самый низкий уровень ведения журнала.|  
|OFF|Отключает ведение журнала.|  
|ALL|Включает регистрацию в журнале всех сообщений.|  
  
 В следующей таблице приводится описание каждого из доступных уровней ведения журнала для внутренних категорий ведения журнала.  
  
|Название|Описание|  
|----------|-----------------|  
|SEVERE|Указывает серьезный сбой и имеет самый высокий уровень ведения журнала. В драйвере JDBC этот уровень используется для выдачи ошибок и исключений.|  
|WARNING|Указывает на возможную проблему.|  
|INFO|Предоставляет информационные сообщения.|  
|FINE|Обеспечивает информацию о трассировке, включая создание и удаление базового объекта. Помимо этого, все исключения, возникшие по вине открытых методов.|  
|FINER|Предоставляет подробные данные трассировки, включая все входные и выходные точки открытых методов с типами данных связанных параметров, а также все открытые свойства для открытых классов. Кроме того, входные параметры, выходные параметры и возвращаемые значения метода, за исключением CLOB, BLOB, NCLOB, Reader, \<поток > значение типы возвращаемых значений.<br /><br /> Следующие категории ведения журнала существовали в версии 1.2 драйвера JDBC и имели уровень ведения журнала FINE: [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md), [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), XA, а [SQLServerDataSource ](../../connect/jdbc/reference/sqlserverdatasource-class.md). С версии 2.0 эти категории обновлены до уровня FINER.|  
|FINEST|Обеспечивает наивысший уровень детализации данных трассировки. Это самый низкий уровень ведения журнала.<br /><br /> Следующие категории ведения журнала существовали в версии 1.2 драйвера JDBC и имели уровень ведения журнала FINEST: TDS.DATA и TDS.TOKEN. Начиная с версии 2.0, эти категории сохраняют уровень ведения журнала FINEST.|  
|OFF|Отключает ведение журнала.|  
|ALL|Включает регистрацию в журнале всех сообщений.|  
  
## <a name="logging-categories"></a>Категории ведения журнала  
 При создании объекта средства ведения журнала, следует указать объекту именованную сущность или категорию, которые нужно получать сведения журнала из. Драйвер JDBC поддерживает следующие открытые категории ведения журнала, определенные в пакете драйвера com.microsoft.sqlserver.jdbc.  
  
|Название|Описание|  
|----------|-----------------|  
|Соединение|Регистрирует сообщения в [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. Приложение может задать уровень ведения журнала FINER.|  
|.|Регистрирует сообщения в [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. Приложение может задать уровень ведения журнала FINER.|  
|DataSource|Регистрирует сообщения в [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
|ResultSet|Регистрирует сообщения в [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса. Приложение может задать уровень ведения журнала FINER.|  
|Драйвер|Регистрирует сообщения в [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md) класса. Приложение может задать уровень ведения журнала FINER.|  
  
 Начиная с версии 2.0 драйвера Microsoft JDBC, драйвер также обеспечивает пакет com.microsoft.sqlserver.jdbc.internals, который включает поддержку ведения журнала для следующих внутренних категорий ведения журнала.  
  
|Название|Описание|  
|----------|-----------------|  
|AuthenticationJNI|Записывает в журнал сообщения о Windows интеграции проблем проверки подлинности (при **authenticationScheme** свойство соединения явно или неявно присвоено **NativeAuthentication**).<br /><br /> Приложение может задать уровень ведения журнала FINEST и FINE.|  
|SQLServerConnection|Регистрирует сообщения в [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. Приложение может задать уровень ведения журнала FINE и FINER.|  
|SQLServerDataSource|Регистрирует сообщения в [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md), и [SQLServerPooledConnection](../../connect/jdbc/reference/sqlserverpooledconnection-class.md) классы.<br /><br /> Приложение может задать уровень ведения журнала FINER.|  
|InputStream|Регистрирует сообщения относительно следующих типов данных: java.io.InputStream, java.io.Reader и типы данных, которые имеют описатель максимального значения, то есть типы данных varchar, nvarchar и varbinary.<br /><br /> Приложение может задать уровень ведения журнала FINER.|  
|SQLServerException|Регистрирует сообщения в [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerResultSet|Регистрирует сообщения в [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса. Приложение может задать уровень ведения журнала FINE, FINER и FINEST.|  
|SQLServerStatement|Регистрирует сообщения в [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. Приложение может задать уровень ведения журнала FINE, FINER и FINEST.|  
|XA|Регистрирует все транзакции XA в [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) класса. Приложение может задать уровень ведения журнала FINE и FINER.|  
|KerbAuthentication|Заносит в журнал сообщения, связанные с проверкой подлинности Kerberos типа 4 (когда **authenticationScheme** соединения свойству **JavaKerberos**). Приложение может задать уровень ведения журнала FINE или FINER.|  
|TDS.DATA|Регистрирует сообщения, содержащие диалог на уровне протокола TDS между драйвером и SQL Server. Подробное содержимое каждого отправленного и полученного пакета TDS вносится в журнал в виде значений ASCII или шестнадцатеричных значений. Учетные данные для входа (имена пользователей и пароли) не вносятся в журнал. Все остальные данные записываются в журнал.<br /><br /> Данная категория создает очень длинные и подробные сообщения, ее можно включить, только если установить уровень ведения журнала на FINEST.|  
|TDS.Channel|Данная категория отслеживает действия канала связи TCP с SQL Server. Вносимые в журнал сообщения включают открытие и закрытие сокета, а также операции считывания и записи. Категория также отслеживает сообщения, связанные с установкой соединения SSL с SQL Server.<br /><br /> Эта категория может быть включена, если установить уровень ведения журнала на FINE, FINER или FINEST.|  
|TDS.Writer|Эта категория отслеживает операции записи в канал TDS. Обратите внимание, что отслеживается длина записей, а не содержимое. Данная категория также отслеживает отправку сигнала на сервер, запрашивающего отмену выполнения инструкции.<br /><br /> Эта категория может быть включена только установкой уровня ведения журнала FINEST.|  
|TDS.Reader|Данная категория отслеживает операции считывания из канала TDS на уровне FINEST. На уровне FINEST отслеживание может быть очень подробным. На уровнях WARNING и SEVERE данная категория отслеживает получение драйвером недействительного протокола TDS от SQL Server до того, как драйвер закроет соединение.<br /><br /> Эта категория может быть включена, если установить уровень ведения журнала на FINER и FINEST.|  
|TDS.Command|Данная категория отслеживает переходы состояния низкого уровня и другую информацию, связанную с выполнением команд TDS, таких как [!INCLUDE[tsql](../../includes/tsql_md.md)] инструкции, курсора ResultSet, фиксации и т. д.<br /><br /> Эта категория может быть включена только установкой уровня ведения журнала FINEST.|  
|TDS.TOKEN|Данная категория вносит в журнал только токены внутри пакетов TDS и является менее подробной, чем категория TDS.DATA. Эта категория может быть включена, только если установить уровень ведения журнала на FINEST.<br /><br /> На уровне FINEST данная категория отслеживает токены TDS по мере их обработки в ответе. На уровне SEVERE данная категория отслеживает обнаружение недопустимого токена TDS.|  
|SQLServerDatabaseMetaData|Регистрирует сообщения в [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerResultSetMetaData|Регистрирует сообщения в [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerParameterMetaData|Регистрирует сообщения в [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerBlob|Регистрирует сообщения в [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerClob|Регистрирует сообщения в [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerSQLXML|Регистрирует сообщения во внутреннем классе SQLServerSQLXML. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerDriver|Регистрирует сообщения в [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerNClob|Регистрирует сообщения в [SQLServerNClob](../../connect/jdbc/reference/sqlservernclob-class.md) класса. Приложение может задать уровень ведения журнала FINE.|  
  
## <a name="enabling-tracing-programmatically"></a>Включение трассировки программным способом  
 Трассировку можно включить программно, создав объект средства ведения журнала и указав категорию для записи в журнал. Например, в следующем коде показано включение ведения журнала для инструкций SQL:  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.FINER);  
```  
  
 Чтобы отключить ведение журнала в коде, используйте следующую инструкцию:  
  
```  
logger.setLevel(Level.OFF);  
```  
  
 Чтобы регистрировать все доступные категории, используйте следующую инструкцию:  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc");  
logger.setLevel(Level.FINE);  
```  
  
 Чтобы отключить регистрацию в журнале определенной категории, используйте следующую инструкцию:  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.OFF);  
```  
  
## <a name="enabling-tracing-by-using-the-loggingproperties-file"></a>Включение трассировки при помощи файла Logging.Properties  
 Можно также включить трассировку с помощью `logging.properties` файл, который можно найти в `lib` каталог установки среды выполнения Java (JRE). Файл может быть использован для установки значений по умолчанию для журналов и обработчиков, которые будут использованы, если трассировка включена.  
  
 Ниже приведен пример настроек, которые можно задать в `logging.properties` файлов:  
  
```  
# Specify the handler, the handlers will be installed during VM startup.  
handlers= java.util.logging.FileHandler  
  
# Default global logging level.  
.level= OFF  
  
# default file output is in user's home directory.  
java.util.logging.FileHandler.pattern = %h/java%u.log  
java.util.logging.FileHandler.limit = 5000000  
java.util.logging.FileHandler.count = 20  
java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter  
java.util.logging.FileHandler.level = FINEST  
  
# Facility specific properties.  
com.microsoft.sqlserver.jdbc.level=FINEST  
  
```  
  
> [!NOTE]  
>  Можно задать свойства в `logging.properties` файла с помощью объекта LogManager, который является частью java.util.logging.  
  
## <a name="see-also"></a>См. также  
 [Диагностика проблем с драйвером JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
