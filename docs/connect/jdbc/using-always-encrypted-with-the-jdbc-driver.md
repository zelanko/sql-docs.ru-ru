---
title: "Использование постоянного шифрования с драйвером JDBC | Документы Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: 64
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: 4bc5be85fddcc86de0a3fe845620f5152b568015
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Использование функции Always Encrypted с драйвером JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Этой статье содержатся сведения о том, как разрабатывать приложения Java, с использованием [постоянного шифрования](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7) и Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.

Постоянное шифрование позволяет клиентам Шифровать конфиденциальные данные, не раскрывая данные или ключи шифрования для SQL Server или база данных SQL Azure. Постоянное шифрование включено драйвера, таких как Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server, достигается с помощью прозрачного шифрования и расшифровки конфиденциальных данных в клиентском приложении. Драйвер автоматически определяет, какой запрос параметров соответствуют важным столбцам базы данных (защищенный с помощью постоянного шифрования) и шифрует значения этих параметров перед их передачей значения в SQL Server или база данных SQL Azure. Аналогичным образом драйвер прозрачно расшифровывает данные, полученные из зашифрованных столбцов базы в результатах запроса. Дополнительные сведения см. на сайте [Always Encrypted (ядро СУБД)](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7) и [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  


## <a name="prerequisites"></a>Предварительные требования

- Настройте функцию постоянного шифрования в базе данных. В процесс настройки входят действия по подготовке ключей постоянного шифрования и настройке шифрования для выбранных столбцов базы данных. Если в базе данных постоянное шифрование еще не настроено, следуйте инструкциям в разделе [Приступая к работе с постоянным шифрованием](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_5).
- Убедитесь, что драйвер Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server должен быть установлен на компьютере разработки. 
-   Скачайте и установите файлы политики юрисдикции неограниченной стойкости Java Cryptography Extension (JCE).  Обязательно прочитайте содержащийся в ZIP-архиве файл сведений для получения инструкции по установке и сопутствующие сведений по возможным проблемам экспорта и импорта.  
  
    -   При использовании sqljdbc41.jar, файлы политики можно скачать из [загрузки файлов Java Cryptography Extension (JCE) неограниченное стойкость юрисдикции политики 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)  
  
    -   При использовании sqljdbc42.jar, файлы политики можно скачать из [загрузки файлов Java Cryptography Extension (JCE) неограниченное стойкость юрисдикции политики 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)   
    
## <a name="enabling-always-encrypted-for-application-queries"></a>Включение Always Encrypted для запросов приложений  
Является самым простым способом включения шифрования параметров и расшифровки результатов запроса к зашифрованным столбцам, задав значение **columnEncryptionSetting** ключевое слово строки подключения для ** Включить**.

Ниже приведен пример строки подключения, включающий постоянное шифрование в драйвере JDBC:
  
```  
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;"; 
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);
     
```  
  
А ниже приведен эквивалент примера с помощью объекта SQLServerDataSource.  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setServerName("localhost");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");  
SQLServerConnection con = (SQLServerConnection) ds.getConnection(); 
```    

Постоянное шифрование также можно включить для отдельных запросов. В разделе **контроля производительности влияние из постоянного шифрования** разделе ниже. Обратите внимание, что включение постоянного шифрования недостаточно для успешного шифрования или расшифровки. Необходимо также проверить выполнение следующих условий:
- Приложение имеет разрешения *VIEW ANY COLUMN MASTER KEY DEFINITION* и *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* для базы данных, необходимые для доступа к метаданным о ключах постоянного шифрования в базе данных. Для дополнительных сведений см. страницу [о разрешениях в статье "Always Encrypted (ядро СУБД)"](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7).
- Приложение может получить доступ к главному ключу столбца, который защищает ключи шифрования столбцов, шифрующие запрашиваемые столбцы базы данных. Обратите внимание, что для использования поставщика хранилища ключей Java, необходимо предоставить дополнительные учетные данные в строке подключения. В разделе **поставщика хранилища ключей с помощью Java** более подробные сведения.

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Настройка способа отправки значений java.sql.Time сервера

**SendTimeAsDatetime** свойство соединения позволяет настроить порядок отправки значения java.sql.Time на сервер. Если sendTimeAsDatetime = false, значение передается как тип SQL Server времени время и когда sendTimeAsDatetime = true, при отправке значения типа datetime. Обратите внимание, что при шифровании столбец времени sendTimeAsDatetime свойство должно быть false как зашифрованных столбцов не поддерживается преобразование из времени в datetime. Также Обратите внимание, что это свойство по умолчанию true, поэтому при использовании зашифрованных столбцов, нужно присвоить ему значение false. В противном случае драйвер вызовет как исключение. Класс SQLServerConnection имеет два метода, начиная с версии 6.0 драйвера для программной настройки значение этого свойства.
 
* открытые void setSendTimeAsDatetime (логическое sendTimeAsDateTimeValue)
* public boolean getSendTimeAsDatetime()

Дополнительные сведения о данном свойстве [как настройка java.sql.Time отправляются на сервер](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx). 

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>Настройка способа отправки строковые значения сервера

**SendStringParametersAsUnicode** свойство соединения используется для настройки способа отправки строковых значений SQL Server. Если задано значение «true», строковые параметры отправляются на сервер в Юникоде. Если задано значение «false», строковые параметры отправляются в формате Юникод, например ASCII/MBCS, а не в Юникоде. По умолчанию для этого свойства равно «true». Если постоянное шифрование включено, а столбец char/varchar/varchar(max) зашифрован, значение **sendStringParametersAsUnicode** должно быть присвоено значение true (или оставить значение по умолчанию). Microsoft JDBC Driver for SQL Server возникает исключение при вставке данных char/varchar/varchar(max) зашифрованный столбец, если это свойство имеет значение false. Дополнительные сведения о данном свойстве [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md). 
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Получение и изменение данных в зашифрованных столбцах

После включения постоянного шифрования для запросов приложений можно использовать стандартные API-интерфейсы JDBC извлекать или изменять данные в столбцах зашифрованной базы данных. При условии, что приложение имеет базы данных, необходимых разрешений можно доступа главного ключа столбца, Microsoft JDBC Driver for SQL Server будет шифровать все параметры запроса, предназначенные для зашифрованных столбцов и расшифровывать данные полученные из зашифрованных столбцов Получение возвращаемых значений открытого текста типов JDBC, соответствующий SQL Server типы данных и задать для столбцов в схеме базы данных.
Если постоянное шифрование не включено, выполнение запросов с параметрами, предназначенными для зашифрованных столбцов, завершится ошибкой. Запросы по-прежнему могут получать данные из зашифрованных столбцов, пока для них не будут указаны параметры, предназначенные для зашифрованных столбцов. Однако Microsoft JDBC Driver for SQL Server не будет пытаться расшифровать все значения, полученные из зашифрованных столбцов, и приложение будет получать двоичные зашифрованные данные (в виде массивов байтов).

В приведенной ниже таблице описывается поведение запросов в зависимости от того, включено постоянное шифрование или нет.

|Характеристика запроса | Постоянное шифрование включено, и приложение может получать доступ к ключам и метаданным ключей|Постоянное шифрование включено, и приложение не может получать доступ к ключам и метаданным ключей | Постоянное шифрование отключено|
|:---|:---|:---|:---|
| Запросы с параметрами, предназначенными для зашифрованных столбцов. | Значения параметров прозрачно шифруются. | Ошибка | Ошибка|
| Запросы, получающие данные из зашифрованных столбцов, без параметров, предназначенных для зашифрованных столбцов.| Результаты из зашифрованных столбцов прозрачно расшифровываются. Приложение получает значения типов данных JDBC, соответствующие типы SQL Server, настроенным для зашифрованных столбцов в открытом тексте. | Ошибка | Результаты из зашифрованных столбцов не расшифровываются. Приложение получает зашифрованные значения в виде массивов байтов (byte[]).
      
 
### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Вставки и извлечения примеры зашифрованные данные 
В следующих примерах показано получение и изменение данных в зашифрованных столбцах. В примерах предполагается использование целевой таблицы с приведенной ниже схемой. Обратите внимание, что столбцы SSN и BirthDate зашифрованы.

```
CREATE TABLE [dbo].[Patients]([PatientId] [int] IDENTITY(1,1), 
 [SSN] [char](11) COLLATE Latin1_General_BIN2 
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL, 
 [BirthDate] [date] 
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = MyCEK) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```
 
### <a name="inserting-data-example"></a>Пример вставки данных

В этом примере показана вставка строки в таблицу Patients. Следует отметить следующее.
- В образце кода нет ничего, связанного с шифрованием. Microsoft JDBC Driver for SQL Server автоматически обнаруживает и шифрует параметры, предназначенные для зашифрованных столбцов. В этом случае шифрование является прозрачным для приложения. 
- Значениях, вставляемых в столбцы базы данных, включая зашифрованные столбцы передаются как параметры, с помощью SQLServerPreparedStatement. При использовании параметров является необязательным при отправке значений в незашифрованные столбцы (хотя, настоятельно рекомендуется, так как он помогает предотвратить внедрение кода SQL), он необходим для значений, предназначенных для зашифрованных столбцов. Если значения, вставленные в зашифрованных столбцах были переданы в качестве литералов, внедренных в инструкции запроса, выполнение запроса завершится ошибкой, так как Microsoft JDBC Driver for SQL Server не сможет определить значения в зашифрованных столбцах, поэтому оно не будет разрешено зашифровать значения. В результате сервер отклонит их как несовместимые с зашифрованными столбцами.
- Все значения, выводимые программой будет в виде обычного текста, как Microsoft JDBC Driver for SQL Server прозрачно расшифровывает данные, полученные из зашифрованных столбцов.
- При выполнении поиска с помощью там, ГДЕ предложение, значение, используемое в предложении WHERE необходимо передать как параметр, Microsoft JDBC Driver for SQL Server прозрачно для его шифрования перед его отправкой в базу данных. В приведенном ниже примере обратите внимание, что SSN передается в качестве параметра, но LastName передается как литерал, как LastName не шифруются.
- Метод задания свойства, используемое для параметра, предназначенных для столбца SSN — setString(), которая сопоставляется тип данных SQL Server char/varchar. Если для этого параметра используется метод задания был setNString(), который сопоставляет nchar/nvarchar, запрос завершится ошибкой, как постоянное шифрование не поддерживает преобразования из зашифрованных значений nchar и nvarchar в зашифрованные char/varchar значения.  

```
String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
try  
{           
     Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
     try (Connection sourceConnection = DriverManager.getConnection(connectionString))  
     {                  
        String insertRecord="INSERT INTO [dbo].[Patients] VALUES (?, ?, ?, ?)";        
        try (PreparedStatement insertStatement = sourceConnection.prepareStatement(insertRecord))  
        {
            insertStatement.setString(1, "795-73-9838");  
            insertStatement.setString(2, "Catherine");   
            insertStatement.setString(3, "Abel");                   
            insertStatement.setDate(4, Date.valueOf("1996-09-10"));  
            insertStatement.executeUpdate();  
            System.out.println("1 record inserted.\n");  
        }         
     }  
}  
catch (Exception e)  
{  
    e.printStackTrace();  
}
```

### <a name="retrieving-plaintext-data-example"></a>Пример получения данных в виде открытого текста

В следующем примере показана фильтрация данных на основе зашифрованных значений и получение данных в виде открытого текста из зашифрованных столбцов. Следует отметить следующее.
- Значение, используемое в предложении WHERE для фильтрации по столбцу SSN должен будет передан как параметр, чтобы Microsoft JDBC Driver for SQL Server мог его прозрачно зашифровать перед отправкой в базу данных.
- Все значения, выводимые программой будет в виде обычного текста, как Microsoft JDBC Driver for SQL Server прозрачно расшифровывает данные, полученные из столбцов SSN и BirthDate.

> [!NOTE]  
>  Запросы могут выполнять сравнение на равенство для столбцов, если они шифруются с помощью детерминированного шифрования. Дополнительные сведения см. в разделе **Выбор детерминированного или случайного шифрования** раздел [Always Encrypted (ядро СУБД)](/sql-docs/docs/relational-databases/security/encryption/always-encrypted-database-engine) раздела.  

```
String connectionString =  "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;" ;
String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN = ?;";  

try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))  
{  
    selectStatement.setString(1, "795-73-9838");  
    ResultSet rs = selectStatement.executeQuery();   
    while(rs.next()) 
    {  
    System.out.println("SSN: " +rs.getString("SSN") + 
    ", FirstName: " + rs.getString("FirstName") + 
    ", LastName:"+ rs.getString("LastName")+
     ", Date of Birth: " + rs.getString("BirthDate"));  
          }  
}
catch (Exception e)  
{  
    e.printStackTrace();  
}
```
  
### <a name="retrieving-encrypted-data-example"></a>Пример получения зашифрованных данных

Если постоянное шифрование не включено, запрос может получать данные из зашифрованных столбцов, пока для него не будут указаны параметры, предназначенные для зашифрованных столбцов.

В следующих примерах показано извлечение двоичных зашифрованных данных из зашифрованных столбцов. Следует отметить следующее.

- Так как постоянное шифрование не включено в строке подключения, запрос будет возвращать зашифрованные значения SSN и BirthD в виде байтовых массивов (программа преобразует значения в строки).
- Запрос, получающий данные из зашифрованных столбцов с отключенным постоянным шифрованием, может иметь параметры при условии, что ни один из параметров не предназначен для зашифрованного столбца. Приведенный выше запрос выполняет фильтрацию по LastName, который не зашифрован в базе данных. Запрос, отфильтрованный по SSN или BirthDate, завершится ошибкой.

```
String connectionString  = "jdbc:sqlserver://localhost:1433;" + "databaseName=Clinic;user=sa;password=******";

