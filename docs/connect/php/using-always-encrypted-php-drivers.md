---
title: Использование функции Always Encrypted с драйверами PHP для SQL Server | Документы Майкрософт
ms.date: 01/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: v-kaywon
ms.author: v-kaywon
manager: mbarwin
ms.openlocfilehash: 5c82c32922712b377fd732b6745b1761e9f32a82
ms.sourcegitcommit: afc0c3e46a5fec6759fe3616e2d4ba10196c06d1
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55890005"
---
# <a name="using-always-encrypted-with-the-php-drivers-for-sql-server"></a>Использование функции Always Encrypted с драйверами PHP для SQL Server
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

## <a name="applicable-to"></a>Применимо к
 -   Драйверы Майкрософт версии 5.2 для PHP для SQL Server
 
## <a name="introduction"></a>Введение

Статья содержит сведения о том, как разрабатывать приложения PHP с использованием [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и [драйверы PHP для SQL Server](../../connect/php/Microsoft-php-driver-for-sql-server.md).

Функция Always Encrypted позволяет шифровать конфиденциальные данные в клиентских приложениях, не раскрывая данные или ключи шифрования для SQL Server или Базы данных SQL Azure. Драйвер с поддержкой Always Encrypted, такой как драйвер OLE DB для SQL Server, выполняет прозрачное шифрование и расшифровку конфиденциальных данных в клиентском приложении. Драйвер автоматически определяет, какие параметры запроса соответствуют важным столбцам базы данных (защищенным с помощью Always Encrypted), и шифрует значения этих параметров перед передачей данных в SQL Server или Базу данных SQL Azure. Аналогичным образом драйвер прозрачно расшифровывает данные, полученные из зашифрованных столбцов базы в результатах запроса. Дополнительные сведения см. в разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Драйверы PHP для SQL Server используют драйвер ODBC для SQL Server для шифрования конфиденциальных данных.

## <a name="prerequisites"></a>предварительные требования

 -   Настройте функцию постоянного шифрования в базе данных. В процесс настройки входят действия по подготовке ключей Always Encrypted и настройке шифрования для выбранных столбцов базы данных. Если в базе данных постоянное шифрование еще не настроено, следуйте инструкциям в разделе [Приступая к работе с постоянным шифрованием](../../relational-databases/security/encryption/always-encrypted-database-engine.md#getting-started-with-always-encrypted). В частности база данных должна содержать определения метаданных для главного ключа столбца (CMK), ключ шифрования столбца (CEK) и таблицу, содержащую один или несколько столбцов, зашифрованных с помощью этого ключа CEK.
 -   Убедитесь, что на компьютере разработки установлен драйвер ODBC для SQL Server 17 или более поздней версии. Дополнительные сведения см. в разделе [драйвер ODBC для SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md).

## <a name="enabling-always-encrypted-in-a-php-application"></a>Для включения постоянного шифрования в приложении PHP

Самым простым способом включения шифрования параметров для зашифрованных столбцов и расшифровки результатов запросов является установка для ключевого слова строки подключения `ColumnEncryption` значения `Enabled`. Ниже приведены примеры Включение постоянного шифрования в драйвере SQLSRV и PDO_SQLSRV.

SQLSRV:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled");
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

Включение постоянного шифрования недостаточно для шифрования или расшифровки для успешного выполнения; необходимо также убедиться, что:
 -   Приложение имеет разрешения VIEW ANY COLUMN MASTER KEY DEFINITION и VIEW ANY COLUMN ENCRYPTION KEY DEFINITION для базы данных, необходимые для доступа к метаданным о ключах Always Encrypted в базе данных. Дополнительные сведения см. в разделе [базы данных разрешения](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
 -   Приложение может получить доступ к CMK, который защищает ключей CEK для запрашиваемых зашифрованных столбцов. Это требование зависит от поставщика хранилища ключей, который хранит CMK. Дополнительные сведения см. в разделе [работа с хранилищами главных ключей столбцов](#working-with-column-master-key-stores).

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Получение и изменение данных в зашифрованных столбцах

После включения постоянного шифрования для подключения, вы можете использовать стандартные API-интерфейсы SQLSRV (см. в разделе [Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)) или API-интерфейсы PDO_SQLSRV (см. в разделе [Справочник по API для драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)) для извлечения или изменения данных в столбцах зашифрованной базы данных. При условии, что приложение имеет разрешения нужную базу данных, а также можно получить доступ к главному ключу столбца, все параметры запроса, предназначенные для зашифрованных столбцов и расшифровывать данные, полученные из зашифрованных столбцов, ведет к прозрачно шифрует драйвер приложения, как если столбцы не были зашифрованы.

Если функция Always Encrypted не включена, выполнение запросов с параметрами, предназначенными для зашифрованных столбцов, завершится ошибкой. Данные по-прежнему могут извлекаться из зашифрованных столбцов, пока для них не будут указаны параметры, предназначенные для зашифрованных столбцов. Тем не менее драйвер не пытайтесь любой расшифровки, и приложение получает двоичных зашифрованных данных (в виде массивов байтов).

В приведенной ниже таблице описывается поведение запросов в зависимости от того, включена ли функция Always Encrypted:

|Характеристика запроса|Постоянное шифрование включено, и приложение может получать доступ к ключам и метаданным ключей|Постоянное шифрование включено, и приложение не может получать доступ к ключам и метаданным ключей|Постоянное шифрование отключено|
|---|---|---|---|
|Параметры, предназначенные для зашифрованных столбцов.|Значения параметров прозрачно шифруются.|Ошибка|Ошибка|
|Извлечение данных из зашифрованных столбцов без параметров, предназначенных для зашифрованных столбцов.|Результаты из зашифрованных столбцов прозрачно расшифровываются. Приложение получает значения столбца в виде обычного текста. |Ошибка|Результаты из зашифрованных столбцов не расшифровываются. Приложение получает зашифрованные значения в виде массивов байтов.|
 
В следующих примерах показано получение и изменение данных в зашифрованных столбцах. В примерах предполагается таблицу со следующей схемой. Столбцы SSN и BirthDate зашифрованы.
```
CREATE TABLE [dbo].[Patients](
 [PatientId] [int] IDENTITY(1,1),
 [SSN] [char](11) COLLATE Latin1_General_BIN2
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL,
 [BirthDate] [date]
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED,
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256',
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

### <a name="data-insertion-example"></a>Пример вставки данных

Следующие примеры демонстрируют, как использовать драйверы SQLSRV и PDO_SQLSRV для вставки строки в таблице пациентов. Обратите внимание на следующие моменты:
 -   В образце кода нет ничего, связанного с шифрованием. Драйвер автоматически обнаруживает и шифрует значения параметров SSN и BirthDate, которые предназначенные для зашифрованных столбцов. В этом случае шифрование является прозрачным для приложения.
 -   Значения, вставляемые в столбцы базы данных, включая зашифрованные столбцы, передаются как связанные параметры. Несмотря на то, что при отправке значений в незашифрованные столбцы использовать параметры необязательно (но настоятельно рекомендуется, так как это помогает предотвратить внедрение кода SQL), они требуются для значений, предназначенных для зашифрованных столбцов. Если значения, вставленные в столбцы SSN или BirthDate были переданы в качестве литералов, внедренных в инструкции запроса, выполнение запроса завершится ошибкой, так как драйвер не будет пытаться шифрования или другим образом обработать литералы в запросах. В результате сервер отклонит их как несовместимые с зашифрованными столбцами.
 -   При вставке значения с помощью параметров привязки, тип SQL, идентичный тип данных целевого столбца или поддерживается, преобразование в тип данных целевого столбца должны передаваться в базу данных. Это требование обусловлено тем, постоянное шифрование поддерживает несколько преобразований типа (Дополнительные сведения см. в разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)). Два драйвера PHP SQLSRV и PDO_SQLSRV, каждый из них имеет механизм, чтобы помочь пользователю определить тип SQL значения. Таким образом пользователь не должен явно указать тип SQL.
  -   Для драйвера SQLSRV у него есть два варианта:
   -   Зависит от драйвера PHP для определения и задать правильный тип SQL. В этом случае пользователь должен использовать `sqlsrv_prepare` и `sqlsrv_execute` для выполнения параметризованного запроса.
   -   Явно задайте тип SQL.
  -   Для драйвера PDO_SQLSRV пользователь не имеет параметр, чтобы явно задать SQL-тип параметра. Драйвер PDO_SQLSRV автоматически помогают пользователю определить тип SQL, при привязке параметра.
 -   Для драйверов определить тип SQL действуют некоторые ограничения.
  -   Драйвер SQLSRV:
   -   Если же пользователь выбирает драйвер для определения типов SQL для зашифрованных столбцов, пользователь должен использовать `sqlsrv_prepare` и `sqlsrv_execute`.
   -   Если `sqlsrv_query` является предпочтительным, пользователь отвечает за определение типов SQL для всех параметров. Указанный тип SQL должен включать длину строки для строковых типов и масштаб и точность для десятичного типа.
  -   Драйвер PDO_SQLSRV:
   -   Атрибут инструкции `PDO::SQLSRV_ATTR_DIRECT_QUERY` не поддерживается в параметризованном запросе.
   -   Атрибут инструкции `PDO::ATTR_EMULATE_PREPARES` не поддерживается в параметризованном запросе.
   
Драйвер SQLSRV и [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel;
$birthDate = "1996-10-19";
$params = array($ssn, $firstName, $lastName, $birthDate);
// during sqlsrv_prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = sqlsrv_prepare($conn, $query, $params);
sqlsrv_execute($stmt);
```

Драйвер SQLSRV и [sqlsrv_query](../../connect/php/sqlsrv-query.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Abel";
$birthDate = "1996-10-19";
// need to provide the SQL types for ALL parameters  
// note the SQL types (including the string length) have to be the same at the column definition
$params = array(array(&$ssn, null, null, SQLSRV_SQLTYPE_CHAR(11)),
                array(&$firstName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$lastName, null, null, SQLSRV_SQLTYPE_NVARCHAR(50)),
                array(&$birthDate, null, null, SQLSRV_SQLTYPE_DATE));
sqlsrv_query($conn, $query, $params);
```

Драйвер PDO_SQLSRV и [PDO::prepare](../../connect/php/pdo-prepare.md):
```
// insertion into encrypted columns must use a parameterized query
$query = "INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (?, ?, ?, ?)";
$ssn = "795-73-9838";
$firstName = "Catherine";
$lastName = "Able";
$birthDate = "1996-10-19";
// during PDO::prepare, the driver determines the SQL types for each parameter and pass them to SQL server
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
$stmt->bindParam(2, $firstName);
$stmt->bindParam(3, $lastName);
$stmt->bindParam(4, $birthDate);
$stmt->execute();
```

### <a name="plaintext-data-retrieval-example"></a>Пример извлечения данных открытым текстом

В следующих примерах демонстрируется фильтрации данных на основе зашифрованных значений и получение данных открытого текста из зашифрованных столбцов, использующих драйверы SQLSRV и PDO_SQLSRV. Обратите внимание на следующие моменты:
 -   Значение, используемое в предложении WHERE для фильтрации по столбцу SSN, необходимо передавать, используя параметр bind, чтобы перед отправкой на сервер драйвер мог его прозрачно зашифровать.
 -   При выполнении запроса со связанными параметрами, драйверами PHP автоматически определяет тип SQL для пользователя, если пользователь явно не указывает тип SQL при использовании драйвера SQLSRV.
 -   Все значения, выводимые программой, будут представлены в открытом тексте, так как драйвер прозрачно расшифровывает данные, полученные из столбцов SSN и BirthDate.
 
Примечание. Запросы могут выполнять сравнения на равенство по зашифрованным столбцам, только в том случае, если шифрование является детерминированным. Дополнительные сведения см. в разделе [Выбор детерминированного или случайного шифрования](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = sqlsrv_prepare($conn, $query, array(&$ssn));
// during sqlsrv_execute, the driver encrypts the ssn value and passes it to the database
sqlsrv_execute($stmt);
// fetch like usual
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
// since SSN is an encrypted column, need to pass the value in the WHERE clause through bind parameter
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = ?";
$ssn = "795-73-9838";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $ssn);
// during PDOStatement::execute, the driver encrypts the ssn value and passes it to the database
$stmt->execute();
// fetch like usual
$row = $stmt->fetch();
```

### <a name="ciphertext-data-retrieval-example"></a>Пример извлечения данных зашифрованного текста

Если постоянное шифрование не включено, запрос может получать данные из зашифрованных столбцов, пока для него не будут указаны параметры, предназначенные для зашифрованных столбцов.

В следующих примерах показаны извлечение двоичных зашифрованных данных из зашифрованных столбцов, использующих драйверы SQLSRV и PDO_SQLSRV. Обратите внимание на следующие моменты:
 -   Так как постоянное шифрование не включено в строке подключения, запрос возвращает зашифрованные значения SSN и BirthD в виде байтовых массивов (программа преобразует значения в строки).
 -   Запрос, получающий данные из зашифрованных столбцов с отключенным постоянным шифрованием, может иметь параметры при условии, что ни один из параметров не предназначен для зашифрованного столбца. Приведенный ниже запрос выполняет фильтрацию по столбцу LastName, который не зашифрован в базе данных. Запрос, отфильтрованный по SSN или BirthDate, завершится ошибкой.
 
SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = sqlsrv_prepare($conn, $query, array(&$lastName));
sqlsrv_execute($stmt);
$row = sqlsrv_fetch_array($stmt);
```

PDO_SQLSRV:
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName] = ?";
$lastName = "Abel";
$stmt = $conn->prepare($query);
$stmt->bindParam(1, $lastName);
$stmt->execute();
$row = $stmt->fetch();
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Как избежать распространенных проблем при запросе зашифрованных столбцов

В этом разделе описываются общие категории ошибок, возникающих при выполнении запросов к зашифрованным столбцам из приложений PHP, и приводятся рекомендации о том, как их избежать.

#### <a name="unsupported-data-type-conversion-errors"></a>Ошибки преобразования неподдерживаемых типов данных

Постоянное шифрование поддерживает несколько преобразований для зашифрованных типов данных. Подробный список поддерживаемых преобразований типов см. в статье [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Чтобы избежать ошибок при преобразовании типов данных, сделайте следующее:
 -   При использовании драйвера SQLSRV с `sqlsrv_prepare` и `sqlsrv_execute` типа SQL, а также размер столбца и количество цифр дробной части параметра определяется автоматически.
 -   При использовании драйвера PDO_SQLSRV для выполнения запроса, тип SQL с помощью размер столбца и количество цифр дробной части параметра определяется автоматически
 -   При использовании драйвера SQLSRV с `sqlsrv_query` для выполнения запроса:
  -   Тип SQL параметра либо точно совпадает с типом целевого столбца, или поддерживается преобразование из типа SQL в тип столбца.
  -   Точность и масштаб параметров, предназначенных для столбцов типов данных SQL Server `decimal` и `numeric`, соответствуют точности и масштабу, настроенным для конечного столбца.
  -   В запросах, которые изменяют конечный столбец, точность параметров, предназначенных для столбцов типов данных SQL Server `datetime2`, `datetimeoffset` или `time`, не превышает точность для конечного столбца.
 -   Не используйте атрибуты инструкции PDO_SQLSRV `PDO::SQLSRV_ATTR_DIRECT_QUERY` или `PDO::ATTR_EMULATE_PREPARES` в параметризованном запросе
 
#### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Ошибки, возникающие из-за передачи значений в виде открытого текста, а не в зашифрованном виде

Любое значение, предназначенное для зашифрованного столбца должен быть зашифрован перед отправкой на сервер. Попытка вставки, изменения или фильтрации по значению, в виде открытого текста в зашифрованном столбце приведет к возникновению ошибки. Чтобы избежать таких ошибок, убедитесь в том, что:
 -   Постоянное шифрование включено (в строке подключения задайте `ColumnEncryption` слово `Enabled`).
 -   для отправки данных, предназначенных для зашифрованных столбцов, используется параметр bind. В следующем примере запрос, который неправильно фильтрует по литералу или константе в зашифрованном столбце (SSN):
```
$query = "SELET [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
```

## <a name="controlling-performance-impact-of-always-encrypted"></a>Управление влиянием постоянного шифрования на производительность

Так как Always Encrypted является технологией шифрования на стороне клиента, значительное влияние на производительность происходит на стороне клиента, а не в базе данных. Помимо затрат на операции шифрования и расшифровки существуют и другие источники снижения производительности на стороне клиента:
 -   дополнительные круговые пути к базе данных для получения метаданных для параметров запроса;
 -   Вызовы хранилища главных ключей столбцов для доступа к главному ключу столбца.
 
### <a name="round-trips-to-retrieve-metadata-for-query-parameters"></a>круговые пути для получения метаданных для параметров запроса.

Если для соединения включена функция Always Encrypted, по умолчанию драйвер будет вызывать [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) для каждого параметризованного запроса, передавая инструкцию запроса (без значений параметров) в SQL Server. Эта хранимая процедура анализирует инструкцию запроса, чтобы узнать, должен быть зашифрован и если да, возвращает связанные с шифрованием сведения для каждого параметра Разрешить драйверу шифровать их.

Так как драйверы PHP позволяет привязать параметр в подготовленной инструкции без предоставления SQL введите, при привязке параметра при соединении с поддержкой постоянного шифрования, вызовите драйверами PHP [SQLDescribeParam](../../odbc/reference/syntax/sqldescribeparam-function.md) на параметр для получения SQL-тип, размер столбца и десятичных цифр. Эти метаданные затем используется для вызова [SQLBindParameter]( ../../odbc/reference/syntax/sqlbindparameter-function.md). Эти дополнительные `SQLDescribeParam` вызовы не требуют лишних обращений к базе данных, как драйвер ODBC уже хранится сведения на стороне клиента при `sys.sp_describe_parameter_encryption` был вызван.

Предыдущего поведения обеспечить высокий уровень прозрачности для клиентского приложения (и разработчику приложений) не обязательно должно знать, какие запросы получают доступ к зашифрованным столбцам, до тех пор, пока значения, предназначенные для зашифрованных столбцов передаются драйверу в параметры.

В отличие от драйвера ODBC для SQL Server Включение постоянного шифрования на уровне инструкции или запроса не еще поддерживается в драйверах PHP. 

### <a name="column-encryption-key-caching"></a>Кэширование ключа шифрования столбца

Чтобы уменьшить количество вызовов хранилища главных ключей столбцов для расшифровки ключей шифрования столбца (CEK), драйвер кэширует ключей CEK открытый текст в памяти. После получения зашифрованного ключа CEK (ECEK) из метаданных базы данных, драйвер ODBC сначала пытается найти соответствующий ключ CEK открытого текста зашифрованного значения ключа в кэше. Драйвер обращается к хранилищу ключей, содержащее CMK только в том случае, если не удается найти соответствующий открытый текст ключа шифрования Столбца в кэше.

Примечание. В драйвере ODBC для SQL Server записей в кэше вытесняются по истечении времени ожидания два часа. Это означает, что для данного ECEK, драйвер обращается к хранилищу ключей только один раз в течение времени существования приложения или каждые два часа, какое значение меньше.

## <a name="working-with-column-master-key-stores"></a>Работа с хранилищами главных ключей столбцов

Для шифрования или расшифровки данных, драйвер должен получить ключ CEK, настроенный для целевого столбца. Ключей CEK, хранятся в зашифрованном виде (ECEKs) в метаданных базы данных. Каждого ключа шифрования Столбца имеет соответствующий CMK, который использовался для его шифрования. [Метаданных базы данных](../../t-sql/statements/create-column-master-key-transact-sql.md) не хранит CMK; он содержит только имя хранилища ключей и информацию о хранилище ключей можно использовать для поиска CMK.

Чтобы получить значение открытого текста ECEK, драйвер сначала получает метаданные о его соответствующий CMK и CEK, и затем использует эти сведения для доступа в хранилище ключей, содержащее CMK и запрашивает его расшифровать ECEK. Драйвер взаимодействует с хранилищем ключей с помощью поставщика хранилища ключей.

Для драйвера Microsoft 5.3.0 для PHP для SQL Server поддерживаются только Windows Certificate Store Provider и хранилище ключей Azure. Другой поставщик хранилища ключей, поддерживаемых драйвером ODBC (настраиваемого поставщика хранилища ключей) не поддерживается.

### <a name="using-the-windows-certificate-store-provider"></a>Использование поставщика хранилища сертификатов Windows

Драйвер ODBC для SQL Server в Windows включает в себя встроенный столбец поставщика хранилища главного ключа для сертификата Windows Store, с именем `MSSQL_CERTIFICATE_STORE`. (Этот поставщик доступен не в macOS или Linux.) С этим поставщиком CMK хранится локально на клиентском компьютере, и никаких дополнительных настроек для приложения необходима для использования его с помощью драйвера. Тем не менее в приложении необходим доступ к сертификат и его закрытый ключ в хранилище. Дополнительные сведения см. в разделе [Create and Store Column Master Keys (Always Encrypted)](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)(Создание и хранение главных ключей столбцов (постоянное шифрование)).

### <a name="using-azure-key-vault"></a>Расширенное управление ключами с Azure Key Vault

Хранилище ключей Azure позволяет хранить ключи шифрования, пароли и другие секретные данные, с помощью Azure и может использоваться для хранения ключей для постоянного шифрования. Драйвер ODBC для SQL Server (версии 17 и более поздние версии) включает в себя встроенные главного ключа поставщика хранилища для хранилища ключей Azure. Следующие параметры подключения обработки конфигурации Azure Key Vault: `KeyStoreAuthentication`, `KeyStorePrincipalId`, и `KeyStoreSecret`. 
 -   `KeyStoreAuthentication` может принимать одно из двух возможных строковых значений: `KeyVaultPassword` и `KeyVaultClientSecret`. Эти значения контролировать, какие учетные данные проверки подлинности используются две другие ключевые слова.
 -   `KeyStorePrincipalId` принимает строку, представляющую идентификатор учетной записи требуется доступ к хранилищу ключей Azure. 
     -   Если `KeyStoreAuthentication` присваивается `KeyVaultPassword`, затем `KeyStorePrincipalId` должно быть имя пользователя Azure ActiveDirectory.
     -   Если `KeyStoreAuthentication` присваивается `KeyVaultClientSecret`, затем `KeyStorePrincipalId` должен быть идентификатор клиента приложения.
 -   `KeyStoreSecret` принимает строку, представляющую секрета учетных данных. 
     -   Если `KeyStoreAuthentication` присваивается `KeyVaultPassword`, затем `KeyStoreSecret` должен быть пароль пользователя. 
     -   Если `KeyStoreAuthentication` присваивается `KeyVaultClientSecret`, затем `KeyStoreSecret` должен быть секрет приложения, связанный с идентификатором приложения клиента.

Все три параметра должны присутствовать в строке подключения, чтобы использовать хранилище ключей Azure. Кроме того `ColumnEncryption` должно быть присвоено `Enabled`. Если `ColumnEncryption` присваивается `Disabled` , но присутствуют параметры хранилища ключей Azure, скрипт будет продолжена без ошибок, но будет выполняться без шифрования.

Следующие примеры демонстрируют для подключения к SQL Server с помощью хранилища ключей Azure.

SQLSRV:

С помощью учетной записи Azure Active Directory:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultPassword", "KeyStorePrincipalId"=>$AADUsername, "KeyStoreSecret"=>$AADPassword);
$conn = sqlsrv_connect($server, $connectionInfo);
```
С помощью идентификатора клиента приложения Azure и секрет:
```
$connectionInfo = array("Database"=>$databaseName, "UID"=>$uid, "PWD"=>$pwd, "ColumnEncryption"=>"Enabled", "KeyStoreAuthentication"=>"KeyVaultClientSecret", "KeyStorePrincipalId"=>$applicationClientID, "KeyStoreSecret"=>$applicationClientSecret);
$conn = sqlsrv_connect($server, $connectionInfo);
```

PDO_SQLSRV: С помощью учетной записи Azure Active Directory:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultPassword; KeyStorePrincipalId = $AADUsername; KeyStoreSecret = $AADPassword;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```
С помощью идентификатора клиента приложения Azure и секрет:
```
$connectionInfo = "Database = $databaseName; ColumnEncryption = Enabled; KeyStoreAuthentication = KeyVaultClientSecret; KeyStorePrincipalId = $applicationClientID; KeyStoreSecret = $applicationClientSecret;";
$conn = new PDO("sqlsrv:server = $server; $connectionInfo", $uid, $pwd);
```

## <a name="limitations-of-the-php-drivers-when-using-always-encrypted"></a>Ограничения при использовании Always Encrypted драйверов PHP

SQLSRV и PDO_SQLSRV:
 -   Linux и macOS не поддерживают Windows Certificate Store Provider
 -   Принудительное шифрование параметров
 -   Включение постоянного шифрования на уровне инструкций 
 -   При использовании Always Encrypted функция и не UTF8 языковых стандартов в Linux и macOS (например, «ru_ru. ISO-8859-1 "), вставка в столбец char(n) зашифрованных значений NULL или является пустой строкой может не работать, если на компьютере установлено кодовой странице 1252
 
SQLSRV:
 -   С помощью `sqlsrv_query` для привязки параметра без указания типа SQL
 -   С помощью `sqlsrv_prepare` для привязки параметров в пакет инструкций SQL  
 
PDO_SQLSRV:
 -   `PDO::SQLSRV_ATTR_DIRECT_QUERY` атрибут инструкции, указанные в параметризованном запросе
 -   `PDO::ATTR_EMULATE_PREPARE` атрибут инструкции, указанные в параметризованном запросе
 -   привязка параметров в пакет инструкций SQL
 
Драйверы PHP также наследуют ограничений, налагаемых драйвером ODBC для SQL Server и базе данных. См. в разделе [ограничения драйвера ODBC при использовании Always Encrypted](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) и [всегда зашифрованы подробные сведения о возможностях](../../relational-databases/security/encryption/always-encrypted-database-engine.md#feature-details).  
  
## <a name="see-also"></a>См. также:  
[Руководство по программированию для драйвера SQL PHP](../../connect/php/programming-guide-for-php-sql-driver.md)
[Справочник по API для драйвера SQLSRV](../../connect/php/sqlsrv-driver-api-reference.md)  
[Справочник по API драйвера PDO_SQLSRV](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
