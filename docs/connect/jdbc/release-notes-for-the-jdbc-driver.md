---
title: Заметки о выпуске для драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 02/06/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b720f2b146273fb694ad0a55b013d20bd65a6a6a
ms.sourcegitcommit: c61c7b598aa61faa34cd802697adf3a224aa7dc4
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/12/2019
ms.locfileid: "56154878"
---
# <a name="release-notes-for-the-jdbc-driver"></a>Заметки о выпуске для драйвера JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-72-for-sql-server"></a>Обновления в Microsoft JDBC Driver 7.2 для SQL Server

7.2 драйвера Microsoft JDBC для SQL Server полностью соответствует спецификации API JDBC 4.2. JAR-файлы в пакете 7,2 присваиваются в соответствии с совместимость версий Java. Например mssql-jdbc-7.2.1.jre11.jar файл из 7,2 пакета следует использовать с помощью Java 11.

> [!NOTE]  
> Проблемы с синтаксический анализ инструкции SQL был найден в драйвер JDBC, RTW-версия 7.2, выпущено 31 января 2019 г. Выполнен откат изменений, а новый JAR-файлы (версия 7.2.1) выпущенных 11 февраля 2019 г. 
>
> Загрузите последние обновления для 7.2 драйвер JDBC из [центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=2063159), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.1), и [центрального репозитория Maven](https://search.maven.org/search?q=g:com.microsoft.sqlserver). Обновите ваши проекты для использования 7.2.1 выпуска JAR-файлы. Дополнительные сведения см. заметки о выпуске [7.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.1).


### <a name="support-for-jdk-11"></a>Поддержка JDK 11

7.2 драйвера Microsoft JDBC для SQL Server теперь совместимы с Java Development Kit (JDK) версии 11.0 в дополнение к JDK 1.8.

### <a name="support-for-active-directory-managed-service-identity-msi-authentication"></a>Поддержка проверки подлинности Active Directory управляемого удостоверения службы (MSI)

7.2 драйвера Microsoft JDBC для SQL Server теперь поддерживает режим проверки подлинности Active Directory управляемого удостоверения службы (MSI). Этот режим проверки подлинности применяется в ресурсах Azure с поддержкой включена функция «Identity». Обоих типов из управляемых удостоверений системы (MSI) поддерживаются получения драйвером **accessToken** для установления безопасного соединения.

Дополнительные сведения и пример приложения для использования этого режима проверки подлинности можно найти здесь: [подключение с использованием аутентификации Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)

### <a name="osgi-support"></a>Поддержка OSGi

7.2 драйвера Microsoft JDBC для SQL Server появилась поддержка OSGi к драйверу, добавив ниже реализации для `org.osgi.service.jdbc.DataSourceFactory` и `org.osgi.framework.BundleActivator` :

- `com.microsoft.sqlserver.jdbc.osgi.SQLServerDataSourceFactory`
- `com.microsoft.sqlserver.jdbc.osgi.Activator`

### <a name="sqlservererror-apis"></a>API-интерфейсы SQLServerError

7.2 драйвера Microsoft JDBC для SQL Server представляет `SQLServerException.getSQLServerError()` и `SQLServerError` считывания API для получения дополнительных сведений об ошибке, созданные на сервере. Дополнительные сведения см. в статье [Обработка ошибок](../../connect/jdbc/handling-errors.md).

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-163"></a>Обновлена версия библиотеки проверки подлинности Microsoft Azure Active Directory (ADAL4J) для Java: 1.6.3.

7.2 драйвера Microsoft JDBC для SQL Server был обновлен его зависимость Maven «Microsoft Azure библиотеку аутентификации Active Directory (ADAL4J) для Java» до версии 1.6.3, который также вводит «Java клиента среды выполнения для AutoRest» как зависимость Maven (версия: 1.6.5). Дополнительные сведения о зависимостях см. в разделе [зависимости Microsoft JDBC Driver компонентов для SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

### <a name="updated-microsoft-azure-key-vault-sdk-for-java-version-120"></a>Обновленная версия «Microsoft Azure ключ хранилища пакета SDK для Java»: 1.2.0

7.2 драйвера Microsoft JDBC для SQL Server был обновлен его зависимость Maven от «Microsoft Azure ключ хранилища пакета SDK для Java» до версии 1.2.0, что также приводит к «Microsoft Azure SDK для Key Vault WebKey» как зависимость Maven (версия: 1.2.0). Дополнительные сведения о зависимостях см. в разделе [зависимости Microsoft JDBC Driver компонентов для SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

### <a name="known-issues"></a>Известные проблемы

С 7.2 драйвера Microsoft JDBC для SQL Server с определенным параметризованных запросов существует известная проблема. Обновление версии 7.2 (v7.2.1), будет выпущено в ближайшее время для устранения этой проблемы.


## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Обновления в Microsoft JDBC Driver 7.0 для SQL Server

7.0 драйвера Microsoft JDBC для SQL Server полностью соответствует спецификации API JDBC 4.2. JAR-файлы в пакете 7.0 присваиваются в соответствии с совместимость версий Java. Например mssql-jdbc-7.0.0.jre10.jar файл из пакета 7.0 можно использовать с помощью Java 10.

### <a name="support-for-jdk-10"></a>Поддержка JDK 10

7.0 драйвера Microsoft JDBC для SQL Server теперь совместимы с Java Development Kit (JDK) версии 10.0, в дополнение к JDK 1.8. Это обновление также предоставляет возможности драйвера `Automatic-Module-Name` как `com.microsoft.sqlserver.jdbc` через файл своего МАНИФЕСТА.

### <a name="support-for-spatial-datatypes"></a>Поддержка пространственных типов данных

7.0 драйвера Microsoft JDBC для SQL Server теперь поддерживает SQL Server пространственных типов данных Geography и Geometry. Дополнительные сведения о пространственных типа данных API-интерфейсы и их использовании см. в разделе [с помощью пространственных типов данных](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Реализация для JDBC 4.3, в которой представлены API java.sql.Connection beginRequest() и endRequest()

7.0 драйвера Microsoft JDBC для SQL Server теперь реализует `beginRequest()` и `endRequest()` API из `java.sql.Connection` класса. Эти интерфейсы API были представлены в спецификации JDBC 4.3 и пакет JDK 9. Дополнительные сведения о возможности драйвера реализации этих интерфейсов API, см. в разделе [соответствие требованиям JDBC 4.3 для JDBC-драйвера](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Поддержка обнаружения и классификации данных SQL

7.0 драйвера Microsoft JDBC для SQL Server обеспечивает поддержку для обнаружения данных SQL и классификации с целевой базой данных, поддерживающей эту функцию. Драйвер теперь предоставляет `SQLServerResultSet.getSensitivityClassification()` API-интерфейсы для извлечения этой информации из полученное `ResultSet`.

Дополнительные сведения о том, как использовать эту функцию с помощью драйвера JDBC см. пример в [SQL данных обнаружения и классификации](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-connection-property-usebulkcopyforbatchinsert"></a>Добавлено свойство подключения: useBulkCopyForBatchInsert

7.0 драйвера Microsoft JDBC для SQL Server предоставляет новое свойство соединения, `useBulkCopyForBatchInsert`. Это свойство поддерживается только для хранилища данных SQL Azure.

Это свойство отключено по умолчанию. Вы можете включить его, чтобы повысить производительность приложений пользователя во время операций большие объемы данных в хранилище данных SQL Azure. Включение этого свойства изменяет поведение операций вставки переключиться на операции массового копирования с помощью пользовательских данных. Дополнительные сведения о это свойство и его ограничения, см. в разделе [операции вставки с помощью интерфейс API массового копирования для пакета](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-connection-property-cancelquerytimeout"></a>Добавлено свойство подключения: cancelQueryTimeout

7.0 драйвера Microsoft JDBC для SQL Server предоставляет новое свойство соединения, `cancelQueryTimeout`, чтобы отменить `queryTimeout` на `java.sql.Connection` и `java.sql.Statement` объектов.

### <a name="added-azure-key-vault-provider-constructors"></a>Добавлена конструкторы поставщика хранилища ключей Azure

7.0 драйвера Microsoft JDBC для SQL Server reintroduces ранее удаленных конструктор, для `SQLServerColumnEncryptionAzureKeyVaultProvider`. Это разрешено проверки подлинности через реализованы через пользовательский метод `SQLServerKeyVaultAuthenticationCallback` для получения маркера доступа.

Новые конструкторы имеют следующее определение:

```java
/* This constructor is added to provide backward compatibility with 6.0
* version of the driver. It is marked deprecated for removal in the next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-160"></a>Обновлена версия библиотеки проверки подлинности Microsoft Azure Active Directory (ADAL4J) для Java: 1.6.0.

7.0 драйвера Microsoft JDBC для SQL Server был обновлен его зависимость Maven «Microsoft Azure библиотеку аутентификации Active Directory (ADAL4J) для Java» до версии 1.6.0. Дополнительные сведения о зависимостях см. в разделе [зависимости Microsoft JDBC Driver компонентов для SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Обновления в драйвере Microsoft JDBC 6.4 для SQL Server

Microsoft JDBC Driver 6.4 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. JAR-файлы в пакете 6,4 присваиваются в соответствии с совместимость версий Java. Например mssql-jdbc-6.4.0.jre8.jar файл из 6,4 пакета необходимо использовать с Java 8.

### <a name="support-for-jdk-9"></a>Поддержка JDK 9

Драйвер поддерживает JDK версии 9.0 в дополнение к JDK 8.0 и 7.0.

### <a name="jdbc-43-compliance"></a>Соответствие требованиям JDBC 4.3

Драйвер поддерживает спецификацию Java Database Connectivity API 4.3 в дополнение к версиям 4.1 и 4.2. Методы JDBC 4.3 API добавлены, но еще не реализован. Дополнительные сведения см. в статье [Соответствие требованиям JDBC 4.3 для JDBC Driver](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-connection-property-sslprotocol"></a>Добавлено свойство подключения: sslProtocol

Новое свойство соединения позволяет пользователям указывать ключевое слово протокола TLS. Возможными значениями являются: «TLS», «TLSv1», «TLSv1.1» и «TLSv1.2». Дополнительные сведения см. в разделе [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol).

### <a name="deprecated-connection-property-fipsprovider"></a>Рекомендуется использовать свойство соединения: fipsProvider

Свойство соединения `fipsProvider` удаляется из списка свойств принятое подключение. Дополнительные сведения см. в разделе связанных [запроса на включение внесенных изменений GitHub](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-a-custom-trustmanager"></a>Свойства соединения добавлены для Указание пользовательского TrustManager

Драйвер теперь поддерживает указание пользовательского TrustManager со добавлены `trustManagerClass` и `trustManagerConstructorArg` свойства соединения. Динамически, можно указать набор сертификатов, которые являются доверенными на уровне подключения без изменения глобальных параметров для среды виртуальных машин (JVM) Java.

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters"></a>Добавлена поддержка datetime или smallDatetime, возвращающих табличные значения параметры

Драйвер теперь поддерживает типы данных `datetime` и `smallDatetime` при использовании возвращающих табличные значения параметров (Tvp).

### <a name="added-support-for-the-sqlvariant-datatype"></a>Добавлена поддержка типа данных sql_variant

Драйвер JDBC теперь поддерживает `sql_variant` типы данных для использования с SQL Server. `sql_variant` Тип данных также поддерживается с помощью функций, таких как возвращающие табличное значение параметры и массового копирования со следующими ограничениями:

* **Для значений даты**: 

  При использовании возвращающего табличное значение Параметра для заполнения таблицы, содержащей `datetime`, `smalldatetime`, или `date` значений, хранящихся в `sql_variant` столбца, вызывая метод `getDateTime()`, `getSmallDateTime()`, или `getDate()` метод в результирующем наборе не работает и вызывает следующее исключение:

  `java java.lang.String cannot be cast to java.sql.Timestamp`
    
  Чтобы обойти это ограничение, используйте `getString()` или `getObject()` метод вместо этого.

* **Использование возвращающего табличное значение параметра с sql_variant для значений null**.
  
  При использовании возвращающего табличное значение Параметра для заполнения таблицы и отправки значение NULL для `sql_variant` тип столбца, можно столкнуться при возникновении исключения. Вставка значения NULL с типом столбца `sql_variant` в возвращающий табличное значение параметр сейчас не поддерживается.

### <a name="implemented-prepared-statement-metadata-caching"></a>Реализовано кэширование метаданных подготовленной инструкции

Драйвер JDBC реализовано кэширование метаданных подготовленной инструкции для повышения производительности. Теперь драйвер поддерживает кэширование метаданных подготовленной инструкции в драйвере с `disableStatementPooling` и `statementPoolingCacheSize` свойства соединения. Эта функция по умолчанию отключена. Дополнительные сведения см. в разделе [подготовить инструкцию кэширование метаданных для драйвера JDBC](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md).

### <a name="added-support-for-azure-ad-integrated-authentication-on-linuxmac"></a>Добавлена поддержка интегрированная проверка подлинности Azure AD в Linux или Mac

Драйвер JDBC поддерживает встроенную проверку подлинности Azure Active Directory во всех поддерживаемых операционных системах (Windows, Linux, Mac) с Kerberos. Кроме того в операционных системах Windows, пользователи могут проходить проверку подлинности с sqljdbc_auth.dll.

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-140"></a>Обновлена версия библиотеки проверки подлинности Microsoft Azure Active Directory (ADAL4J) для Java: 1.4.0.

Драйвер JDBC был обновлен его зависимость Maven «Microsoft Azure библиотеку аутентификации Active Directory (ADAL4J) для Java» до версии 1.4.0. Дополнительные сведения о зависимостях см. в разделе [зависимости Microsoft JDBC Driver компонентов для SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Обновления в Microsoft JDBC Driver 6.2 для SQL Server

Microsoft JDBC Driver 6.2 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. JAR-файлы в пакете 6.2 присваиваются в соответствии с совместимость версий Java. Например mssql-jdbc-6.2.2.jre8.jar файл из 6.2 пакета рекомендуется для использования с Java 8.

> [!NOTE]  
> Проблемы с улучшения кэширования метаданных был найден в RTW 6.2 JDBC, выпуск состоится 29 июня 2017 г. Улучшение был выполнен откат, и новый JAR-файлы (версии 6.2.1) были выпущены на 17 июля 2017 г. 
>
> Еще одно улучшение обновляется версия зависимые библиотеки Azure Key Vault 1.0.0 и новый JAR-файлы (версии 6.2.2) были выпущены на 19 октября 2017 г.
>
> Загрузите последние обновления для JDBC Driver 6.2 из [центра загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2), и [центрального репозитория Maven](https://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22). Обновите ваши проекты для использования 6.2.2 выпуска JAR-файлы. Дополнительные сведения см. заметки о выпуске [6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) и [6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2).

### <a name="azure-ad-support-for-linux"></a>Поддержка Azure AD для Linux

Подключение приложений Linux базу данных SQL Azure с использованием проверки подлинности Azure AD с помощью имени пользователя и пароля и доступом маркера методов.

### <a name="fips-enabled-jvms"></a>Виртуальных машин Java с поддержкой стандарта FIPS

Теперь драйвер JDBC можно использовать на виртуальных машин Java, работающих в режиме федеральных обработки информации Standard (FIPS) 140 соответствия в соответствии с федеральным стандартам на соответствие.

### <a name="kerberos-authentication-improvements"></a>Улучшения проверки подлинности Kerberos

Драйвер JDBC теперь имеет поддержку:

- Метод субъекта и пароля для приложений, где конфигурации Kerberos не может быть изменен, или не удалось получить новый маркер или keytab. Этот метод можно использовать для проверки подлинности на экземпляр SQL Server, который разрешает только проверку подлинности Kerberos.
- Проверка подлинности между областями, с использованием встроенной проверки подлинности Kerberos без явного указания имени участника-службы сервера. Драйвер теперь автоматически вычисляет области даже в том случае, если он не указан.
- Ограниченное делегирование Kerberos, принимая олицетворение учетных данных пользователя, как объект GSS учетных данных с помощью источника данных. Затем олицетворенного учетных данных используется для установления соединения Kerberos.

### <a name="added-timeouts"></a>Добавлена времени ожидания

Драйвер JDBC теперь поддерживает следующие настраиваемые значения времени ожидания. Можно изменить их в зависимости от потребностей вашего приложения.

- Время ожидания запроса, чтобы контролировать количество секунд до истечения периода ожидания, при выполнении запроса.
- Время ожидания сокета, чтобы указать число миллисекунд ожидания до начала истечения времени ожидания на сокете чтения или принять.

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Обновления в Microsoft JDBC Driver 6.1 для SQL Server

Microsoft JDBC Driver 6.1 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. Это первоначальный выпуск драйвера JDBC открытым исходным кодом. Он содержит файлы mssql-jdbc-6.1.0.jre8.jar и mssql-jdbc-6.1.0.jre7.jar, которые соответствуют совместимость версий Java.

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Обновления в Microsoft JDBC Driver 6.0 для SQL Server

Microsoft JDBC Driver 6.0 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. JAR-файлы в пакете 6.0 присваиваются в соответствии с их соответствие с версией JDBC API. Например sqljdbc42.jar из пакета 6.0 он совместим с JDBC API 4.2. Аналогичным образом файл sqljdbc41.jar совместима с API JDBC 4.1.

Чтобы убедиться, что имеется файл sqljdbc41.jar или sqljdbc42.jar правой, выполните приведенный ниже код. Если выходные данные «версии драйвера: версией 6.0.7507.100», у вас есть пакет JDBC Driver 6.0.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Постоянное шифрование

Драйвер поддерживает функцию Always Encrypted в SQL Server 2016. Эта функция гарантирует, что конфиденциальные данные никогда не отображается в виде обычного текста в экземпляре SQL Server. В основе работы Always Encrypted лежит прозрачное шифрование данных в приложении, чтобы SQL Server обрабатывал только зашифрованные данные, а не значения открытого текста. Даже в случае компрометации экземпляра SQL или хост-компьютера злоумышленник получит только зашифрованный текст конфиденциальных данных. Дополнительные сведения см. в статье [Использование функции Always Encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-names"></a>Международное доменное имя (IDN)

Драйвер поддерживает международные доменные имена (IDN) в качестве имени сервера. Дополнительные сведения см. в разделе «Использование международных доменных имен» в [функции поддержки различных языков драйвера JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md) статьи.

### <a name="parameterized-queries"></a>Параметризованные запросы

Драйвер теперь поддерживает получение метаданных параметра с подготовленными инструкциями для сложных запросов, например подзапросов или соединений. Обратите внимание, что это улучшение доступно только при использовании SQL Server 2012 и более новых версий.

### <a name="azure-active-directory"></a>Azure Active Directory

Проверка подлинности Azure AD — это механизм подключения к базе данных SQL Azure версии 12 с помощью удостоверений в Azure AD. Проверка подлинности AAD используется для централизованного управления удостоверениями пользователей базы данных и в качестве альтернативы проверке подлинности SQL Server. 

Драйвер JDBC 6.0 позволяет указать учетные данные Azure AD в строке подключения JDBC для подключения к базе данных SQL Azure. Дополнительные сведения см. в разделе свойство проверки подлинности в [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) статьи.

### <a name="table-valued-parameters"></a>Возвращающие табличные значения параметры

Параметры, возвращающие табличное значение, упрощают маршалинг нескольких строк данных из клиентского приложения в SQL Server, устраняя потребность в нескольких круговых путях или специальной серверной логике для обработки данных. Параметры, возвращающие табличное значение, можно использовать для инкапсуляции строк данных в клиентском приложении и их отправки на сервер единой параметризованной командой. Входящие строки данных хранятся в переменной таблицы, которая затем можно управлять с помощью Transact-SQL. Дополнительные сведения см. в разделе [использование возвращающих табличные значения параметров](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="always-on-availability-groups"></a>Группы доступности AlwaysOn

Драйвер теперь поддерживает прозрачное подключение для групп доступности AlwaysOn. Драйвер быстро обнаруживает текущую топологию групп доступности AlwaysOn серверной инфраструктуры и прозрачно подключается к текущему активному серверу.

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Обновления в драйвере Microsoft JDBC 4.2 для SQL Server и более поздних версий

Microsoft JDBC Driver 4.2 для SQL Server полностью соответствует спецификации JDBC 4.1 и 4.2. JAR-файлы в пакете 4.2 присваиваются в соответствии с их соответствие с версией JDBC API. Например sqljdbc42.jar из пакета 4.2 он совместим с JDBC API 4.2. Аналогичным образом файл sqljdbc41.jar совместима с API JDBC 4.1.

Чтобы убедиться, у вас есть правой sqljdbc42.jar или файл sqljdbc41.jar, запустите приведенный ниже код. Если выходные данные «версии драйвера: 4.2.6420.100», у вас есть пакет драйвера JDBC 4.2.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Поддержка JDK 8

Драйвер поддерживает JDK версии 8.0 в дополнение к JDK 7.0, 6.0 и 5.0.

### <a name="jdbc-41-and-42-compliance"></a>Соответствие JDBC 4.1 и 4.2

Драйвер поддерживает спецификации Java Database Connectivity API 4.1 и 4.2 в дополнение к версии 4.0. Дополнительные сведения см. в разделе [соответствия JDBC 4.1 для драйвера JDBC](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) и [соответствия JDBC 4.2 для драйвера JDBC](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Массовое копирование

Функция массового копирования используется для быстрого копирования больших объемов данных в таблицы или представления в базах данных SQL Server. Дополнительные сведения см. в статье [Использование массового копирования с драйвером JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Возможность отката транзакций XA

Добавлены новые параметры времени ожидания для существующего автоматического отката неподготовленных транзакций. Дополнительные сведения см. в разделе [транзакции XA понимание](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Новое свойство соединения участника Kerberos

Драйвер использует новое свойство соединения для улучшения гибкости подключений Kerberos. Дополнительные сведения см. в статье [Использование встроенной проверки подлинности Kerberos для соединения с SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Обновления в драйвере Microsoft JDBC 4.1 для SQL Server и более поздних версиях

### <a name="support-for-jdk-7"></a>Поддержка JDK 7

Драйвер поддерживает JDK версии 7.0 в дополнение к JDK 6.0 и 5.0.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium не поддерживается в приложениях, использующих драйвер JDBC версии 6.4, 6.0, 4.2 и 4.1.

Драйверы Microsoft JDBC версий 6.4, 6.0, 4.2 и 4.1 для приложений SQL Server не поддерживают выполнение на компьютерах с процессором Itanium.

## <a name="see-also"></a>См. также раздел

[Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)
