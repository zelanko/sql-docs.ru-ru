---
title: Заметки о выпуске для драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 04/16/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8f5f520be226d74c2c6530aacee7916aa381dc06
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66778152"
---
# <a name="release-notes-for-the-microsoft-jdbc-driver"></a>Заметки о выпуске для драйвера Microsoft JDBC Driver

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье перечислены выпуски _Microsoft JDBC Driver для SQL Server_ . Для каждой версии выпуска названы и описаны изменения.

## <a name="722"></a>7.2.2

### <a name="compliance"></a>Соответствие

16 апреля 2019 г.

| Изменение соответствий | Сведения |
| :---------------- | :------ |
| Скачайте последние обновления для драйвера JDBC версии 7.2. | &bull; &nbsp; [Центр загрузки Майкрософт](https://go.microsoft.com/fwlink/?linkid=2063159)<br/>&bull; &nbsp; [GitHub 7.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.2)<br/>&bull; &nbsp; [Maven Central](https://search.maven.org/search?q=g:com.microsoft.sqlserver) |
| Полностью соответствует спецификации API JDBC версии 4.2. | JAR-файлам в пакете 7.2 имена присваиваются в соответствии с совместимостью версий Java.<br/><br/>Например, файл mssql-jdbc-7.2.2.jre11.jar из пакета 7.2 должен использоваться с Java 11. |
| Совместимость с пакетом Java Development Kit (JDK) версии 11.0 в дополнение к JDK версии 1.8. | Microsoft JDBC Driver версии 7.2 для SQL Server совместим с пакетом Java Development Kit (JDK) версии 11.0 в дополнение к JDK версии 1.8. |
| &nbsp; | &nbsp; |

> [!NOTE]
> Обнаружена проблема в анализе инструкции SQL драйвера JDBC 7.2 Release To Web (RTW), выпущенного 31 января 2019 года. Выполнен откат изменений, а новые JAR-файлы (версии 7.2.1) выпущены 11 февраля 2019 года.
>
> Чтобы устранить проблемы с ActivityID, которые не были исправлены должным образом, было создано другое обновление для драйвера. Новые JAR-файлы (версии 7.2.2) были выпущены 16 апреля 2019 года.
> 
> Для использования JAR-файлов выпуска 7.2.2 рекомендуется обновить проекты. Дополнительные сведения см. в заметках о выпуске [GitHub 7.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.1) и [GitHub 7.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v7.2.2).

### <a name="active-directory-managed-service-identity-msi-authentication"></a>Проверка подлинности с помощью _Управляемого удостоверения службы_ (MSI) Active Directory

| Изменение MSI | Сведения |
| :--------- | :------ |
| Поддерживается режим проверки подлинности с помощью Управляемого удостоверения службы (MSI) Active Directory. | Этот режим проверки подлинности применяется в ресурсах Azure с поддержкой активной функции Identity.<br/><br/>Оба типа Управляемых удостоверений службы (MSI) поддерживаются драйвером для получения **accessToken** для установления безопасного соединения. |
| Дополнительные сведения и пример приложения для использования этого режима проверки подлинности. | См. дополнительные сведения об [установке подключения с использованием аутентификации Azure Active Directory](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md). |
| &nbsp; | &nbsp; |

### <a name="introduces-open-service-gateway-initiative-osgi-support"></a>Представление поддержки _Open Service Gateway Initiative_ (OSGi)

| Изменение OSGi | Сведения |
| :---------- | :------ |
| Добавлена реализация **DataSourceFactory**. | &bull; &nbsp; `org.osgi.service.jdbc.DataSourceFactory`<br/>&bull; &nbsp; `com.microsoft.sqlserver.jdbc.osgi.SQLServerDataSourceFactory` |
| Добавлена реализация **Activator**. | &bull; &nbsp; `org.osgi.framework.BundleActivator`<br/>&bull; &nbsp; `com.microsoft.sqlserver.jdbc.osgi.Activator` |
| &nbsp; | &nbsp; |

### <a name="introduces-sqlservererror-apis"></a>Представление API-интерфейсов _SQLServerError_

| Изменение API ошибок | Сведения |
| :--------------- | :------ |
| Представлен API SQLServerError. | Метод получения API для извлечения дополнительных сведений об ошибке, созданной на сервере.<br/><br/>&bull; &nbsp; `SQLServerException.getSQLServerError()`<br/>&bull; &nbsp; `SQLServerError` |
| Дополнительные сведения. | См. дополнительные сведения об [обработке ошибок](../../connect/jdbc/handling-errors.md). |
| &nbsp; | &nbsp; |

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-163"></a>Обновлена _Библиотека проверки подлинности Microsoft Azure Active Directory (ADAL4J) для Java_ версии 1.6.3.

| Изменение ADAL4J | Сведения |
| :------------ | :------ |
| Зависимость Maven в ADAL4J обновлена до версии 1.6.3. | &nbsp; |
| _Клиентская среда выполнения Java для AutoRest_ представлена в качестве зависимости Maven версии 1.6.5. | &nbsp; |
| Дополнительные сведения. | См. дополнительные сведения о [зависимостях компонентов Microsoft JDBC Driver для SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="updated-microsoft-azure-key-vault-sdk-for-java-version-120"></a>_Пакет SDK для Microsoft Azure Key Vault для Java_ обновлен до версии 1.2.0

| Изменение пакета SDK для Key Vault | Сведения |
| :------------------- | :------ |
| Зависимость Maven _для пакета SDK для Microsoft Azure Key Vault для Java_ обновлена до версии 1.2.0. | &nbsp; |
| Общие сведения о зависимости Maven версии 1.2.0 для пакета _Microsoft Azure SDK для Key Vault WebKey_. | &nbsp; |
| Дополнительные сведения. | См. дополнительные сведения о [зависимостях компонентов Microsoft JDBC Driver для SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Известные проблемы

| Известные проблемы | Сведения |
| :----------- | :------ |
| Параметризованные запросы в некоторых случаях. | Чтобы устранить эту проблему, в феврале 2019 года было выпущено обновление версии 7.2.0 (7.2.1). |
| Удаление из ActivityIds. | Чтобы устранить эту проблему, в апреле 2019 года было выпущено обновление версии 7.2.1 (7.2.2). |
| &nbsp; | &nbsp; |

## <a name="70"></a>7.0

Microsoft JDBC Driver версии 7.0 для SQL Server полностью соответствует спецификации API JDBC версии 4.2. JAR-файлам в пакете 7.0 имена присваиваются в соответствии с совместимостью версий Java. Например, файл mssql-jdbc-7.0.0.jre10.jar из пакета 7.0 должен использоваться с Java 10.

### <a name="support-for-jdk-10"></a>Поддержка JDK 10

Microsoft JDBC Driver версии 7.0 для SQL Server совместим с пакетом Java Development Kit (JDK) версии 10.0 в дополнение к JDK версии 1.8. Это обновление также предоставляет `Automatic-Module-Name` драйвера в качестве `com.microsoft.sqlserver.jdbc` с помощью файла манифеста.

### <a name="support-for-spatial-datatypes"></a>Поддержка пространственных типов данных

Microsoft JDBC Driver версии 7.0 для SQL Server теперь поддерживает пространственные типы данных, такие как география и геометрия. Дополнительные сведения о пространственных типах данных API-интерфейсов и их использовании см. [здесь](../../connect/jdbc/use-spatial-datatypes.md).

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>Реализация для JDBC 4.3, в которой представлены API java.sql.Connection beginRequest() и endRequest()

Microsoft JDBC Driver версии 7.0 для SQL Server теперь реализует API `beginRequest()` и `endRequest()` из класса `java.sql.Connection`. Эти API-интерфейсы были представлены в спецификации JDBC 4.3 и JDK 9. Дополнительные сведения о возможности драйвера реализовать эти API-интерфейсы см. в статье[Соответствие требованиям JDBC 4.3 для JDBC Driver](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="support-for-sql-data-discovery-and-classification"></a>Поддержка обнаружения и классификации данных SQL

Microsoft JDBC Driver версии 7.0 для SQL Server обеспечивает поддержку для обнаружения и классификации данных SQL в любой целевой базе данных, поддерживающей эту функцию. Драйвер теперь предоставляет API-интерфейсы `SQLServerResultSet.getSensitivityClassification()` для извлечения этой информации из полученного `ResultSet`.

Дополнительные сведения об использовании этой функции с помощью драйвера JDBC см. в примере в статье [Обнаружение и классификация данных SQL](../../connect/jdbc/data-discovery-classification-sample.md).

### <a name="added-connection-property-usebulkcopyforbatchinsert"></a>Добавлено свойство подключения: useBulkCopyForBatchInsert

Microsoft JDBC Driver версии 7.0 для SQL Server предоставляет новое свойство соединения — `useBulkCopyForBatchInsert`. Это свойство поддерживается только Хранилищем данных SQL Azure.

По умолчанию это свойство отключено. Вы можете включить его, чтобы повысить производительность пользовательских приложений при отправке больших объемов данных в Хранилище данных SQL Azure. Включение этого свойства изменяет поведение операций пакетной вставки на переход на операции массового копирования с предоставленными пользователем данными. Дополнительные сведения об этом свойстве и его ограничениях см. в статье [Использование API массового копирования для операции пакетной вставки](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md).

### <a name="added-connection-property-cancelquerytimeout"></a>Добавлено свойство подключения: cancelQueryTimeout

Microsoft JDBC Driver версии 7.0 для SQL Server предоставляет новое свойство подключения, `cancelQueryTimeout`, для отключения `queryTimeout` на объектах `java.sql.Connection` и `java.sql.Statement`.

### <a name="added-azure-key-vault-provider-constructors"></a>Добавлены конструкторы поставщика Azure Key Vault

Microsoft JDBC Driver версии 7.0 для SQL Server возвращает ранее удаленный конструктор для `SQLServerColumnEncryptionAzureKeyVaultProvider`. Это дало возможность при выполнении проверки подлинности с помощью пользовательского метода, реализованного через `SQLServerKeyVaultAuthenticationCallback`, получить токен доступа.

Новые конструкторы имеют следующее определение.

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

Microsoft JDBC Driver версии 7.0 для SQL Server обновил зависимость Maven "Библиотека проверки подлинности Microsoft Azure Active Directory (ADAL4J) для Java" до версии 1.6.0. Дополнительные сведения см. в статье [Зависимости компонентов Microsoft JDBC Driver для SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="64"></a>6.4

Microsoft JDBC Driver версии 6.4 для SQL Server полностью соответствует спецификации JDBC версий 4.1 и 4.2. JAR-файлам в пакете 6.4 имена присваиваются в соответствии с совместимостью версий Java. Например, файл mssql-jdbc-6.4.0.jre8.jar из пакета 6.4 должен использоваться с Java 8.

### <a name="support-for-jdk-9"></a>Поддержка JDK 9

Драйвер поддерживает JDK версии 9.0 в дополнение к версиям 8.0 и 7.0.

### <a name="jdbc-43-compliance"></a>Соответствие требованиям JDBC 4.3

Драйвер поддерживает спецификацию Java Database Connectivity API 4.3 в дополнение к версиям 4.1 и 4.2. Методы API JDBC 4.3 добавлены, но еще не реализованы. Дополнительные сведения см. в статье [Соответствие требованиям JDBC 4.3 для JDBC Driver](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md).

### <a name="added-connection-property-sslprotocol"></a>Добавлено свойство подключения: sslProtocol

Новое свойство подключения дает пользователям возможность указывать ключевое слово протокола TLS. Возможными значениями являются TLS, TLSv1, TLSv1.1 и TLSv1.2. Дополнительные сведения см. на странице [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol).

### <a name="deprecated-connection-property-fipsprovider"></a>Устаревшее свойство подключения: fipsProvider

Свойство подключения `fipsProvider` удалено из списка принятых свойств подключения. Дополнительные сведения см. на странице [Запрос на вытягивание GitHub](https://github.com/Microsoft/mssql-jdbc/pull/460).

### <a name="added-connection-properties-for-specifying-a-custom-trustmanager"></a>Добавлены свойства подключения для указания пользовательского TrustManager

Теперь драйвер поддерживает указание пользовательского TrustManager с добавленными свойствами подключения `trustManagerClass` и `trustManagerConstructorArg`. Вы можете динамически указывать набор сертификатов, которые проверяются при каждом подключении, без изменения глобальных параметров среды виртуальной машины Java (JVM).

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters"></a>В параметры, возвращающие табличные значения, добавлена поддержка datetime или smallDatetime

Теперь при использовании параметров, возвращающих табличные значения, драйвер поддерживает типы данных `datetime` и `smallDatetime`.

### <a name="added-support-for-the-sqlvariant-datatype"></a>Добавлена поддержка типа данных sql_variant

Теперь для использования с SQL Server драйвер JDBC поддерживает типы данных `sql_variant`. Тип данных `sql_variant` также поддерживается такими функциями, как параметры табличных значений и массовое копирование, со следующими ограничениями.

* **Для значений даты**: 

  Когда вы используете параметр табличного значения для заполнения таблицы, которая содержит значения `datetime`, `smalldatetime` или `date`, хранящиеся в столбце `sql_variant`, вызывается метод `getDateTime()`, `getSmallDateTime()` или `getDate()`, когда результирующий набор не работает и выдает следующее исключение.

  `java java.lang.String cannot be cast to java.sql.Timestamp`
    
  Чтобы этого избежать, используйте метод `getString()` или `getObject()`.

* **Использование возвращающего табличное значение параметра с sql_variant для значений null**.
  
  При использовании параметра табличного значения для заполнения таблицы и отправки значения NULL в столбец типа `sql_variant` будет возникать исключение. Вставка значения NULL в столбец типа `sql_variant` в параметре табличного значения в настоящее время не поддерживается.

### <a name="implemented-prepared-statement-metadata-caching"></a>Реализовано кэширование метаданных подготовленной инструкции

В драйвере JDBC реализовано кэширование метаданных подготовленной инструкции для повышения производительности. Теперь драйвер поддерживает кэширование метаданных подготовленной инструкции в драйвере с использованием свойств подключения `disableStatementPooling` и `statementPoolingCacheSize`. Эта функция по умолчанию отключена. Дополнительные сведения см. в разделе [Кэширование метаданных подготовленной инструкции для JDBC Driver](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md).

### <a name="added-support-for-azure-ad-integrated-authentication-on-linuxmac"></a>Добавлена ​​поддержка Azure AD Integrated в Linux и Mac

Драйвер JDBC поддерживает встроенную проверку подлинности Azure Active Directory во всех поддерживаемых операционных системах (Windows, Linux, Mac) с Kerberos. Кроме того, в операционных системах Windows пользователи могут проходить проверку подлинности с помощью sqljdbc_auth.dll.

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-140"></a>Обновлена версия библиотеки проверки подлинности Microsoft Azure Active Directory (ADAL4J) для Java: 1.4.0.

В драйвере JDBC зависимость Maven "Библиотека проверки подлинности Microsoft Azure Active Directory (ADAL4J) для Java" обновлена до версии 1.4.0. Дополнительные сведения см. в статье [Зависимости компонентов Microsoft JDBC Driver для SQL Server](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md).

## <a name="62"></a>6.2

Microsoft JDBC Driver версии 6.2 для SQL Server полностью соответствует спецификации JDBC версий 4.1 и 4.2. JAR-файлам в пакете 6.2 имена присваиваются в соответствии с совместимостью версий Java. Например, файл mssql-jdbc-6.2.2.jre8.jar из пакета 6.2 должен использоваться с Java 8.

> [!NOTE]  
> Проблема с улучшением кэширования метаданных была обнаружена в RTW JDBC 6.2, выпущенном 29 июня 2017 года. Выполнен откат улучшений, а новые JAR-файлы (версии 6.2.1) выпущены 17 июля 2017 года. 
>
> С помощью еще одного улучшения версия зависимой библиотеки Azure Key Vault обновлена до версии 1.0.0, а новые файлы JAR-файлы (версии 6.2.2) были выпущены 19 октября 2017 года.
>
> Скачайте последние обновления для драйвера JDBC 6.2 из [центра загрузок Майкрософт](https://go.microsoft.com/fwlink/?linkid=852460), [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2) и [Maven Central](https://search.maven.org/search?q=g:com.microsoft.sqlserver). Для использования JAR-файлов выпуска 6.2.2 обновите проекты. Дополнительные сведения см. в заметках о выпуске [6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1) и [6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2).

### <a name="azure-ad-support-for-linux"></a>Поддержка Azure AD для Linux

Подключите свои приложения Linux к базе данных SQL Azure, используя проверку подлинности Azure AD через имя пользователя и пароль, а также методы доступа к токену.

### <a name="fips-enabled-jvms"></a>Виртуальные машины Java с поддержкой стандарта FIPS

Теперь драйвер JDBC можно использовать на виртуальных машинах Java, работающих в режиме использования федерального стандарта обработки информации (FIPS) 140 в соответствии с федеральными стандартами.

### <a name="kerberos-authentication-improvements"></a>Улучшения проверки подлинности Kerberos

Теперь драйвер JDBC поддерживает следующее.

- Метод субъект/пароль для приложений, в которых конфигурация Kerberos не может быть изменена или не может получить новый токен или таблицу ключей. Этот метод можно использовать для проверки подлинности на экземпляре SQL Server, который разрешает только проверку подлинности Kerberos.
- Проверка подлинности между областями с использованием встроенной проверки подлинности Kerberos без явного указания имени участника-службы сервера. Теперь драйвер автоматически вычисляет области, даже если они не указаны.
- Ограниченное делегирование Kerberos путем принятия учетных данных олицетворенного пользователя в качестве объекта учетных данных GSS через источник данных. Эти олицетворенные учетные данные затем используются для установления подключения Kerberos.

### <a name="added-timeouts"></a>Добавлено время ожидания

Теперь драйвер JDBC поддерживает следующие настраиваемые значения времени ожидания. Вы можете изменить их в зависимости от потребностей своего приложения.

- Время ожидания запроса для контроля количества секунд ожидания до истечения времени ожидания при выполнении запроса.
- Время ожидания сокета для указания количества миллисекунд ожидания до истечения времени ожидания чтения или принятия сокета.

## <a name="61"></a>6.1

Microsoft JDBC Driver версии 6.1 для SQL Server полностью соответствует спецификации JDBC версий 4.1 и 4.2. Это первоначальный выпуск драйвера JDBC с открытым исходным кодом. Он содержит файлы mssql-jdbc-6.1.0.jre8.jar и mssql-jdbc-6.1.0.jre7.jar, которые соответствуют совместимости версий Java.

## <a name="60"></a>6.0

Microsoft JDBC Driver версии 6.0 для SQL Server полностью соответствует спецификации JDBC версий 4.1 и 4.2. JAR-файлам в пакете 6.0 имена присваиваются в соответствии с их совместимостью с версией API JDBC. Например, файл sqljdbc42.jar из пакета 6.0 совместим с API JDBC 4.2. Аналогичным образом файл sqljdbc41.jar совместим с API JDBC 4.1.

Чтобы убедиться, что у вас есть правильный файл sqljdbc42.jar или sqljdbc41.jar, запустите следующие строки кода. Если выводится сообщение "Версия драйвера: 6.0.7507.100", у вас есть пакет драйвера JDBC 6.0.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Always Encrypted

Драйвер поддерживает функцию постоянного шифрования в SQL Server 2016. Эта функция гарантирует, что конфиденциальные данные никогда не будут отображаться в виде открытого текста в экземпляре SQL Server. В основе работы Always Encrypted лежит прозрачное шифрование данных в приложении, чтобы SQL Server обрабатывал только зашифрованные данные, а не значения открытого текста. Даже в случае компрометации экземпляра SQL или хост-компьютера злоумышленник получит только зашифрованный текст конфиденциальных данных. Дополнительные сведения см. в статье [Использование функции Always Encrypted с драйвером JDBC](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md).

### <a name="internationalized-domain-names"></a>Международное доменное имя (IDN)

Драйвер поддерживает международные доменные имена (IDN) в качестве имен серверов. Дополнительные сведения см. в разделе "Использование международных доменных имен" в статье [Функции поддержки различных языков драйвера JDBC](../../connect/jdbc/international-features-of-the-jdbc-driver.md).

### <a name="parameterized-queries"></a>Параметризованные запросы

Драйвер теперь поддерживает получение метаданных параметра с подготовленными инструкциями для сложных запросов, например подзапросов или соединений. Обратите внимание, что это улучшение доступно только при использовании SQL Server 2012 и более новых версий.

### <a name="azure-active-directory"></a>Azure Active Directory

Проверка подлинности Active Directory — это механизм подключения к базе данных Azure SQL версии 12 с помощью удостоверений в Azure AD. Проверка подлинности AAD используется для централизованного управления удостоверениями пользователей базы данных и в качестве альтернативы проверке подлинности SQL Server. 

Вы можете использовать драйвер JDBC 6.0, чтобы указать учетные данные AAD в строке подключения JDBC для подключения к базе данных SQL Azure. Дополнительные сведения см. в разделе о свойстве проверки подлинности в статье [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).

### <a name="table-valued-parameters"></a>Возвращающие табличные значения параметры

Параметры, возвращающие табличное значение, упрощают маршалинг нескольких строк данных из клиентского приложения в SQL Server, устраняя потребность в нескольких круговых путях или специальной серверной логике для обработки данных. Параметры, возвращающие табличное значение, можно использовать для инкапсуляции строк данных в клиентском приложении и их отправки на сервер единой параметризованной командой. Входящие строки данных хранятся в переменной таблицы, которой затем можно управлять с помощью Transact-SQL. Дополнительные сведения см. в разделе [Использование параметров, возвращающих табличные значения](../../connect/jdbc/using-table-valued-parameters.md).

### <a name="always-on-availability-groups"></a>Группы доступности AlwaysOn

Теперь драйвер поддерживает прозрачное подключение к группам доступности Always On. Драйвер быстро обнаруживает текущую топологию групп доступности AlwaysOn серверной инфраструктуры и прозрачно подключается к текущему активному серверу.

## <a name="42"></a>4.2

Microsoft JDBC Driver версии 4.2 для SQL Server полностью соответствует спецификации JDBC версий 4.1 и 4.2. JAR-файлам в пакете 4.2 имена присваиваются в соответствии с их совместимостью с версией API JDBC. Например, файл sqljdbc42.jar из пакета 4.2 совместим с API JDBC 4.2. Аналогичным образом файл sqljdbc41.jar совместим с API JDBC 4.1.

Чтобы убедиться, что у вас есть правильный файл sqljdbc42.jar или sqljdbc41.jar, запустите следующие строки кода. Если выводится сообщение "Версия драйвера: 4.2.6420.100", у вас есть пакет драйвера JDBC 4.2.

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>Поддержка JDK 8

Драйвер поддерживает JDK версии 8.0 в дополнение к версиям 7.0, 6.0 и 5.0.

### <a name="jdbc-41-and-42-compliance"></a>Соответствие JDBC 4.1 и 4.2

Драйвер поддерживает спецификации Java Database Connectivity API 4.1 и 4.2 в дополнение к версии 4.0. Дополнительные сведения см. в статьях [Соответствие JDBC 4.1 для JDBC Driver](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md) и [Соответствие JDBC 4.2 для JDBC Driver](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md).

### <a name="bulk-copy"></a>Массовое копирование

Функция массового копирования используется для быстрого копирования больших объемов данных в таблицы или представления в базах данных SQL Server. Дополнительные сведения см. в статье [Использование массового копирования с драйвером JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

### <a name="xa-transaction-rollback-option"></a>Возможность отката транзакций XA

Добавлены новые параметры времени ожидания для существующего автоматического отката неподготовленных транзакций. Дополнительные сведения см. в статье [Основные сведения о транзакциях XA](../../connect/jdbc/understanding-xa-transactions.md).

### <a name="new-kerberos-principal-connection-property"></a>Новое свойство соединения участника Kerberos

Драйвер использует новое свойство соединения для улучшения гибкости подключений Kerberos. Дополнительные сведения см. в статье [Использование встроенной проверки подлинности Kerberos для соединения с SQL Server](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md).

## <a name="41"></a>4.1

### <a name="support-for-jdk-7"></a>Поддержка JDK 7

Драйвер поддерживает JDK версии 7.0 в дополнение к версиям 6.0 и 5.0.

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium не поддерживается в приложениях, использующих драйвер JDBC версии 6.4, 6.0, 4.2 и 4.1.

Драйверы Microsoft JDBC версий 6.4, 6.0, 4.2 и 4.1 для приложений SQL Server не поддерживают выполнение на компьютерах с процессором Itanium.

## <a name="see-also"></a>См. также раздел

[Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)
