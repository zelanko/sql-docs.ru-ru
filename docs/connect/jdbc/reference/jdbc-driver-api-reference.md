---
title: Справочник по API для драйвера JDBC | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e4e1ae9d-18a6-41db-8bd2-9cf0eee4cccb
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2b9dc05cfa6e96fc3dd987095917a932883df4e2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32843189"
---
# <a name="jdbc-driver-api-reference"></a>Справочник интерфейса драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] Предоставляет API, который можно использовать в Java программный код для подключения и взаимодействия с [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных.  
  
> [!NOTE]  
>  Основные сведения об использовании драйвера JDBC см. в разделе [Общие сведения о драйвере JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md).  
  
> [!IMPORTANT]  
>  JDBC 4.1 и 4.2 поддерживают соответствия, используйте Microsoft JDBC Driver 4.2 (или более поздней версии) для SQL Server. Предыдущие выпуски драйверов Microsoft JDBC Driver 4.1 и 4.0 не поддерживают новые методы, появившиеся в JDBC 4.1 или 4.2.  
>   
>  Сведения об интерфейсе API для соответствия JDBC 4.1 не представлены в этом разделе. В разделе [JDBC 4.1 соответствия для драйвера JDBC](../../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md).  
>   
>  Сведения об интерфейсе API для соответствия JDBC 4.2 не представлены в этом разделе. В разделе [JDBC 4.2 соответствия для драйвера JDBC](../../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).  
>   
>  В этом разделе не представлены сведения об API для массового копирования, доступной начиная с Microsoft JDBC Driver 4.2 для SQL Server. В разделе [с помощью массового копирования с драйвером JDBC](../../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).  
>   
>  В этом разделе не представлены сведения об API для Always Encrypted, доступной начиная с Microsoft JDBC Driver 6.0 для SQL Server. В разделе [постоянного шифрования Справочник по API для драйвера JDBC](../../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  
>   
>  В этом разделе не представлены сведения об API для параметров Using Table-Valued, начиная с Microsoft JDBC Driver 6.0 для SQL Server. В разделе [использование возвращающих табличные значения параметров](../../../connect/jdbc/using-table-valued-parameters.md)  
>   
>  6.4 драйвера Microsoft JDBC поддерживает компиляцию с JDK 7.0, 8.0 и 9.0.  
>   
>  Microsoft JDBC Driver 6.2 поддерживает компиляцию с JDK 7.0 и 8.0.  
>   
>  Драйверы Microsoft JDBC Driver 6.0 и 4.2 поддерживают компиляцию с JDK 5.0, 6.0, 7.0 и 8.0.  
>   
>  Драйвер Microsoft JDBC Driver 4.1 поддерживает компиляцию с помощью с JDK 5.0, 6.0 и 7.0.  

## <a name="interfaces"></a>Интерфейсы  
  
|Имя интерфейса|Описание|  
|--------------------|-----------------|  
|[Интерфейс ISQLServerCallableStatement](../../../connect/jdbc/reference/isqlservercallablestatement-interface.md)|Позволяет указать имя вызываемой хранимой процедуры с входными и выходными параметрами.|  
|[Интерфейс ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md)|Представляет соединение JDBC с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных.|  
|[Класс SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)|Представляет список свойств, относящихся к подключению к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных с помощью [ISQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)|Представляет базовую реализацию функциональности подготовленной инструкции JDBC.|  
|[ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)|Представляет результирующий набор JDBC.|  
|[ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)|Представляет базовую реализацию функциональности инструкции JDBC.|  
  
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
|[SQLServerDataSource](../../../connect/jdbc/reference/isqlserverdatasource-interface.md)|Представляет список свойств, относящихся к подключению к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных с помощью [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) объекта.|  
|[SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)|Представляет фабрику объектов для материализации источников данных из интерфейса JNDI.|  
|[SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)|Представляет драйвер JDBC. Этот класс содержит методы для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных, а также для получения сведений о драйвере JDBC.|  
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
|[SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)|Представляет фабрику для [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) объектов, которые используется для внутренних целей.|  
|[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)|Представляет XAResource для XA управления распределенными транзакциями.|  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о драйвере JDBC](../../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