String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;"; 
 
try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))  
{  
    selectStatement.setString(1, "Abel");  
    ResultSet rs = selectStatement.executeQuery();   
    while(rs.next())
    {  
        System.out.println("SSN: " + rs.getString("SSN") +
         ", FirstName: " + rs.getString("FirstName") + 
        ", LastName:"+ rs.getString("LastName")+ 
        ", Date of Birth: " + rs.getString("BirthDate"));  
    } 
}  
catch (Exception e)  
{  
    e.printStackTrace();  
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Как избежать распространенных проблем при запросе зашифрованных столбцов

В этом разделе описываются общие категории ошибок, при запросе зашифрованных столбцов из приложений Java и приводятся рекомендации о том, как их избежать.

### <a name="unsupported-data-type-conversion-errors"></a>Ошибки преобразования типов данных не поддерживается

Постоянное шифрование поддерживает несколько преобразований для зашифрованных типов данных. В разделе [Always Encrypted (ядро СУБД)](/sql-docs/docs/relational-databases/security/encryption/always-encrypted-database-engine) подробный список поддерживаемых преобразований типов. Далее приведены действия, позволяющие избежать ошибок преобразования типов данных.

- Используйте методы задания правильного при передаче значения для параметров, предназначенных для зашифрованных столбцов, таким образом, тип данных SQL Server параметра либо точно так же, как тип целевого столбца или преобразования параметра типа данных SQL Server Тип столбца поддерживается в целевой объект. Обратите внимание, что были добавлены новые методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement и SQLServerResultSet для передачи параметров, соответствующих определенных типов данных SQL Server. Например если столбец принадлежит незашифрованные можно использовать метод setTimestamp() передать параметр datetime2 или к столбцу типа datetime. Но когда столбец зашифрован необходимо использовать конкретный метод, представляющий тип столбца в базе данных. Например можно используйте setTimestamp() передавать значения в столбце зашифрованные datetime2 и использовать setDateTime() для передачи значений в столбец зашифрованные datetime. В разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) полный список новых интерфейсов API. 
- Точность и масштаб параметров, предназначенных для столбцов типов данных SQL Server decimal и numeric, соответствуют точности и масштабу, настроенным для целевого столбца. Обратите внимание, что были добавлены новые методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement и SQLServerResultSet для приема точность и масштаб, а также значения данных для параметров и столбцами, представляющими десятичных и числовых типов данных. В разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) полный список новых и перегруженные API-интерфейсов.  
- доли секунды точность или шкала параметров, предназначенных для столбцов datetime2, datetimeoffset или времени типов данных SQL Server не больше, чем в целевой столбец, в запросах, которые изменяют значения целевого столбца. Обратите внимание, что были добавлены новые методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement и SQLServerResultSet для приема долей секунды точность или шкала вместе со значениями данных для представления этих типов данных параметров. В разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) полный список новых и перегруженные API-интерфейсов.   

