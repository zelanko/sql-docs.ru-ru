---
title: Справочник по API для драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e4e1ae9d-18a6-41db-8bd2-9cf0eee4cccb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f311458a8fb6b58f22a1ca4c23fa8d1f36dddc51
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773798"
---
# <a name="jdbc-driver-api-reference"></a>Справочник интерфейса драйвера JDBC

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] предоставляет API-интерфейс, который можно использовать в программном коде Java для подключения к базе данных [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и взаимодействия с ней.



### <a name="javadocio-website-is-primary"></a>Является первичной репликой JavaDoc.io веб-сайта

Microsoft JDBC справочная документация по API размещается на просмотр JavaDoc.io веб-сайта. JavaDoc.io теперь является нашей основной веб-сайт, справочную документацию по JDBC. Наши JDBC справочную документацию по JavaDoc.io доступна по следующей ссылке direct:

- [https://javadoc.io/doc/com.microsoft.sqlserver/mssql-jdbc/](https://javadoc.io/doc/com.microsoft.sqlserver/mssql-jdbc/)

JavaDoc.io имеет наших JDBC справочную документацию, начиная с версии 6.0.

#### <a name="only-legacy-jdbc-documentation-is-here-on-docs"></a>Только для прежних версий JDBC документацию можно здесь на документы

В JDBC API справочной документации здесь статьях на **https://docs.microsoft.com/sql/connect/jdbc/reference/** больше не обновляются при обновлении классах JDBC для новых выпусков. Тем не менее здесь статьи содержат все ссылки для версий JDBC 4.1 и 4.2.

Документация по JDBC версии 6.0 и более поздних версиях можно здесь. Но для любой версии 6.0 или более поздней версии, используйте JavaDoc.io веб-сайта.



### <a name="important-notes"></a>Важные примечания

> [!NOTE]  
>  Основные сведения об использовании драйвера JDBC см. в разделе [Общие сведения о драйвере JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
>  Для поддержки соответствия JDBC 4.1 и 4.2 используйте Microsoft JDBC Driver 4.2 (или более поздней версии) для SQL Server. Предыдущие выпуски драйверов Microsoft JDBC Driver 4.1 и 4.0 не поддерживают новые методы, появившиеся в JDBC 4.1 или 4.2.  
>   
>  Сведения об интерфейсе API для соответствия JDBC 4.1 не представлены в этом разделе. См. [Соответствие требованиям JDBC 4.1 для JDBC Driver](../../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md).  
>   
>  Сведения об интерфейсе API для соответствия JDBC 4.2 не представлены в этом разделе. См. [Соответствие требованиям JDBC 4.2 для JDBC Driver](../../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).  
>   
>  Сведения об API для функции массового копирования, доступной начиная с версии Microsoft JDBC Driver 4.2 для SQL Server, не представлены в этом разделе. См. [Использование массового копирования с драйвером JDBC](../../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).  
>   
>  Сведения об API для функции Always Encrypted, доступной начиная с версии Microsoft JDBC Driver 6.0 для SQL Server, не представлены в этом разделе. См. [Справочник по API Always Encrypted для драйвера JDBC](../../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  
>   
>  Сведения об API для параметров Using Table-Valued, доступный начиная с Microsoft JDBC Driver 6.0 для SQL Server, не представлены в этом разделе. См. [Использование параметров, возвращающих табличные значения](../../../connect/jdbc/using-table-valued-parameters.md)  
>   
>  Драйвер Microsoft JDBC 6.4 поддерживает компиляцию с JDK 7.0, 8.0 и 9.0.  
>   
>  Драйвер Microsoft JDBC 6.2 поддерживает компиляцию с JDK 7.0 и 8.0.  
>   
>  Драйверы Microsoft JDBC 6.0 и 4.2 поддерживают компиляцию с JDK 5.0, 6.0, 7.0 и 8.0.  
>   
>  Драйвер Microsoft JDBC Driver 4.1 поддерживает компиляцию с помощью с JDK 5.0, 6.0 и 7.0.  



## <a name="interfaces"></a>Интерфейсы  
  
|Имя интерфейса|Описание|  
|--------------------|-----------------|  
|[Интерфейс ISQLServerCallableStatement](../../../connect/jdbc/reference/isqlservercallablestatement-interface.md)|Позволяет указать имя вызываемой хранимой процедуры с входными и выходными параметрами.|  
|[Интерфейс ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md)|Представляет соединение JDBC с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|[Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)|Представляет список свойств, относящихся к подключению к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием объекта [ISQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)|Представляет базовую реализацию функциональности подготовленной инструкции JDBC.|  
|[ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)|Представляет результирующий набор JDBC.|  
|[ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)|Представляет базовую реализацию функциональности инструкции JDBC.|
| &nbsp; | &nbsp; |


  
## <a name="classes"></a>Классы  
  
|Имя класса|Описание|  
|----------------|-----------------|  
|[DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)|Представляет объект типа microsoft.sql.DateTimeOffset.|  
|[SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)|Представляет большой двоичный объект (BLOB).|  
|[SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)|Реализует ISQLServerCallableStatement.|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)|Представляет символьный большой двоичный объект (CLOB).|  
|[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)|Реализует ISQLServerConnectopn.|  
|[SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)|Представляет физические подключение к базе данных для диспетчеров пулов соединений.|  
|[SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)|Представляет метаданные для базы данных.|  
|[SQLServerDataSource](../../../connect/jdbc/reference/isqlserverdatasource-interface.md)|Представляет список свойств, относящихся к подключению к базе данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с использованием объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).|  
|[SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)|Представляет фабрику объектов для материализации источников данных из интерфейса JNDI.|  
|[SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)|Представляет драйвер JDBC. Этот класс включает методы для соединения с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и для получения данных о драйвере JDBC.|  
|[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)|Представляет неуспешное или неполное выполнение инструкции SQL.|  
|[Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)|Представляет символьный большой двоичный объект, используя национальный набор символов.|  
|[SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)|Представляет метаданные для параметров подготовленных инструкций.|  
|[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)|Представляет физическое подключение к базе данных в пуле соединений.|  
|[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)|Реализует ISQLServerPreparedStatement.|  
|[SQLServerResource](../../../connect/jdbc/reference/sqlserverresource-class.md)|Представляет локализованный ресурс строки ошибки. Этот класс предназначен только для внутреннего использования.|  
|[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)|Реализует ISQLServerResultSet.|  
|[SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)|Представляет метаданные столбцов, которые содержатся в результирующем наборе.|  
|[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)|Представляет контрольную точку, для которой может быть выполнен откат транзакции.|  
|[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)|Реализует ISQLServerStatement.|  
|[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)|Представляет подключения JDBC, которые могут участвовать в распределенных транзакциях (XA).|  
|[SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)|Представляет фабрику для объектов [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md), предназначенных для внутреннего использования.|  
|[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)|Представляет интерфейс XAResource для управления распределенными транзакциями XA.|
| &nbsp; | &nbsp; |



## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md)

