---
title: "Основные сведения о поддержке Java EE | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9448b80-b7a3-49cf-8bb4-322c73676005
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b878069cb0ddf04d4c8c743795f876b00fef23dc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="understanding-java-ee-support"></a>Основные сведения о поддержке Java EE
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  В следующих разделах описывается как [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] обеспечивает поддержку Java Platform, Enterprise Edition (Java EE) и дополнительные функции API JDBC 3.0. Образцы исходного кода, собранные в данном разделе справки, позволяют быстро освоить эти функции.  
  
 Сначала убедитесь, что среда JAVA (JDK, JRE) включает пакет javax.sql. Это обязательный пакет для любого приложения JDBC, которое использует дополнительный API-интерфейс. JDK 1.5 и более поздние версии уже содержат этот пакет, поэтому нет необходимости устанавливать его отдельно.  
  
## <a name="driver-name"></a>Имя драйвера  
 Имя класса драйвера ― **com.microsoft.sqlserver.jdbc.SQLServerDriver**. Для драйверов JDBC 4.0, 4.1, 6.0 и 4.2 драйвер содержится в файле sqljdbc.jar, sqljdbc4.jar, sqljdbc41.jar или sqljdbc42.jar. Для 6.2 драйвера JDBC драйвер содержится в mssql jdbc-6.2.1.jre7.jar или mssql jdbc-6.2.1.jre8.jar.
  
 Имя класса используется каждый раз при загрузке драйвера с помощью класса JDBC DriverManager. Оно также используется всегда, когда нужно указать имя класса драйвера в любой конфигурации драйвера. Например, для настройки источника данных на сервере приложений Java EE требуется имя класса драйвера.  
  
## <a name="data-sources"></a>Источники данных  
 Драйвер JDBC обеспечивает поддержку для источников данных Java EE/JDBC 3.0. Драйвер JDBC [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) реализуется класс **com.microsoft.sqlserver.jdbc.SQLServerXADataSource**.  
  
### <a name="datasource-names"></a>Имена источников данных  
 Подключения к базам данных можно создать, используя источники данных. Источники данных, доступные с драйвером JDBC, описываются в следующей таблице.  
  
|Тип источника данных|Имя класса и описание|  
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
  
```  
initialize JNDI ..  
Context ctx = new InitialContext(System.getProperties());  
...  
DataSource ds = (DataSource) ctx.lookup("MyDataSource");  
Connection c = ds.getConnection("user", "pwd");  
```  
  
 Дополнительные сведения о свойствах источника данных см. в разделе [настройки свойств источника данных](../../connect/jdbc/setting-the-data-source-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