### <a name="errors-due-to-incorrect-connection-properties"></a>Ошибки из-за свойства подключения
В этом разделе описывается настройка параметров подключения соответствующим образом, чтобы использовать постоянное шифрование данных. Так как зашифрованные данные типы поддерживают только преобразования, параметры подключения «sendTimeAsDatetime» и «sendStringParametersAsUnicode» требуется правильная настройка при использовании зашифрованных столбцов. Убедитесь, что: 
- [sendTimeAsDatetime](https://msdn.microsoft.com/library/ff427224(v=sql.110).aspx) подключение установлено значение false при вставке данных в зашифрованные столбцы времени. Дополнительные сведения см. раздел «Настройка как значения java.sql.Time отправляются на сервер».
- [sendStringParametersAsUnicode](../../connect/jdbc/setting-the-connection-properties.md) подключение установлено значение true (или остается по умолчанию) при вставке данных в зашифрованные столбцы char/varchar/varchar(max). Дополнительные сведения см. раздел «Настройка как строковые значения отправляются на сервер».

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Ошибки из-за передачи открытый текст вместо зашифрованные значения

Любое значение, предназначенное для зашифрованного столбца, должно быть зашифровано внутри приложения. Попытка вставки, изменения или фильтрации по значению в виде открытого текста в зашифрованном столбце приведет к возникновению ошибки, подобной следующей:


```
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Чтобы избежать таких ошибок, убедитесь, что:
- Постоянное шифрование включено для запросов приложений, предназначенных для зашифрованных столбцов (для строки подключения или для конкретного запроса).
- с помощью подготовленных инструкций и параметры для отправки данных, предназначенных для зашифрованных столбцов. Ниже примере показан запрос, который неправильно фильтрует по литералу или константе в зашифрованном столбце (SSN), вместо передачи литерала внутри в качестве параметра. Этот запрос завершится ошибкой.

```
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");  
```

## <a name="working-with-column-master-key-stores"></a>Работа с хранилищами главных ключей столбцов
Для шифрования значения параметра или расшифровать данные в результатах запроса, Microsoft JDBC Driver for SQL Server необходимо получить ключ шифрования столбца, настроенный для целевого столбца. Ключи шифрования столбца хранятся в зашифрованном виде в метаданных базы данных. Каждый ключ шифрования столбца имеет соответствующий главный ключ столбца, который использовался для шифрования ключа шифрования столбца. Метаданные базы данных не хранят главные ключи столбцов — они содержат только сведения о хранилище ключей, где находится определенный главный ключ столбца, и расположении ключа в хранилище ключей.

Чтобы получить значение открытого текста ключа шифрования столбца, Microsoft JDBC Driver for SQL Server сначала получает метаданные о ключе шифрования столбца и его соответствующий главный ключ столбца и затем использует сведения в метаданных для ключа обратитесь в службу хранилище, содержащее главный ключ столбца и расшифровки ключа шифрования зашифрованного столбца. Microsoft JDBC Driver for SQL Server взаимодействует с хранилищем ключей с помощью поставщик хранилища главного ключа столбцов — который является экземпляром класса, производного от **SQLServerColumnEncryptionKeyStoreProvider** класса.


### <a name="using-built-in-column-master-key-store-providers"></a>Использование встроенных поставщиков хранилища главных ключей столбцов
  
Microsoft JDBC Driver for SQL Server имеются следующие поставщики хранилища главных ключей встроенный столбец. Обратите внимание, что некоторые из этих поставщиков, предварительно зарегистрированный с конкретными именами поставщиков (используется для поиска поставщика), а некоторые требуют дополнительных учетных данных или явная регистрация.

| Class | Описание | Имя поставщика |Предварительно зарегистрирован?|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Поставщик хранилища ключей для хранилища ключей Azure.| AZURE_KEY_VAULT|Нет|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Поставщик для хранилища сертификатов Windows.|MSSQL_CERTIFICATE_STORE|Да
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Поставщик для хранилище ключей Java|MSSQL_JAVA_KEYSTORE|Да|

Для поставщиков предварительно зарегистрированными хранилища ключей не требуется внести любые изменения кода приложения для использования этих поставщиков, но Обратите внимание на следующее:

- Вы (или ваш администратор баз данных) должны проверить правильность имени поставщика, настроенного в метаданных главного ключа столбца, и убедиться, что путь к ключу главного ключа столбца соответствует формату пути к ключу, который является допустимым для данного поставщика. Для настройки ключей рекомендуется использовать средство, такое как среда SQL Server Management Studio, которое при выполнении инструкции CREATE COLUMN MASTER KEY (Transact-SQL) автоматически создает допустимые имена поставщиков и пути к ключам.
- Необходимо убедиться, что приложение может получать доступ к ключам в хранилище ключей. Для этого может потребоваться предоставить приложению доступ к ключу или хранилищу ключей (в зависимости от хранилища ключей) или выполнить другие действия по настройке конкретного хранилища ключей. Например с помощью SQLServerColumnEncryptionJavaKeyStoreProvider необходимо указать расположение и пароль из хранилища ключей, в свойствах соединения. 

Ниже более подробно описываются все эти поставщики хранилища ключей.
  
### <a name="using-azure-key-vault-provider"></a>Использование поставщика хранилища ключей Azure
Хранилище ключей Azure удобно для хранения главных ключей столбцов для постоянного шифрования, особенно в том случае, если приложения размещены в Azure. Microsoft JDBC Driver for SQL Server включает встроенный поставщик, SQLServerColumnEncryptionAzureKeyVaultProvider, для приложений, имеющих ключи, хранящиеся в хранилище ключей Azure. Этот поставщик называется AZURE_KEY_VAULT. Для использования поставщика хранилища ключей Azure хранилища, разработчик приложения должен создавать хранилища и ключи в Azure и настроить приложение для доступа к ключам. Дополнительные сведения о настройке хранилища ключей и создания главного ключа столбца посвящены [хранилище ключей Azure — шаг за шагом, Дополнительные сведения о настройке хранилища ключей](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) и [создании главных ключей столбцов в хранилище ключей Azure](https://msdn.microsoft.com/library/mt723359.aspx#Anchor_2).  
  
Чтобы использовать хранилище ключей Azure, клиентские приложения должны создать экземпляр SQLServerColumnEncryptionAzureKeyVaultProvider и зарегистрируйте его в драйвере. Проверка подлинности делегаты драйвера JDBC приложения через интерфейс вызывается SQLServerKeyVaultAuthenticationCallback, который имеет метод для получения маркера доступа из хранилища ключей. Для создания экземпляра поставщика хранилища ключей Azure хранилища, разработчику приложения необходимо предоставить реализацию только метод, вызываемый **getAccessToken** получает маркер доступа для ключа, хранящегося в хранилище ключей Azure.  
  
Ниже приведен пример инициализации SQLServerKeyVaultAuthenticationCallback и SQLServerColumnEncryptionAzureKeyVaultProvider:  
  
```  
// String variables clientID and clientSecret hold the client id and client secret values respectively.  
  
ExecutorService service = Executors.newFixedThreadPool(10);  
SQLServerKeyVaultAuthenticationCallback authenticationCallback = new SQLServerKeyVaultAuthenticationCallback() {  
       @Override  
    public String getAccessToken(String authority, String resource, String scope) {  
        AuthenticationResult result = null;  
        try{  
                AuthenticationContext context = new AuthenticationContext(authority, false, service);  
            ClientCredential cred = new ClientCredential(clientID, clientSecret);  
  
            Future<AuthenticationResult> future = context.acquireToken(resource, cred, null);  
            result = future.get();  
        }  
        catch(Exception e){  
            e.printStackTrace();  
        }  
        return result.getAccessToken();  
    }  
};  
  
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(authenticationCallback, service);  
  
```

После приложение создает экземпляр SQLServerColumnEncryptionAzureKeyVaultProvider, приложению необходимо зарегистрировать экземпляр в драйвере Microsoft JDBC для SQL Server с помощью Метод SQLServerConnection.registerColumnEncryptionKeyStoreProviders(). Настоятельно рекомендуется, поиск имени и по умолчанию, AZURE_KEY_VAULT, который можно получить путем вызова SQLServerColumnEncryptionAzureKeyVaultProvider.getName() API зарегистрирован экземпляр. С помощью имени по умолчанию позволит вам средств, таких как SQL Server Management Studio или PowerShell, для подготовки ключей и управление ими постоянное шифрование (средства используйте имя по умолчанию для создания объекта метаданных для главного ключа столбца). Примере ниже показан регистрации поставщика хранилища ключей Azure. Дополнительные сведения о методе SQLServerConnection.registerColumnEncryptionKeyStoreProviders(). в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md). 

```
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();   
keyStoreMap.put(akvProvider.getName(), akvProvider);   
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);   
```
  
> [!IMPORTANT]  
>  Реализация хранилища ключей Azure драйвер JDBC имеет зависимости от этих библиотек (с) (GitHub).  
>   
>  [Azure sdk для java](https://github.com/Azure/azure-sdk-for-java)  
>   
>  [библиотеки Azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)  
  
### <a name="using-windows-certificate-store-provider"></a>С помощью поставщика хранилища сертификатов Windows
SQLServerColumnEncryptionCertificateStoreProvider можно использовать для хранения главных ключей столбцов в хранилище сертификатов Windows. Используйте мастер постоянного шифрования в SQL Server Management Studio (SSMS) или другие средства, поддерживающие создание главного ключа столбца и шифрование столбцов определения ключа в базе данных. Тот же самый мастер позволяет создать самозаверяющий сертификат в хранилище сертификатов Windows, который будет использовать в качестве главного ключа столбца для постоянного шифрования данных. Дополнительные сведения о столбце шифрования главного ключа столбца и посетите ключа синтаксис T-SQL [CREATE COLUMN MASTER KEY](/sql-docs/docs/t-sql/statements/create-column-master-key-transact-sql) и [Создание ключа ШИФРОВАНИЯ СТОЛБЦА](/sql-docs/docs/t-sql/statements/create-column-encryption-key-transact-sql) соответственно.

Имя SQLServerColumnEncryptionCertificateStoreProvider — «MSSQL_CERTIFICATE_STORE» и могут запрашиваться getName() API объекта поставщика. Он автоматически регистрируется с помощью драйвера и без проблем может быть использован без изменения приложения.

> [!IMPORTANT]  
>  Реализация SQLServerColumnEncryptionCertificateStoreProvider драйвера JDBC в операционных системах Windows только и имеет зависимость от sqljdbc_auth.dll, которая доступна в пакете драйверов.  Чтобы использовать этот поставщик, скопируйте файл sqljdbc_auth.dll каталог в пути системы Windows на компьютере, где установлен драйвер JDBC. Или можно задать системное свойство java.libary.path для указания каталога, в котором содержится файл sqljdbc_auth.dll. При использовании 32-разрядной виртуальной машины Java (JVM) следует использовать файл sqljdbc_auth.dll в папке x86 folder, даже если используется операционная система x64. При использовании 64-разрядной виртуальной машины и процессора x64 используйте файл sqljdbc_auth.dll в папке x64. Например если вы используете 32-разрядной виртуальной машины Java и JDBC драйвера в каталог по умолчанию, можно указать расположение библиотеки DLL с помощью следующий аргумент виртуальной машины (VM) при запуске приложения Java:  
`-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`
        
### <a name="using-java-key-store-provider"></a>С помощью поставщика хранилища ключей Java  
Драйвер JDBC поставляется со встроенной ключ хранения реализации поставщика для хранилища ключей Java. Драйвер автоматически создает и регистрирует поставщик для хранилища ключей Java, в том случае, если **keyStoreAuthentication** свойство строки соединения в строке соединения присутствует и имеет значение «JavaKeyStorePassword» (см. в разделе Подробнее см. ниже). Имя поставщика хранилища ключей Java — MSSQL_JAVA_KEYSTORE. Это имя также могут запрашиваться SQLServerColumnEncryptionJavaKeyStoreProvider.getName() API. 

Чтобы разрешить клиентского программного обеспечения для декларативного указания учетных данных, драйвер должен проходить проверку подлинности в хранилище ключей Java представлены три новых ключевых слов строки подключения. Драйвер будет инициализировать поставщика на основе значений из следующих трех свойств строки соединения, для конкретных подключений. 
  
 **keyStoreAuthentication:** идентифицирует хранилище ключей для использования. С Microsoft JDBC Driver 6.0 для SQL Server могут проходить проверку подлинности в хранилище ключей Java только через это свойство. Для хранилища ключей Java значение этого свойства должно быть «JavaKeyStorePassword».   
  
 **keyStoreLocation:** путь файл ключей Java с помощью главного ключа столбца. Обратите внимание, что путь включает имя файла хранилища ключей.  
  
 **keyStoreSecret:** секретный код или пароль, используемый для хранилище ключей, а также как и для ключа. Обратите внимание, что для использования в хранилище ключей Java хранилище ключей и пароль ключа должны быть одинаковыми.  

Ниже приведен пример на предоставление информации, эти учетные данные в строке подключения:

    String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
    
Эти параметры также можно с помощью объекта SQLServerDataSource set или get. В разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) для получения дополнительной информации.     
  
Драйвер JDBC автоматически создает экземпляр SQLServerColumnEncryptionJavaKeyStoreProvider, если эти учетные данные в свойства соединения. 
  
### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Создание главного ключа столбца для хранилища ключей Java
SQLServerColumnEncryptionJavaKeyStoreProvider может использоваться с типами хранилища ключей JKS или PKCS12. Чтобы создать или импортировать ключ, используемый с этим поставщиком используйте Java [keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) программы. Обратите внимание на то, что ключ должен иметь один и тот же пароль в хранилище ключей, сам. Ниже приведен пример того, как создать открытый ключ и его с помощью служебной программы keytool закрытого ключа.

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks    

Эта команда создает открытый ключ и переносит его в X.509, самозаверяющий сертификат, который сохраняется в хранилище ключей «keystore.jks», а также его закрытого ключа. Эта запись в хранилище ключей определяется псевдоним «AlwaysEncryptedKey». 

Ниже приведен пример такой же с помощью PKCS12 storetype. 

    keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword   

Обратите внимание, что если хранилище ключей имеет тип PKCS12, то программа keytool не запрашивает пароль ключа и пароль ключа должна быть обеспечена с помощью параметра - keypass, как SQLServerColumnEncryptionJavaKeyStoreProvider требует, чтобы хранилище ключей и ключ одинаковый пароль.

Можно также экспортировать сертификат из хранилища сертификатов Windows в формате PFX и использовать его с SQLServerColumnEncryptionJavaKeyStoreProvider. Экспортированный сертификат можно также импортировать в хранилище ключей Java как тип JKS хранилища ключей. 

После создания записи keytool необходимо создать метаданные главного ключа столбца в базе данных, в которой требуется имя поставщика хранилища ключей и пути к ключу. Дополнительные сведения о том, как создать метаданные главного ключа столбца [CREATE COLUMN MASTER KEY](/sql-docs/docs/t-sql/statements/create-column-master-key-transact-sql). Для SQLServerColumnEncryptionJavaKeyStoreProvider путь к разделу является просто псевдоним ключа. И SQLServerColumnEncryptionJavaKeyStoreProvider называется «MSSQL_JAVA_KEYSTORE». Это имя, с помощью getName() открытого API-интерфейса класса SQLServerColumnEncryptionJavaKeyStoreProvider можно также выполнить запрос. 

Ниже приведен синтаксис T-SQL для создания главного ключа столбца.

```  
CREATE COLUMN MASTER KEY [<CMK_name>]  
WITH  
(  
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',  
    KEY_PATH = N'<key_alias>'  
)  
```  

Для «AlwaysEncryptedKey» созданная выше будет определения главного ключа столбца:

```  
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```  
    
> [!NOTE]  
>  Встроенный в SQL Server management Studio функции не удается создать столбец определения главного ключа для хранилища ключей Java, для которого необходимо использовать команды T-SQL.  
  
### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Создание ключа шифрования столбца для хранилища ключей Java
Обратите внимание, что SQL Server management Studio или других средств может не использоваться для создания столбца ключей шифрования с помощью главных ключей столбцов в хранилище ключей Java. Клиентское приложение необходимо создавать программно с помощью класса SQLServerColumnEncryptionJavaKeyStoreProvider ключа шифрования столбца. Дополнительные сведения см. раздел «С помощью столбца поставщики хранилища главных ключей для подготовки программный ключ». 

  
### <a name="implementing-a-custom-column-master-key-store-provider"></a>Реализация настраиваемого поставщика хранилища главных ключей столбцов
Если вы хотите сохранить главные ключи столбцов в хранилище ключей, не поддерживаемый существующего поставщика, можно реализовать пользовательский поставщик, расширив класс SQLServerColumnEncryptionKeyStoreProvider и зарегистрировав поставщик с помощью Метод SQLServerConnection.registerColumnEncryptionKeyStoreProviders().
  
```  
public class MyCustomKeyStore extends SQLServerColumnEncryptionKeyStoreProvider{  
    private String name = "MY_CUSTOM_KEYSTORE";
    
