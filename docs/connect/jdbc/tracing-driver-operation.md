---
title: Трассировка операций драйвера
description: Узнайте, как использовать трассировку для записи сведений в журнал и устранения проблем, возникающих при использовании драйвера JDBC для SQL Server.
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 723aeae7-6504-4585-ba8b-3525115bea8b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c25f97d79477497d60d458c994ef5dbdc102463d
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727543"
---
# <a name="tracing-driver-operation"></a>Трассировка операций драйвера
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает трассировку (или ведение журнала), что позволяет решать проблемы с драйвером JDBC при его использовании в приложении. Чтобы включить использование трассировки, драйвер JDBC использует интерфейсы API ведения журнала в java.util.logging, который обеспечивает набор классов для создания объектов Logger и LogRecord.  
  
> [!NOTE]  
>  Для собственного компонента (sqljdbc_xa.dll), который включен в комплект драйвера JDBC, трассировка включается стандартом BID. Дополнительные сведения о BID см. в статье [Трассировка доступа к данным в SQL Server](/previous-versions/sql/sql-server-2008/cc765421(v=sql.100)).  
  
 При разработке приложения вы можете выполнять вызовы объектов Logger, которые в свою очередь создают объекты LogRecord, передаваемые затем объектам Handler для обработки. Объекты Logger и Handler используют уровни ведения журнала и, при необходимости, фильтры ведения журнала для регулирования обрабатываемых записей журнала (LogRecord). Когда операции ведения журнала завершены, объекты Handler могут также использовать объекты Formatter для публикации данных журнала.  
  
 По умолчанию, среда java.util.logging записывает выходные данные в файл. Файл журнала с выходными данными должен иметь разрешения записи для контекста, в рамках которого работает драйвер JDBC.  
  
> [!NOTE]  
>  Дополнительные сведения об использовании различных объектов ведения журнала для отслеживания программ см. в разделе API-интерфейсы ведения журнала Java документации на веб-сайте Sun Microsystems.  
  
 В следующих разделах приводится описание уровней ведения журнала и категорий, которые могут быть занесены в журнал, а также включение трассировки в приложении.  
  
## <a name="logging-levels"></a>Уровни ведения журнала  
 Каждое создаваемое сообщение журнала имеет связанный уровень ведения журнала. Уровень ведения журнала определяет важность сообщения журнала, которая задается классом **Level** в java.util.logging. Включение ведения журнала на одном уровне также включает ведение журнала на всех более высоких уровнях. В данном разделе приводится описание уровней ведения журнала как для открытых категорий ведения журнала, так и для внутренних. Дополнительные сведения о категориях ведения журнала см. в разделе "Категории ведения журнала" этой статьи.  
  
 В следующей таблице приводится описание каждого из доступных уровней ведения журнала для открытых категорий ведения журнала.  
  
|Имя|Описание|  
|----------|-----------------|  
|SEVERE|Указывает серьезный сбой и имеет самый высокий уровень ведения журнала. В драйвере JDBC этот уровень используется для выдачи ошибок и исключений.|  
|WARNING|Указывает на возможную проблему.|  
|INFO|Предоставляет информационные сообщения.|  
|CONFIG|Предоставляет сообщения о конфигурации. Обратите внимание, что драйвер JDBC сейчас не предоставляет сообщения о конфигурации.|  
|FINE|Обеспечивает базовую информацию об отслеживании, включая все исключения, возникшие по вине открытых методов.|  
|FINER|Предоставляет подробные данные трассировки, включая все входные и выходные точки открытых методов с типами данных связанных параметров, а также все открытые свойства для открытых классов. Кроме этого, входные и выходные параметры и значения, возвращенные методами, кроме возвращаемых значений типов CLOB, BLOB, NCLOB, Reader, \<stream>.|  
|FINEST|Обеспечивает наивысший уровень детализации данных трассировки. Это самый низкий уровень ведения журнала.|  
|OFF|Отключает ведение журнала.|  
|ALL|Включает регистрацию в журнале всех сообщений.|  
  
 В следующей таблице приводится описание каждого из доступных уровней ведения журнала для внутренних категорий ведения журнала.  
  
