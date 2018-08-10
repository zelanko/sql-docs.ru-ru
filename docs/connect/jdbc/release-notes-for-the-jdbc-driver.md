---
title: Заметки о выпуске для драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
caps.latest.revision: 206
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1870693ad4c12a6f04cd3b01380b77de728c245c
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39454378"
---
# <a name="release-notes-for-the-jdbc-driver"></a>Заметки о выпуске для драйвера JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Обновления в Microsoft JDBC Driver 7.0 для SQL Server

Microsoft 7.0 драйвера JDBC для SQL Server полностью соответствует спецификации API JDBC 4.2. JAR-файлы в пакете 7.0 присваиваются в соответствии с совместимость версий Java. Например mssql-jdbc-7.0.0.jre8.jar файл из пакета 7.0 можно использовать с Java 8.

### <a name="support-for-jdk-10"></a>Поддержка JDK 10

Microsoft 7.0 драйвера JDBC для SQL Server теперь совместимы с Java Development Kit (JDK) версии 10.0, в дополнение к JDK 1.8. Это обновление также предоставляет драйвера «Авто-Module-Name» в виде `com.microsoft.sqlserver.jdbc` через файл своего МАНИФЕСТА.

### <a name="support-for-spatial-datatypes"></a>Поддержка пространственных типов данных