    public void setName(String name)
    {
        this.name = name;
    }
    
    public String getName()
    {
        return name;
    }

    public byte[] encryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] plainTextColumnEncryptionKey)  
    {  
        // Logic for encrypting the column encryption key  
    }  
    
    public byte[] decryptColumnEncryptionKey(String masterKeyPath, String encryptionAlgorithm, byte[] encryptedColumnEncryptionKey)  
    {  
        // Logic for decrypting the column encryption key  
    }  
}  
  
```  
  
 Регистрация поставщика:  
  
```  
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();  
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();  
keyStoreMap.put(storeProvider.getName(), storeProvider);  
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);  
  
```  
  
## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>Использование поставщиков хранилищ главных ключей столбцов для программной подготовки ключей

При доступе к зашифрованным столбцам, Microsoft JDBC Driver for SQL Server прозрачно находит и вызывает поставщика хранилища главного ключа столбца справа для расшифровки ключей шифрования столбцов. Как правило, обычный код приложения не вызывает поставщики хранилища главных ключей напрямую. Однако можно создать и явным образом вызвать поставщик для программной подготовки ключей постоянного шифрования и управления ими: для создания ключа шифрования зашифрованного столбца и расшифровки ключа шифрования столбца (например, в ходе смены главного ключа столбца). Дополнительные сведения см. в разделе [Overview of Key Management for Always Encrypted](/sql-docs/docs/relational-databases/security/encryption/overview-of-key-management-for-always-encrypted)(Общие сведения об управлении ключами для постоянного шифрования).
Обратите внимание, что реализация собственных средств управления ключами может потребоваться только в том случае, если используется настраиваемый поставщик хранилища ключей. При использовании ключей, хранящихся в хранилище сертификатов Windows или в хранилище ключей Azure, можно использовать существующие средства, такие как SQL Server Management Studio или PowerShell, чтобы управлять ключами и их подготовки. При использовании ключей, хранящихся в хранилище ключей Java, необходимо подготовить ключи программным путем. Ниже примере показано использование класса SQLServerColumnEncryptionJavaKeyStoreProvider для шифрования ключа с помощью ключа, хранящегося в хранилище ключей Java.

```  
import java.sql.*;
import javax.xml.bind.DatatypeConverter;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programatically for the Java Key Store.
 */
