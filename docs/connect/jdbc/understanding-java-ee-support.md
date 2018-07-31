---
title: Основные сведения о поддержке Java EE | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a9448b80-b7a3-49cf-8bb4-322c73676005
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5d5cc306a407e818a79d67cfc4c4340e1a9c2b22
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278865"
---
# <a name="understanding-java-ee-support"></a>Основные сведения о поддержке Java EE
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В следующих разделах описывается, как драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализует поддержку платформы Java Enterprise Edition (Java EE) и дополнительные функции API-интерфейсов JDBC 3.0. Образцы исходного кода, собранные в данном разделе справки, позволяют быстро освоить эти функции.  
  
 Сначала убедитесь, что среда JAVA (JDK, JRE) включает пакет javax.sql. Это обязательный пакет для любого приложения JDBC, которое использует дополнительный API-интерфейс. JDK 1.5 и более поздние версии уже содержат этот пакет, поэтому нет необходимости устанавливать его отдельно.  
  
## <a name="driver-name"></a>Имя драйвера  
 Имя класса драйвера ― com.microsoft.sqlserver.jdbc.SQLServerDriver **. Драйвер содержится в файле sqljdbc.jar, sqljdb4.jar, sqljdbc41.jar или sqljdbc42.jar. Для JDBC Driver 6.2 драйвер содержится в mssql-jdbc-6.2.1.jre7.jar или mssql-jdbc-6.2.1.jre8.jar. Для JDBC Driver 6.4 драйвер содержится в mssql-jdbc-6.4.0.jre7.jar mssql-jdbc-6.4.0.jre8.jar и mssql-jdbc-6.4.0.jre9.jar.
  
 Имя класса используется каждый раз при загрузке драйвера с классом JDBC . Оно также используется всегда, когда нужно указать имя класса драйвера в любой конфигурации драйвера. Например, для настройки источника данных на сервере приложений Java EE требуется имя класса драйвера.  
  
## <a name="data-sources"></a>обозревателе решений  
 Драйвер JDBC обеспечивает поддержку для источников данных Java EE/JDBC 3.0. Класс драйвера JDBC SQLServerXADataSource[ реализуется при помощи com.microsoft.sqlserver.jdbc.SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md).  
  
### <a name="datasource-names"></a>Имена источников данных  
 Подключения к базам данных можно создать, используя источники данных. Источники данных, доступные с драйвером JDBC, описываются в следующей таблице.  
  
|Тип источника данных|Добавить имя и описание|  
|---------------|--------------------------|  
|DataSource|com.microsoft.sqlserver.jdbc.SQLServerDataSource <br/> <br/> Источник данных без организации пулов.|  
|ConnectionPoolDataSource|com.microsoft.sqlserver.jdbc.SQLServerConnectionPoolDataSource <br/> <br/> Источник данных для настройки пулов соединений сервера приложений JAVA EE. Обычно используется, когда приложение работает на сервере приложений JAVA EE.|  
|XADataSource|com.microsoft.sqlserver.jdbc.SQLServerXADataSource <br/> <br/> Источник данных для настройки источников данных JAVA EE XA. Обычно используется, когда приложение работает на сервере приложений JAVA EE и диспетчере транзакций XA.|  
  
### <a name="data-source-properties"></a>Свойства источника данных  
 Все источники данных поддерживают возможность задания и получения любого свойства, связанного с базовым набором свойств драйвера.  
  
 Примеры:  
  
 `setServerName("localhost");`  
  
 `setDatabaseName("AdventureWorks");`  
  
 Далее показано, как приложение подключается, используя источник данных.  
  
```java
initialize JNDI ..  
Context ctx = new InitialContext(System.getProperties());  
...  
DataSource ds = (DataSource) ctx.lookup("MyDataSource");  
Connection c = ds.getConnection("user", "pwd");  
```  
  
 Дополнительные сведения о свойствах источника данных, см. в разделе [задание свойств источника данных](../../connect/jdbc/setting-the-data-source-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