|Имя|Описание|  
|----------|-----------------|  
|SEVERE|Указывает серьезный сбой и имеет самый высокий уровень ведения журнала. В драйвере JDBC этот уровень используется для выдачи ошибок и исключений.|  
|WARNING|Указывает на возможную проблему.|  
|INFO|Предоставляет информационные сообщения.|  
|FINE|Обеспечивает информацию о трассировке, включая создание и удаление базового объекта. Помимо этого, все исключения, возникшие по вине открытых методов.|  
|FINER|Предоставляет подробные данные трассировки, включая все входные и выходные точки открытых методов с типами данных связанных параметров, а также все открытые свойства для открытых классов. Кроме этого, входные и выходные параметры и значения, возвращенные методами, кроме возвращаемых значений типов CLOB, BLOB, NCLOB, Reader, \<stream>.<br /><br /> Следующие категории ведения журнала существовали в драйвере JDBC версии 1.2 и имели уровень ведения журнала FINE. [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md), [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), XA и [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). С версии 2.0 эти категории обновлены до уровня FINER.|  
|FINEST|Обеспечивает наивысший уровень детализации данных трассировки. Это самый низкий уровень ведения журнала.<br /><br /> Следующие категории ведения журнала существовали в драйвере JDBC версии 1.2 и имели уровень ведения журнала FINEST. TDS.DATA и TDS.TOKEN. Начиная с версии 2.0, эти категории сохраняют уровень ведения журнала FINEST.|  
|OFF|Отключает ведение журнала.|  
|ALL|Включает регистрацию в журнале всех сообщений.|  
  
## <a name="logging-categories"></a>Категории ведения журнала  
 При создании объекта Logger следует указать именованную сущность или категорию, из которой необходимо получать сведения журнала. Драйвер JDBC поддерживает следующие открытые категории ведения журнала, определенные в пакете драйвера com.microsoft.sqlserver.jdbc.  
  