public class AlwaysEncrypted
{
    // Alias of the key stored in the keystore.
    private static String keyAlias = "<proide key alias>";

    // Name by which the column master key will be known in the database.
    private static String columnMasterKeyName = "MyCMK";

    // Name by which the column encryption key will be known in the database.
    private static String columnEncryptionKey = "MyCEK";

    // The location of the keystore. 
    private static String keyStoreLocation = "C:\\Dev\\Always Encrypted\\keystore.jks";

    // The password of the keystore and the key.
    private static char[] keyStoreSecret = "********".toCharArray();

    /**
     * Name of the encryption algorithm used to encrypt the value of
     * the column encryption key. The algorithm for the system providers must be RSA_OAEP.
     */
    private static String algorithm = "RSA_OAEP";

    public static void main(String[] args)
    {
        String connectionString = GetConnectionString();
        try
        {
            // Note: if you are not using try-with-resources statements (as here),
            // you must remember to call close() on any Connection, Statement,
            // ResultSet objects that you create.

            // Open a connection to the database.
            Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
            try (Connection sourceConnection = DriverManager.getConnection(connectionString))
            {
                // Instantiate the Java Key Store provider.
                SQLServerColumnEncryptionKeyStoreProvider storeProvider = 
                        new SQLServerColumnEncryptionJavaKeyStoreProvider(
                                keyStoreLocation,
                                keyStoreSecret);

                byte [] encryptedCEK=getEncryptedCEK(storeProvider);

                /**
                 * Create column encryption key 
                 * For more details on the syntax refer: 
                 * https://msdn.microsoft.com/library/mt146372.aspx
                 * Encrypted column encryption key first needs to be converted into varbinary_literal from bytes, 
                 * for which DatatypeConverter.printHexBinary is used
                 */
                String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY " 
                        + columnEncryptionKey
                        + " WITH VALUES ( "
                        + " COLUMN_MASTER_KEY = " 
                        + columnMasterKeyName
                        + " , ALGORITHM =  '" 
                        + algorithm
                        + "' , ENCRYPTED_VALUE =  0x" 
                        + DatatypeConverter.printHexBinary(encryptedCEK)
                        + " ) ";

                try (Statement cekStatement = sourceConnection.createStatement())
                {
                    cekStatement.executeUpdate(createCEKSQL);
                    System.out.println("Column encryption key created with name : " + columnEncryptionKey);
                }
            }
        }
        catch (Exception e)
        {
            // Handle any errors that may have occurred.
            e.printStackTrace();
        }
    }