Microsoft 7.0 драйвера JDBC для SQL Server теперь поддерживает SQL Server пространственных типов данных «География» и «Геометрия». Дополнительные сведения о пространственных типов данных API-интерфейсы, а также способы их использования см. в разделе [здесь](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Реализация для JDBC 4.3, в которой представлены API java.sql.Connection beginRequest() и endRequest()

Microsoft 7.0 драйвера JDBC для SQL Server теперь реализует `beginRequest()` и `endRequest()` API из `java.sql.Connection` класса. Эти интерфейсы API были представлены в спецификации JDBC 4.3 и пакет JDK 9. Дополнительные сведения о возможности драйвера реализации этих интерфейсов API, см. в разделе [здесь](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Поддержка обнаружения и классификации данных SQL

Microsoft 7.0 драйвера JDBC для SQL Server обеспечивает поддержку для функции «поиск данных SQL и классификации» с целевой базой данных, поддерживающей эту функцию. Драйвер теперь предоставляет `SQLServerResultSet.getSensitivityClassification()` API-интерфейсы для извлечения этой информации из извлеченных результирующего набора.

Дополнительные сведения о том, как использовать эту функцию с помощью драйвера JDBC см. пример [здесь](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-new-connection-property-usebulkcopyforbatchinsert"></a>Добавить новое свойство соединения: useBulkCopyForBatchInsert

Microsoft 7.0 драйвера JDBC для SQL Server предоставляет новое свойство соединения, useBulkCopyForBatchInsert, который поддерживается только для **хранилище данных**.

Это свойство является **отключена** , по умолчанию и может быть включен для увеличения производительности приложений пользователя при отправке больших сумм данных в хранилище данных Azure. Включение этого свойства изменяет поведение операций пакетной вставки переключиться на операции массового копирования с пользователем данные. Дополнительные сведения о это свойство и его ограничения, см. в разделе [здесь](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-new-connection-property-cancelquerytimeout"></a>Добавить новое свойство соединения: cancelQueryTimeout

Microsoft 7.0 драйвера JDBC для SQL Server предоставляет новое свойство соединения `cancelQueryTimeout`, чтобы отменить `queryTimeout` на `java.sql.Connection` и `java.sql.Statement` объектов.

### <a name="added-azure-key-vault-provider-constructors"></a>Конструкторы поставщика добавлена хранилища ключей Azure

Microsoft 7.0 драйвера JDBC для SQL Server повторно вводит ранее удаленных конструктор, для `SQLServerColumnEncryptionAzureKeyVaultProvider`, разрешенных проверки подлинности с помощью пользовательского метода, реализованных на `SQLServerKeyVaultAuthenticationCallback` для получения маркера доступа.

Новые конструкторы обладают под определением:

```java
/* This constructor is added to provide backwards compatibility with 6.0
* version of the driver. It is marked deprecated for removal in next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New Constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-adal4j-version-to-160"></a>Обновленная версия ADAL4J до версии 1.6.0

Microsoft 7.0 драйвера JDBC для SQL Server был обновлен его maven зависимостью от azure-activedirectory-library-for-java (ADAL4J) до версии 1.6.0. Дополнительные сведения о зависимостях см. [здесь](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Обновления в драйвере Microsoft JDBC 6.4 для SQL Server

Microsoft JDBC Driver 6.4 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. JAR-файлы в пакете 6,4 присваиваются в соответствии с совместимость версий Java. Например mssql-jdbc-6.4.0.jre8.jar файл из 6,4 пакета рекомендуется для использования с Java 8.

### <a name="support-for-jdk-9"></a>Поддержка JDK 9

Поддержка для пакета Java Development Kit (JDK) версии 9.0 в дополнение к JDK 8.0 и 7.0.

### <a name="jdbc-43-compliance"></a>Соответствие требованиям JDBC 4.3

Поддержка спецификаций Java Database Connectivity API 4.3 в дополнение к версиям 4.1 и 4.2. Методы JDBC 4.3 API добавлены, но еще не реализован. Дополнительные сведения см. в статье о [соответствии требованиям JDBC 4.3 для JDBC Driver](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-new-connection-property-sslprotocol"></a>Добавить новое свойство соединения: sslProtocol

Добавлено новое свойство соединения, позволяющее пользователям указывать ключевое слово протокола TLS. Возможными значениями являются: «TLS», «TLSv1», «TLSv1.1», «TLSv1.2». См. в разделе [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol) сведения.

### <a name="deprecated-connection-property-fipsprovider"></a>Рекомендуется использовать свойство соединения: fipsProvider

Свойство подключения «fipsProvider» удаляется из списка свойств принятое подключение. Просмотреть сведения [здесь](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-custom-trustmanager"></a>Свойства соединения добавлены для Указание пользовательского TrustManager

Теперь драйвер поддерживает указание пользовательского TrustManager со добавлена «trustManagerClass» и «trustManagerConstructorArg» свойства соединения. Это позволяет выполнять динамическую спецификацию набор сертификатов, которые являются доверенными на уровне подключения без изменения глобальных параметров для среды виртуальной машины Java.

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters-tvp"></a>Добавлена поддержка datetime/smallDatetime в возвращающих табличное значение параметров (TVP)

Теперь драйвер поддерживает типы данных DATETIME и SMALLDATETIME при использовании возвращающих табличное значение параметров (TVP).

### <a name="added-support-for-sqlvariant-datatype"></a>Добавлена поддержка типа данных sql_variant

Драйвер JDBC теперь поддерживает типы данных sql_variant для использования с SQL Server. Sql_variant также поддерживается с помощью функции, такие как возвращающего табличное значение параметров (TVP) и BulkCopy с ниже ограничения:

1. Для значений даты: при использовании возвращающего табличное значение Параметра для заполнения таблицы, содержащей значения datetime, smalldatetime или date, хранящиеся в столбце sql_variant, вызывая методы getDateTime()/getSmallDateTime()/getDate() resultset не работает и вызывает следующее исключение:  `java java.lang.String cannot be cast to java.sql.Timestamp` Обходной путь: вместо этого используйте «getString()» или «getObject()» методов.

2. Использование возвращающего табличное значение параметра с SQL Variant для значений null

При использовании возвращающего табличное значение Параметра для заполнения таблицы и отправки значения NULL в столбец типа sql_variant, придется столкнуться исключение, как вставка значения NULL со столбцом типа sql_variant в возвращающий табличное значение параметр сейчас не поддерживается.

### <a name="implemented-prepared-statement-metadata-caching"></a>Реализован подготовленной инструкции кэширование метаданных

Драйвер JDBC реализовала подготовить инструкцию кэширование метаданных для повышения производительности. Теперь драйвер поддерживает кэширование метаданных подготовленной инструкции в драйвере со свойствами подключения «disableStatementPooling» и «значение параметра statementPoolingCacheSize». Эта функция по умолчанию отключена. Дополнительные сведения можно найти [здесь](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)

### <a name="added-support-for-aad-integrated-authentication-on-linuxmac"></a>Добавлена поддержка встроенной проверки подлинности AAD в Linux или Mac

Драйвер JDBC также поддерживает встроенную проверку подлинности Azure Active Directory во всех поддерживаемых операционных системах (Windows, Mac, Linux) с Kerberos. Кроме того в Windows операционных систем проверки подлинности пользователей с sqljdbc_auth.dll.

### <a name="updated-adal4j-version-to-140"></a>Обновленная версия ADAL4J для 1.4.0

Драйвер JDBC был обновлен его maven зависимостью от azure-activedirectory-library-for-java (ADAL4J) до версии 1.4.0. Дополнительные сведения о зависимостях см. [здесь](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Обновления в Microsoft JDBC Driver 6.2 для SQL Server

Microsoft JDBC Driver 6.2 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. JAR-файлы в пакете 6.0 присваиваются в соответствии с совместимость версий Java. Например mssql-jdbc-6.2.1.jre8.jar файл из 6.2 пакета рекомендуется для использования с Java 8.

> [!NOTE]  
> Проблемы с улучшения кэширования метаданных был найден в RTW 6.2 JDBC, выпуск состоится 29 июня 2017 г. Улучшение был выполнен откат, и новый JAR-файлы (версии 6.2.1) были выпущены на 17 июля 2017 г. на [центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1), и [центрального репозитория Maven](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Обновите ваши проекты для использования 6.2.1 выпуска JAR-файлы. Можно найти [заметки о выпуске](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) для получения дополнительных сведений.

### <a name="azure-active-directory-aad-support-for-linux"></a>Поддержка Azure Active Directory (AAD) для Linux

Подключение приложений Linux базу данных SQL Azure с использованием проверки подлинности AAD с помощью имени пользователя и пароля и доступом маркера методов.

### <a name="federal-information-processing-standard-fips-enabled-jvms"></a>Федеральная обработки информации Standard (FIPS) включена виртуальных машин Java

Теперь драйвер JDBC можно использовать на виртуальных машин Java, работающих в режиме соответствия FIPS 140 в соответствии с федеральным стандартам и соответствия требованиям.

### <a name="kerberos-authentication-improvements"></a>Улучшения проверки подлинности Kerberos

Драйвер JDBC теперь имеет поддержку:

- Метод субъекта и пароля для приложений, где конфигурации Kerberos не может быть измененный или не удалось получить новый маркер или keytab. Этот метод можно использовать для проверки подлинности SQL Server, который допускает только проверку подлинности Kerberos.
- Проверка подлинности между областями, встроенную проверку подлинности Kerberos без явного указания имени участника-службы сервера. Драйвер теперь автоматически вычисляет области даже в том случае, если он еще не были предоставлены.
- Ограниченное делегирование Kerberos, принимая олицетворение учетных данных пользователя, как объект Воплощаемые учетные данные с помощью источника данных. Затем олицетворенного учетных данных используется для установления соединения Kerberos.

### <a name="added-timeouts"></a>Добавлена времени ожидания

Драйвер JDBC теперь поддерживает следующие можно настроить значения времени ожидания, которые можно изменить в зависимости от потребностей вашего приложения:

- Время ожидания запроса, чтобы контролировать количество секунд до истечения периода ожидания, при выполнении запроса.
- Время ожидания сокета, чтобы указать число миллисекунд ожидания до начала истечения времени ожидания на сокете чтения или принять.

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Обновления в Microsoft JDBC Driver 6.1 для SQL Server

Microsoft JDBC Driver 6.1 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. Это первоначальный выпуск драйвера JDBC открытым исходным кодом и mssql-jdbc-6.1.0.jre8.jar mssql-jdbc-6.1.0.jre7.jar, файлы, которые соответствуют совместимость версий Java.

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Обновления в Microsoft JDBC Driver 6.0 для SQL Server

Microsoft JDBC Driver 6.0 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. JAR-файлы в пакете 6.0 присваиваются в соответствии с их соответствие с версией JDBC API. Например sqljdbc42.jar из пакета 6.0 он совместим с JDBC API 4.2. Аналогичным образом файл sqljdbc41.jar совместима с API JDBC 4.1.

Чтобы убедиться, что у вас есть sqljdbc41.jar или sqljdbc42.jar вправо, выполните приведенный ниже код. Если выходные данные «версии драйвера: версией 6.0.7507.100», у вас есть пакет JDBC Driver 6.0.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Постоянное шифрование

В версии SQL Server 2016 поддерживается недавно выпущенная функция постоянного шифрования Always Encrypted. Благодаря этой новой функции безопасности конфиденциальные данные никогда не отображаются в открытом тексте в экземпляре SQL Server. В основе работы функции постоянного шифрования лежит прозрачное шифрование данных в приложении, чтобы сервер SQL Server обрабатывал только зашифрованные данные, а не значения открытого текста. Даже в случае компрометации экземпляра SQL или хост-компьютера злоумышленник получит только зашифрованный текст конфиденциальных данных. Дополнительные сведения см. в статье [Использование функции Always Encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-name-idn"></a>Международное доменное имя (IDN)

Поддержка международных доменных имен (IDN) в качестве имен серверов. Дополнительные сведения см. Использование международных доменных имен на [международные функции драйвера JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md) страницы.

### <a name="parameterized-query"></a>Параметризированный запрос

Теперь поддерживается получение метаданных параметра с подготовленными инструкциями для сложных запросов, например подзапросов или соединений. Обратите внимание, что это улучшение доступно только при использовании SQL Server 2012 и более новых версий.

### <a name="azure-active-directory-aad"></a>Azure Active Directory (AAD)

Проверка подлинности AAD — это механизм подключения к базе данных SQL Azure версии 12 с помощью удостоверений в Azure Active Directory. Проверка подлинности AAD используется для централизованного управления удостоверениями пользователей базы данных и в качестве альтернативы проверке подлинности SQL Server. Драйвер JDBC 6.0 позволяет указать учетные данные AAD в строке подключения JDBC для подключения к базе данных SQL Azure. Дополнительные сведения см. свойство проверки подлинности на [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) страницы.

### <a name="table-valued-parameters"></a>Параметры, возвращающие табличные значения

Параметры, возвращающие табличное значение, упрощают маршалинг нескольких строк данных из клиентского приложения в SQL Server, устраняя потребность в нескольких круговых путях или специальной серверной логике для обработки данных. Параметры, возвращающие табличное значение, можно использовать для инкапсуляции строк данных в клиентском приложении и их отправки на сервер единой параметризованной командой. Входящие строки данных хранятся в переменной таблицы, которая может затем можно работать с помощью Transact-SQL. Дополнительные сведения см. в разделе [Using Table-Valued параметры](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="alwayson-availability-groups-ag"></a>Группы доступности AlwaysOn

Драйвер теперь поддерживает прозрачное подключение к группам доступности AlwaysOn. Он быстро обнаруживает текущую топологию AlwaysOn серверной инфраструктуры и прозрачно подключается к текущему активному серверу.

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Обновления в драйвере Microsoft JDBC 4.2 для SQL Server и более поздних версий

Microsoft JDBC Driver 4.2 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. JAR-файлы в пакете 4.2 присваиваются в соответствии с их соответствие с версией JDBC API. Например sqljdbc42.jar из пакета 4.2 он совместим с JDBC API 4.2. Аналогичным образом файл sqljdbc41.jar совместима с API JDBC 4.1.

Чтобы убедиться, что у вас есть sqljdbc41.jar или sqljdbc42.jar вправо, выполните приведенный ниже код. Если выходные данные «версии драйвера: 4.2.6420.100», у вас есть пакет драйвера JDBC 4.2.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Поддержка JDK 8

Поддержка для пакета Java Development Kit (JDK) версии 8.0 в дополнение к JDK 7.0, 6.0 и 5.0.

### <a name="jdbc-41-and-42-compliance"></a>Соответствие JDBC 4.1 и 4.2

Поддержка спецификаций Java Database Connectivity API 4.1 и 4.2 в дополнение к версии 4.0. Дополнительные сведения см. в разделе [соответствие JDBC 4.1 для драйвера JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) и [соответствие JDBC 4.2 для драйвера JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Массовое копирование

Функция массового копирования используется для быстрого копирования больших объемов данных в таблицы или представления в базах данных SQL Server. Дополнительные сведения см. в статье [Использование массового копирования с драйвером JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Возможность отката транзакций XA

Добавлены новые параметры времени ожидания для существующего автоматического отката неподготовленных транзакций. Дополнительные сведения см. в разделе [основные сведения о транзакциях XA](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Новое свойство соединения участника Kerberos

Добавлено новое свойство соединения для улучшения гибкости подключений Kerberos. Дополнительные сведения см. в статье об [использовании встроенной проверки подлинности Kerberos для подключения к SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Обновления в драйвере Microsoft JDBC 4.1 для SQL Server и более поздних версиях

### <a name="support-for-jdk-7"></a>Поддержка JDK 7

Поддержка для пакета Java Development Kit (JDK) версии 7.0 в дополнение к JDK 6.0 и 5.0.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium не поддерживается в приложениях, использующих драйвер JDBC версии 6.4, 6.0, 4.2 и 4.1.

Драйверы Microsoft JDBC версий 6.4, 6.0, 4.2 и 4.1 для приложений SQL Server не поддерживают выполнение на компьютерах с процессором Itanium.

## <a name="see-also"></a>См. также:

[Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)
