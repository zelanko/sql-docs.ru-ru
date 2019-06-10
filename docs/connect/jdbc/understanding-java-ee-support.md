---
title: Основные сведения о поддержке Java EE | Документация Майкрософт
ms.custom: ''
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a9448b80-b7a3-49cf-8bb4-322c73676005
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bd082fbbc6aadbbef2ec8778b61a68c659949e74
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66788472"
---
# <a name="understanding-java-ee-support"></a>Основные сведения о поддержке Java EE

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В следующих разделах описано, как драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализует поддержку платформы Java, Enterprise Edition (Java EE) и дополнительные функции API-интерфейсов JDBC 3.0. Образцы исходного кода, собранные в данном разделе справки, позволяют быстро освоить эти функции.  
  
Сначала убедитесь, что среда JAVA (JDK, JRE) включает пакет javax.sql. Это обязательный пакет для любого приложения JDBC, которое использует дополнительный API-интерфейс. JDK 1.5 и более поздние версии уже содержат этот пакет, поэтому устанавливать его отдельно не требуется.  
  
## <a name="driver-name"></a>Имя драйвера

Имя класса драйвера ― **com.microsoft.sqlserver.jdbc.SQLServerDriver**. Для драйверов JDBC 4.1, 4.2 и 6.0 драйвер содержится в файле **sqljdbc.jar**, **sqljdbc4.jar**, **sqljdbc41.jar** или **sqljdbc42.jar**.

Для драйвера JDBC 6.2 драйвер содержится в файле **mssql-jdbc-6.2.2.jre7.jar** или **mssql-jdbc-6.2.2.jre8.jar**.

Для драйвера JDBC 6.4 драйвер содержится в файле **mssql-jdbc-6.4.0.jre7.jar**, **mssql-jdbc-6.4.0.jre8.jar** или **mssql-jdbc-6.4.0.jre9.jar**.

Для драйвера JDBC 7.0 драйвер содержится в файле **mssql-jdbc-7.0.0.jre8.jar** или **mssql-jdbc-7.0.0.jre10.jar**.

Для драйвера JDBC 7.2 драйвер содержится в файле **mssql-jdbc-7.2.2.jre8.jar** или **mssql-jdbc-7.2.2.jre11.jar**.
  
Имя класса используется каждый раз при загрузке драйвера с классом JDBC DriverManager. Оно также используется всегда, когда нужно указать имя класса драйвера в любой конфигурации драйвера. Например, имя класса драйвера может потребоваться для настройки источника данных на сервере приложений Java EE.  
  
## <a name="data-sources"></a>обозревателе решений

Драйвер JDBC обеспечивает поддержку для источников данных Java EE/JDBC 3.0. Класс [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) драйвера JDBC реализуется `com.microsoft.sqlserver.jdbc.SQLServerXADataSource`.  
  
### <a name="datasource-names"></a>Имена источников данных

Подключения к базам данных можно создать, используя источники данных. Источники данных, доступные с драйвером JDBC, описываются в следующей таблице.  
  
|Тип источника данных|Имя класса и описание|  
|---------------|--------------------------|  
|DataSource|`com.microsoft.sqlserver.jdbc.SQLServerDataSource` <br/> <br/> Источник данных без организации пулов.|  
|ConnectionPoolDataSource|`com.microsoft.sqlserver.jdbc.SQLServerConnectionPoolDataSource` <br/> <br/> Источник данных для настройки пулов соединений сервера приложений JAVA EE. Обычно используется, когда приложение работает на сервере приложений JAVA EE.|  
|XADataSource|`com.microsoft.sqlserver.jdbc.SQLServerXADataSource` <br/> <br/> Источник данных для настройки источников данных JAVA EE XA. Обычно используется, когда приложение работает на сервере приложений JAVA EE и диспетчере транзакций XA.|  
  
### <a name="data-source-properties"></a>Свойства источника данных

Все источники данных поддерживают возможность задания и получения любого свойства, связанного с базовым набором свойств драйвера.  
  
Примеры:  
  
`setServerName("localhost");`  
`setDatabaseName("AdventureWorks");`  
  
Далее показано, как приложение подключается, используя источник данных.  

```java
//initialize JNDI ..  
Context ctx = new InitialContext(System.getProperties());
...
DataSource ds = (DataSource) ctx.lookup("MyDataSource");
Connection c = ds.getConnection("user", "pwd");  
```

Дополнительные сведения см. в статье [Задание свойств источника данных](../../connect/jdbc/setting-the-data-source-properties.md).  
  
## <a name="see-also"></a>См. также:

[Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