    // To avoid storing the sourceConnection String in your code,
    // you can retrieve it from a configuration file.
    private static String GetConnectionString()
    {

        // Create a variable for the connection string.
        String connectionUrl = "jdbc:sqlserver://localhost:1433;" +
                "databaseName=ae2;user=sa;password=********;";

        return connectionUrl;
    }

    private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException
    {
        /**
         * Following arguments needed by  SQLServerColumnEncryptionJavaKeyStoreProvider
         * 1) keyStoreLocation : 
         *      Path where keystore is located, including the keystore file name. 
         * 2) keyStoreSecret : 
         *      Password of the keystore and the key.  
         */
        String plainTextKey = "You need to give your plain text";

        // plainTextKey has to be 32 bytes with current algorithm supported
        byte[] plainCEK = plainTextKey.getBytes();

        // This will give us encrypted column encryption key in bytes
        byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(
                keyAlias,
                algorithm,
                plainCEK);

        return encryptedCEK;
    }
}

```  
  
## <a name="force-encryption-on-input-parameters"></a>Принудительное шифрование на входные параметры
  
Функция принудительное шифрование принудительно шифрует параметр при использовании постоянного шифрования. Если используется принудительное шифрование и SQL Server сообщает драйверу, что параметр не должен быть зашифрован, запрос, использующий параметр завершится ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих предоставление клиенту скомпрометированным SQL Server неверных метаданных шифрования, что может привести к раскрытию данных. Набор * методы классов SQLServerPreparedStatement и SQLServerCallableStatement и обновление\* реализованы перегруженные методы в классе SQLServerResultSet принимает логический аргумент, чтобы указать параметр force шифрования. Если значение этого аргумента равно false, драйвер не будет устанавливать параметры шифрования. Если принудительное шифрование задано значение true, то запрос параметра будут отправлены только если целевой столбец зашифрован и постоянное шифрование включено при соединении или в отчете. Это обеспечивает дополнительный уровень безопасности, гарантируя, что данные не по ошибке отправляется SQL Server как обычный текст, когда он должен быть зашифрован.  
  
 Дополнительные сведения о перегруженные методы SQLServerPreparedStatement и SQLServerCallableStatement с помощью параметра force шифрования см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-performance-impact-of-always-encrypted"></a>Управление влиянием постоянного шифрования на производительность

Поскольку постоянное шифрование является технологией шифрования на стороне клиента, значительное влияние на производительность происходит на стороне клиента, а не в базе данных. Помимо затрат на операции шифрования и расшифровки существуют и другие источники снижения производительности на стороне клиента:
- Дополнительные обращения к базе данных для получения метаданных для параметров запроса.
- Вызовы хранилища главных ключей столбцов для доступа к главному ключу столбца.

В этом разделе описывается оптимизация производительности, встроенные в драйвере Microsoft JDBC для SQL Server и как можно контролировать влияние двух указанных выше факторов на производительность.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Управление обращениями для получения метаданных для параметров запроса

Если включено постоянное шифрование для подключения, по умолчанию драйвера JDBC для SQL Server будет вызывать [sys.sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx?f=255&MSPPError=-2147217396) для каждого параметризованного запроса, передавая инструкцию запроса (без каких-либо значения параметров) для SQL Server. [sys.sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx?f=255&MSPPError=-2147217396) анализирует инструкцию запроса, чтобы узнать, если любой из параметров должен быть зашифрован и таким образом, для каждого такого возвращает сведения, относящиеся к шифрования, который позволит драйвера JDBC для SQL Server При шифровании значений параметров. Описанное выше поведение обеспечивает высокий уровень прозрачности для клиентского приложения. Приложение (и разработчику приложений), не следует учитывать, какие запросы получают доступ к зашифрованным столбцам, при условии, что значения, предназначенные для зашифрованных столбцов, передаются в Microsoft JDBC Driver для SQL Server в качестве параметров.


#### <a name="setting-always-encrypted-at-the-query-level"></a>Задание постоянного шифрования на уровне запроса

Для управления влиянием процесса получения метаданных шифрования для параметризованных запросов на производительность можно включить постоянное шифрование для отдельных запросов, а не настраивать его для соединения. Таким образом, это гарантирует, что sys.sp_describe_parameter_encryption вызывается только для запросов, которые точно имеют параметры, предназначенные для зашифрованных столбцов. Обратите внимание, что в этом случае снижается прозрачность шифрования: при изменении свойств шифрования столбцов базы данных может потребоваться изменить код приложения в соответствии с изменениями схемы.


Для управления поведением постоянного шифрования для отдельных запросов, необходимо настроить объектов отдельные инструкции, передавая Enum SQLServerStatementColumnEncryptionSetting, который указывает отправлено и получено при чтении и записи данных зашифрованные столбцы для этой инструкцией. Ниже приведены некоторые полезные рекомендации.
- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, получает доступ к зашифрованным столбцам:
    - Ключевое слово строки подключения columnEncryptionSetting значение Enabled.
    - Задайте SQLServerStatementColumnEncryptionSetting.Disabled для отдельных запросов, которые не обращаются к зашифрованным столбцам. Будет отключена возможность вызова sys.sp_describe_parameter_encryption и расшифровки всех значений в наборе результатов.
    - Задайте SQLServerStatementColumnEncryptionSetting.ResultSet для отдельных запросов, которые не имеют параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Будет отключена возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.
- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, не получают доступа к зашифрованным столбцам:
    - Ключевое слово строки подключения columnEncryptionSetting значение Disabled.
    - Задайте SQLServerStatementColumnEncryptionSetting.Enabled для отдельных запросов, имеющих параметры, которые требуется зашифровать. Будет включена возможность вызова sys.sp_describe_parameter_encryption и расшифровки результатов запроса, полученных из зашифрованных столбцов.
    - Задайте SQLServerStatementColumnEncryptionSetting.ResultSet для запросов, которые не имеют параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Будет отключена возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.

Обратите внимание, что параметры SQLServerStatementColumnEncryptionSetting не может использоваться для обхода шифрования и получения доступа к данным в виде обычного текста. Дополнительные сведения о том, как настройка шифрования столбцов в инструкции в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

В следующем примере постоянное шифрование отключено для подключения к базе данных. Запрос, выполняемый приложением, имеет параметр, предназначенный для незашифрованного столбца LastName. Запрос получает данные из зашифрованных столбцов SSN и BirthDate. В этом случае вызывать sys.sp_describe_parameter_encryption для получения метаданных шифрования не требуется. Однако необходимо включить расшифровку результатов запроса, чтобы приложение могло получать значения в виде обычного текста из двух зашифрованных столбцов. Чтобы убедиться, что используется параметр SQLServerStatementColumnEncryptionSetting.ResultSet.

```
// Assumes the same table definition as in Section "Retrieving and modifying data in encrypted columns"
// where only SSN and BirthDate columns are encrypted in the database.
String connectionUrl = "jdbc:sqlserver://localhost;databaseName=ae;user=sa;password=******;"
        + "keyStoreAuthentication=JavaKeyStorePassword;"
        + "keyStoreLocation=" + keyStoreLocation + ";"
        + "keyStoreSecret=******;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);