|Имя|Описание|  
|----------|-----------------|  
|Соединение|Регистрирует сообщения в классе [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Приложение может задать уровень ведения журнала FINER.|  
|.|Регистрирует сообщения в классе [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Приложение может задать уровень ведения журнала FINER.|  
|DataSource|Регистрирует сообщения в классе [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). Приложение может задать уровень ведения журнала FINE.|  
|ResultSet|Регистрирует сообщения в классе [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). Приложение может задать уровень ведения журнала FINER.|  
|Драйвер|Регистрирует сообщения в классе [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md). Приложение может задать уровень ведения журнала FINER.|  
  
 Начиная с версии 2.0 драйвера Microsoft JDBC, драйвер также обеспечивает пакет com.microsoft.sqlserver.jdbc.internals, который включает поддержку ведения журнала для следующих внутренних категорий ведения журнала.  
  
|Имя|Описание|  
|----------|-----------------|  
|AuthenticationJNI|Записывает в журнал сообщения, связанные с проблемами при встроенной проверке подлинности Windows (когда свойство подключения **authenticationScheme** явно или неявно получает значение **NativeAuthentication**).<br /><br /> Приложение может задать уровень ведения журнала FINEST и FINE.|  
|SQLServerConnection|Регистрирует сообщения в классе [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Приложение может задать уровень ведения журнала FINE и FINER.|  
|SQLServerDataSource|Регистрирует сообщения в классах [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md), [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md) и [SQLServerPooledConnection](../../connect/jdbc/reference/sqlserverpooledconnection-class.md).<br /><br /> Приложение может задать уровень ведения журнала FINER.|  
|InputStream|Регистрирует сообщения относительно следующих типов данных: java.io.InputStream, java.io.Reader и типы данных, которые имеют описатель максимального значения, то есть типы данных varchar, nvarchar и varbinary.<br /><br /> Приложение может задать уровень ведения журнала FINER.|  
|SQLServerException|Регистрирует сообщения в классе [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Приложение может задать уровень ведения журнала FINE.|  
|SQLServerResultSet|Регистрирует сообщения в классе [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md). Приложение может задать уровень ведения журнала FINE, FINER и FINEST.|  
|SQLServerStatement|Регистрирует сообщения в классе [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Приложение может задать уровень ведения журнала FINE, FINER и FINEST.|  
|XA|Регистрирует сообщения для всех транзакций XA в классе [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md). Приложение может задать уровень ведения журнала FINE и FINER.|  
|KerbAuthentication|Записывает сообщения, связанные с проверкой подлинности Kerberos типа 4 (когда свойство подключения **authenticationScheme** установлено в значение **JavaKerberos**). Приложение может задать уровень ведения журнала FINE или FINER.|  
|TDS.DATA|Регистрирует сообщения, содержащие диалог на уровне протокола TDS между драйвером и SQL Server. Подробное содержимое каждого отправленного и полученного пакета TDS вносится в журнал в виде значений ASCII или шестнадцатеричных значений. Учетные данные для входа (имена пользователей и пароли) не вносятся в журнал. Все остальные данные записываются в журнал.<br /><br /> Данная категория создает очень длинные и подробные сообщения, ее можно включить, только если установить уровень ведения журнала на FINEST.|  
|TDS.Channel|Данная категория отслеживает действия канала связи TCP с SQL Server. Вносимые в журнал сообщения включают открытие и закрытие сокета, а также операции считывания и записи. Категория также отслеживает сообщения, связанные с установкой соединения TLS, ранее называемого SSL, с SQL Server.<br /><br /> Эта категория может быть включена, если установить уровень ведения журнала на FINE, FINER или FINEST.|  
|TDS.Writer|Эта категория отслеживает операции записи в канал TDS. Обратите внимание, что отслеживается длина записей, а не их содержимое. Данная категория также отслеживает отправку сигнала на сервер, запрашивающего отмену выполнения инструкции.<br /><br /> Эта категория может быть включена только установкой уровня ведения журнала FINEST.|  
|TDS.Reader|Данная категория отслеживает операции считывания из канала TDS на уровне FINEST. На уровне FINEST отслеживание может быть подробным. На уровнях WARNING и SEVERE данная категория отслеживает получение драйвером недействительного протокола TDS от SQL Server до того, как драйвер закроет соединение.<br /><br /> Эта категория может быть включена, если установить уровень ведения журнала на FINER и FINEST.|  
|TDS.Command|Эта категория отслеживает переходы состояния низкого уровня и другую информацию, связанную с выполнением команд TDS, таких как инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)], выборки курсора ResultSet, фиксации и так далее.<br /><br /> Эта категория может быть включена только установкой уровня ведения журнала FINEST.|  
|TDS.TOKEN|Данная категория вносит в журнал только токены внутри пакетов TDS и является менее подробной, чем категория TDS.DATA. Эта категория может быть включена, только если установить уровень ведения журнала на FINEST.<br /><br /> На уровне FINEST в этой категории отслеживаются токены TDS по мере их обработки в ответе. На уровне SEVERE данная категория отслеживает обнаружение недопустимого токена TDS.|  
|SQLServerDatabaseMetaData|Регистрирует сообщения в классе [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md). Приложение может задать уровень ведения журнала FINE.|  
|SQLServerResultSetMetaData|Регистрирует сообщения в классе [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md). Приложение может задать уровень ведения журнала FINE.|  
|SQLServerParameterMetaData|Регистрирует сообщения в классе [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md). Приложение может задать уровень ведения журнала FINE.|  
|SQLServerBlob|Регистрирует сообщения в классе [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md). Приложение может задать уровень ведения журнала FINE.|  
|SQLServerClob|Регистрирует сообщения в классе [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md). Приложение может задать уровень ведения журнала FINE.|  
|SQLServerSQLXML|Регистрирует сообщения во внутреннем классе SQLServerSQLXML. Приложение может задать уровень ведения журнала FINE.|  
|SQLServerDriver|Регистрирует сообщения в классе [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md). Приложение может задать уровень ведения журнала FINE.|  
|SQLServerNClob|Регистрирует сообщения в классе [SQLServerNClob](../../connect/jdbc/reference/sqlservernclob-class.md). Приложение может задать уровень ведения журнала FINE.|  
  
## <a name="enabling-tracing-programmatically"></a>Включение трассировки программным способом  
 Трассировку можно включить программно, создав объект Logger и указав категорию для регистрации. Например, в следующем коде показано включение ведения журнала для инструкций SQL:  
  
```java
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.FINER);  
```  
  
 Чтобы отключить ведение журнала в коде, используйте следующую инструкцию:  
  
```java
logger.setLevel(Level.OFF);  
```  
  
 Чтобы регистрировать все доступные категории, используйте следующую инструкцию:  
  
```java
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc");  
logger.setLevel(Level.FINE);  
```  
  
 Чтобы отключить регистрацию в журнале определенной категории, используйте следующую инструкцию:  
  
```java
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.OFF);  
```  
  
## <a name="enabling-tracing-by-using-the-loggingproperties-file"></a>Включение трассировки с помощью файла logging.properties  
 Можно также включить трассировку с помощью файла `logging.properties`, который находится в каталоге `lib` установки среды выполнения Java (JRE). Файл может быть использован для установки значений по умолчанию для журналов и обработчиков, которые будут использованы, если трассировка включена.  
  
 Далее приводится пример настроек, которые можно задать в файлах `logging.properties`:  
  
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
>  Свойства можно задать в файле`logging.properties` с помощью объекта LogManager, который является частью java.util.logging.  
  
## <a name="see-also"></a>См. также раздел  
 [Диагностика проблем с JDBC Driver](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