String filterRecord="SELECT FirstName, LastName, SSN, BirthDate FROM " + tblName + " WHERE LastName = ?";  
PreparedStatement selectStatement = connection.prepareStatement(
        filterRecord, 
        ResultSet.TYPE_FORWARD_ONLY, 
        ResultSet.CONCUR_READ_ONLY, 
        connection.getHoldability(), 
        SQLServerStatementColumnEncryptionSetting.ResultSetOnly);
selectStatement.setString(1, "Abel");  
ResultSet rs = selectStatement.executeQuery();  
while(rs.next()) {  
    System.out.println("First name: " + rs.getString("FirstName"));  
    System.out.println("Last name: " + rs.getString("LastName"));  
    System.out.println("SSN: " + rs.getString("SSN"));  
    System.out.println("Date of Birth: " + rs.getDate("BirthDate"));  
}  
rs.close();
selectStatement.close();
connection.close();
```


### <a name="column-encryption-key-caching"></a>Кэширование ключа шифрования столбца

Чтобы уменьшить количество вызовов к хранилищу главных ключей столбцов для расшифровки ключей шифрования столбцов, Microsoft JDBC Driver for SQL Server кэширует ключи шифрования столбцов открытым текстом в памяти. После получения значения ключа шифрования зашифрованного столбца метаданных базы данных драйвер сначала пытается найти ключ шифрования столбца с открытым текстом, соответствующий зашифрованному значению ключа. Драйвер обращается к хранилищу ключей, содержащему главный ключ столбца, только в том случае, если ему не удается найти значение ключа шифрования зашифрованных столбцов в кэше.

Значение срока жизни для записи ключей шифрования столбцов можно настроить в кэш, используя API setColumnEncryptionKeyCacheTtl(), в классе SQLServerConnection. Значение по умолчанию срок жизни для записи ключей шифрования столбцов в кэше составляет 2 часа. Чтобы отключить кэширование используйте значение 0. Чтобы задать любое использование значения времени жизни следующего API:
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
   
Например чтобы задать значение срока жизни 10 минут, используйте
    
    SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)

Обратите внимание, что только дней, часов, МИНУТ или СЕКУНД поддерживаются в качестве единицы измерения времени.  


## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Копирование данных, зашифрованных с помощью SQLServerBulkCopy

С SQLServerBulkCopy можно скопировать данные, которые уже зашифрованы и хранятся в одной таблице, в другую таблицу без расшифровки данных. Для этого выполните указанные далее действия.

- Убедитесь, что конфигурация шифрования целевой таблицы идентична конфигурации исходной таблицы. В частности, обе таблицы должны иметь одинаковые зашифрованные столбцы, которые должны быть зашифрованы с помощью одних и тех же типов шифрования и ключей шифрования. Примечание. Если способ шифрования какого-либо целевого столбца отличается от способа шифрования соответствующего исходного столбца, вы не сможете расшифровать данные в целевой таблице после операции копирования. Данные будут повреждены.
- Настройте подключения базы данных к исходной и целевой таблицам без включения постоянного шифрования. 
- Задайте параметр allowEncryptedValueModifications. В разделе [с помощью массового копирования с драйвером JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md) для получения дополнительной информации.
 
Примечание: Будьте внимательны при указании AllowEncryptedValueModifications, как это может привести к повреждению базы данных, так как драйвер Microsoft JDBC для SQL Server не проверяет данные шифруются на самом деле или правильность их шифрования с помощью того же шифрования тип алгоритма и ключа, где находится целевой столбец.

## <a name="see-also"></a>См. также:  
 [Always Encrypted (ядро СУБД)](/sql-docs/docs/relational-databases/security/encryption/always-encrypted-database-engine)  
  
  
