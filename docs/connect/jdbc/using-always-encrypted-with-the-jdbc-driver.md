---
title: С помощью постоянного шифрования с драйвером JDBC | Документы Microsoft
ms.custom: ''
ms.date: 3/14/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 425f965c37e1d148a267566bd1980eb345cadfc6
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>С помощью постоянного шифрования с драйвером JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Эта страница содержит сведения о том, как разрабатывать приложения Java, с использованием [постоянного шифрования](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.

Постоянное шифрование позволяет клиентам Шифровать конфиденциальные данные, не раскрывая данные или ключи шифрования для SQL Server или база данных SQL Azure. Постоянное шифрование включено драйвера, таких как Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server, реализует это за счет прозрачного шифрования и расшифровки конфиденциальных данных в клиентском приложении. Драйвер автоматически определяет, какой запрос параметров соответствуют постоянного шифрования столбцов базы данных, а также шифрует значения этих параметров перед их отправкой в SQL Server или база данных SQL Azure. Аналогичным образом драйвер прозрачно расшифровывает данные, полученные из зашифрованных столбцов базы в результатах запроса. Дополнительные сведения см. в разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

## <a name="prerequisites"></a>предварительные требования
- Убедитесь, что драйвер Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server должен быть установлен на компьютере разработки. 
- Скачайте и установите файлы политики юрисдикции неограниченной стойкости Java Cryptography Extension (JCE).  Не забудьте прочитать файл сведений, включенных в ZIP-файл для инструкции по установке и соответствующие сведения о проблемах, возможности экспорта и импорта.  

    - Если используется mssql, jdbc, X.X.X.jre7.jar или sqljdbc41.jar, файлы политики можно загрузить с [загрузки файлов Java Cryptography Extension (JCE) неограниченное стойкость юрисдикции политики 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html)

    - Если используется mssql, jdbc, X.X.X.jre8.jar или sqljdbc42.jar, файлы политики можно загрузить с [загрузки файлов Java Cryptography Extension (JCE) неограниченное стойкость юрисдикции политики 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html)

    - При использовании mssql-jdbc-X.X.X.jre9.jar, необходимо загрузить файл политики не. Политики юрисдикции в Java 9 неограниченное стойкость шифрования по умолчанию.

## <a name="working-with-column-master-key-stores"></a>Работа с хранилищами главного ключа столбца
Для шифрования или расшифровки данных для зашифрованных столбцов, SQL Server поддерживает ключи шифрования столбцов. Ключи шифрования столбца хранятся в зашифрованном виде в метаданных базы данных. Каждый ключ шифрования столбца имеет соответствующий главный ключ столбца, который используется для шифрования ключа шифрования столбца. Метаданные базы данных не содержит главные ключи столбцов. Эти ключи хранятся только клиентом. Однако в метаданные базы данных содержат сведения о хранения главных ключей столбца относительно клиента. Например метаданных базы данных может сказать, что хранилище ключей, удерживая главный ключ столбца является хранилище сертификатов Windows и определенных сертификат, используемый для шифрования и расшифровки расположен в указанную папку в хранилище сертификатов Windows. Если клиент имеет доступ к этому сертификату в хранилище сертификатов Windows, его можно получить сертификат. Сертификат можно затем использовать для расшифровки ключа шифрования столбца. Затем можно использовать этот ключ шифрования для расшифровки или шифрования данных для зашифрованных столбцов, с помощью этого ключа шифрования столбца.

Microsoft JDBC Driver for SQL Server взаимодействует с использованием хранилища ключей, поставщик хранилища главного ключа столбцов, который является экземпляром класса, производного от **SQLServerColumnEncryptionKeyStoreProvider**.

### <a name="using-built-in-column-master-key-store-providers"></a>Использование встроенных поставщиков хранилища главных ключей столбцов
Microsoft JDBC Driver for SQL Server имеются следующие поставщики хранилища главных ключей встроенный столбец. Некоторые из этих поставщиков предварительно зарегистрированы с конкретными именами поставщиков (используется для поиска поставщика), а некоторые требуют дополнительных учетных данных или явная регистрация.

| Class | Описание | Имя поставщика |Предварительно зарегистрирован?|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Поставщик для хранилища ключей для хранилища ключей Azure.| AZURE_KEY_VAULT|нет|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Поставщик для хранилища сертификатов Windows.|MSSQL_CERTIFICATE_STORE|Да
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Поставщик для хранилище ключей Java|MSSQL_JAVA_KEYSTORE|Да|

Для поставщиков хранилища ключей предварительно зарегистрированными не требуется внести любые изменения кода приложения, чтобы использовать эти поставщики, но иметь в виду следующее:

- Вы (или ваш администратор баз данных) должны убедитесь, что имя поставщика, настроенные в метаданных главного ключа столбца указано правильно и путь к главному ключу столбца соответствует формату пути к ключу, допустимый для данного поставщика. Рекомендуется настроить ключей, с помощью средств, таких как SQL Server Management Studio, который автоматически создает допустимые имена поставщиков и путей при выполнении инструкции CREATE COLUMN MASTER KEY (Transact-SQL).
- Убедитесь, что приложение может получить доступ к ключа в хранилище ключей. Эта задача может включать предоставить приложению доступ к ключу или хранилище ключей, в зависимости от того, хранилище ключей или выполнения других действий конфигурации, относящиеся к хранилищу ключей. Например при помощи SQLServerColumnEncryptionJavaKeyStoreProvider необходимо указать расположение и пароль из хранилища ключей, в свойствах соединения. 

Все эти поставщики хранилища ключей описаны более подробно в последующих разделах. Необходимо реализовать один поставщик хранилища ключей для использования постоянного шифрования.

### <a name="using-azure-key-vault-provider"></a>Использование поставщика хранилища ключей Azure
Хранилище ключей Azure удобна для хранения и управления главных ключей столбцов для постоянного шифрования (в особенности, если приложение размещено в Azure). Microsoft JDBC Driver for SQL Server включает в себя встроенного поставщика, SQLServerColumnEncryptionAzureKeyVaultProvider, для приложений, имеющих ключи, хранящиеся в хранилище ключей Azure. Этот поставщик называется AZURE_KEY_VAULT. Чтобы использовать поставщик хранилища ключей Azure хранилища, разработчик приложения должен хранилища и ключи в хранилище ключей Azure и создать запись о регистрации приложения в Azure Active Directory. Зарегистрированного приложения должно быть предоставлено получить, расшифровку, Encrypt, распаковки ключ, перенос ключа и проверьте разрешения в политике доступа, определенных для хранилища ключей, специально для использования с постоянным шифрованием. Дополнительные сведения о том, как настроить хранилище ключей и создать главный ключ столбца см. в разделе [хранилище ключей Azure — шаг за шагом](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) и [создании главных ключей столбцов в хранилище ключей Azure](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault).

Для примеров на этой странице, если вы создали хранилище ключей Azure на основе главного ключа столбца и ключ шифрования столбца с помощью SQL Server Management Studio, сценарий T-SQL для повторного создания их может выглядеть как показано в примере с определенные **KEY_ ПУТЬ** и **ENCRYPTED_VALUE**:

```
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'AZURE_KEY_VAULT',
    KEY_PATH = N'https://<MyKeyValutName>.vault.azure.net:443/keys/Always-Encrypted-Auto1/c61f01860f37302457fa512bb7e7f4e8'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x01BA000001680074507400700073003A002F002F006400610076006...
)
```

Чтобы использовать хранилище ключей Azure, клиентские приложения должны создать экземпляр SQLServerColumnEncryptionAzureKeyVaultProvider и зарегистрируйте его в драйвере.

Ниже приведен пример инициализации SQLServerColumnEncryptionAzureKeyVaultProvider:  

```
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**clientID** приложения идентификатор регистрации приложения в экземпляре Azure Active Directory. **clientKey** пароль ключа зарегистрированного в это приложение, который предоставляет доступ к API хранилища ключей Azure.

После приложение создает экземпляр SQLServerColumnEncryptionAzureKeyVaultProvider, приложение необходимо зарегистрировать экземпляр с помощью драйвера, с помощью метода SQLServerConnection.registerColumnEncryptionKeyStoreProviders(). Настоятельно рекомендуется экземпляр зарегистрирован с помощью имени Уточняющий запрос по умолчанию, AZURE_KEY_VAULT, который можно получить путем вызова SQLServerColumnEncryptionAzureKeyVaultProvider.getName() API. Использует имя по умолчанию позволит вам использовать средства, такие как SQL Server Management Studio или PowerShell для подготовки и управления ключами, постоянное шифрование (средства используйте имя по умолчанию для создания объекта метаданных для главного ключа столбца). В следующем примере показано регистрации поставщика хранилища ключей Azure. Дополнительные сведения о методе SQLServerConnection.registerColumnEncryptionKeyStoreProviders() см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

```
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Если используется поставщик хранилища ключей для хранилища ключей Azure, хранилище ключей Azure реализация драйвера JDBC имеет зависимости от этих библиотек (с) (GitHub), которые должны входить в состав приложения:
>
>  [azure-sdk-for-java](https://github.com/Azure/azure-sdk-for-java)
>
>  [библиотеки Azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> Пример того, как включить эти зависимости в проект Maven см. в разделе [загрузки ADAL4J и хранилищем ключей AZURE зависимостей с помощью Apache Maven](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven)

### <a name="using-windows-certificate-store-provider"></a>С помощью поставщика хранилища сертификатов Windows
SQLServerColumnEncryptionCertificateStoreProvider можно использовать для хранения главных ключей столбцов в хранилище сертификатов Windows. Используйте мастер постоянного шифрования в SQL Server Management Studio (SSMS) или другие средства, поддерживающие создание главного ключа столбца и шифрование столбцов определения ключа в базе данных. Же мастер можно использовать для создания самозаверяющего сертификата в хранилище сертификатов Windows, который может использоваться в качестве главного ключа столбца для постоянного шифрования данных. Дополнительные сведения о главном ключе столбца и синтаксиса T-SQL для ключа шифрования столбца см. в разделе [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) и [Создание ключа ШИФРОВАНИЯ СТОЛБЦА](../../t-sql/statements/create-column-encryption-key-transact-sql.md) соответственно.

Имя SQLServerColumnEncryptionCertificateStoreProvider — MSSQL_CERTIFICATE_STORE и могут запрашиваться getName() API объекта поставщика. Он автоматически регистрируется с помощью драйвера и без проблем может быть использован без изменения приложения.

Для примеров на этой странице, если было создано хранилище сертификатов Windows на основе главного ключа столбца и ключ шифрования столбца с помощью SQL Server Management Studio, сценарий T-SQL для повторного создания их может выглядеть как показано в примере с определенные **KEY_PATH** и **ENCRYPTED_VALUE**:

```
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_CERTIFICATE_STORE',
    KEY_PATH = N'CurrentUser/My/A2A91F59C461B559E4D962DA9D2BC6131B32CB91'
)

CREATE COLUMN ENCRYPTION KEY [MyCEK]
WITH VALUES
(
    COLUMN_MASTER_KEY = [MyCMK],
    ALGORITHM = 'RSA_OAEP',
    ENCRYPTED_VALUE = 0x016E000001630075007200720065006E0074007500730065007200...
)
```

> [!IMPORTANT]
> На всех платформах, поддерживаемых драйвером доступны другие поставщики хранилища ключей в этой статье, реализация SQLServerColumnEncryptionCertificateStoreProvider драйвер JDBC также доступна в операционных системах Windows только. Он имеет зависимость от sqljdbc_auth.dll, которая доступна в пакете драйверов. Чтобы использовать этот поставщик, скопируйте файл sqljdbc_auth.dll каталог в пути системы Windows на компьютере, где установлен драйвер JDBC. Или можно задать системное свойство java.libary.path для указания каталога, в котором содержится файл sqljdbc_auth.dll. При использовании 32-разрядной виртуальной машины Java (JVM) следует использовать файл sqljdbc_auth.dll в папке x86 folder, даже если используется операционная система x64. При использовании 64-разрядной виртуальной машины и процессора x64 используйте файл sqljdbc_auth.dll в папке x64. Например если вы используете 32-разрядной виртуальной машины Java и JDBC драйвера в каталог по умолчанию, можно указать расположение библиотеки DLL с помощью следующий аргумент виртуальной машины (VM) при запуске приложения Java: `-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>С помощью поставщика хранилища ключей Java
Драйвер JDBC поставляется с реализацией поставщика встроенного хранилища ключей для хранилища ключей Java. Если **keyStoreAuthentication** свойство строки соединения в строке соединения присутствует и имеет значение «JavaKeyStorePassword», драйвер автоматически создает и регистрирует поставщик данных для хранилища ключей Java. Имя поставщика хранилища ключей Java — MSSQL_JAVA_KEYSTORE. Это имя можно также запрашивать с помощью SQLServerColumnEncryptionJavaKeyStoreProvider.getName() API. 

Существует три свойства строки соединения, которые позволяют клиентскому приложению указывать учетные данные, которые этот драйвер должен проходить проверку подлинности в хранилище ключей Java. Драйвер Инициализирует поставщика на основе значений этих трех свойств в строке подключения.

**keyStoreAuthentication:** идентифицирует хранилище ключей Java для использования. С помощью драйвера JDBC версии 6.0 и более поздних версий для SQL Server могут проходить проверку подлинности в хранилище ключей Java только через это свойство. Для хранилища ключей Java, значение этого свойства должно быть `JavaKeyStorePassword`.

**keyStoreLocation:** путь к файлу хранилища ключей Java, которое сохраняет главный ключ столбца. Путь содержит имя файла хранилища ключей.

**keyStoreSecret:** секретный код или пароль, используемый для хранилище ключей, а также как и для ключа. С помощью хранилище ключей Java, хранилище ключей и пароль ключа должно совпадать.

Ниже приведен пример указания этих учетных данных в строке подключения:

```
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

Можно также получить или задать эти параметры, с помощью объекта SQLServerDataSource. Дополнительные сведения см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

Драйвер JDBC автоматически создает экземпляр SQLServerColumnEncryptionJavaKeyStoreProvider, если эти учетные данные в свойства соединения.

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Создание главного ключа столбца для хранилища ключей Java
SQLServerColumnEncryptionJavaKeyStoreProvider может использоваться с типами хранилища ключей JKS или PKCS12. Чтобы создать или импортировать ключ, используемый с этим поставщиком используйте Java [keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) программы. Ключ должен иметь один и тот же пароль в хранилище ключей, сам. Ниже приведен пример создания открытого ключа и соответствующего закрытого ключа с помощью служебной программы keytool:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

Эта команда создает открытый ключ и переносит его в самозаверяющий сертификат, который хранится в хранилище ключей «keystore.jks», а также его закрытого ключа X.509. Эта запись в хранилище ключей определяется псевдоним «AlwaysEncryptedKey».

Ниже приведен пример использования того же типа PKCS12 хранилища:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

Если хранилище ключей типа PKCS12, программа keytool не запрашивает пароль ключа и пароль ключа должен предоставить с помощью параметра - keypass SQLServerColumnEncryptionJavaKeyStoreProvider требует, что хранилище ключей и ключ с одинаковыми пароль.

Можно также экспортировать сертификат из хранилища сертификатов Windows в формате PFX и использовать его с SQLServerColumnEncryptionJavaKeyStoreProvider. Экспортированный сертификат можно также импортировать в хранилище ключей Java как тип JKS хранилища ключей.

После создания записи keytool, создайте метаданные главного ключа столбца в базе данных требуется имя поставщика хранилища ключей и пути к ключу. Дополнительные сведения о том, как создать метаданные главного ключа столбца см. в разделе [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md). Для SQLServerColumnEncryptionJavaKeyStoreProvider пути к ключу имеет только псевдоним ключа и SQLServerColumnEncryptionJavaKeyStoreProvider называется «MSSQL_JAVA_KEYSTORE». Это имя, с помощью getName() открытого API-интерфейса класса SQLServerColumnEncryptionJavaKeyStoreProvider можно также выполнить запрос. 

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
> Встроенные SQL Server management Studio функции не удается создать определения главного ключа столбца для хранилища ключей Java. Программно необходимо использовать команды T-SQL.

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Создание ключа шифрования столбца для хранилища ключей Java
SQL Server Management Studio или любой другой инструмент не может использоваться для создания столбца ключей шифрования с помощью главных ключей столбцов в хранилище ключей Java. Клиентское приложение необходимо создавать программно с помощью класса SQLServerColumnEncryptionJavaKeyStoreProvider ключа шифрования столбца. Дополнительные сведения см. в разделе [используя поставщики хранилища главных ключей столбцов для программной подготовки ключей](#using-column-master-key-store-providers-for-programmatic-key-provisioning).

### <a name="implementing-a-custom-column-master-key-store-provider"></a>Реализация настраиваемого поставщика хранилища главных ключей столбцов
Если вы хотите сохранить главные ключи столбцов в хранилище ключей, не поддерживается существующего поставщика, можно реализовать пользовательский поставщик, расширив класс SQLServerColumnEncryptionKeyStoreProvider и зарегистрировав поставщик с помощью Метод SQLServerConnection.registerColumnEncryptionKeyStoreProviders().

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
При доступе к зашифрованным столбцам, Microsoft JDBC Driver for SQL Server прозрачно находит и вызывает поставщика хранилища главного ключа столбца справа для расшифровки ключей шифрования столбцов. Как правило, обычный код приложения не вызывает поставщики хранилища главных ключей напрямую. Тем не менее, может создать экземпляр и вызвать поставщик программными средствами для подготовки и управления ключами постоянного шифрования. Этот шаг может выполняться для формирования ключа шифрования зашифрованного столбца и расшифровки ключа шифрования столбца как часть смены главного ключа столбца, например. Дополнительные сведения см. в разделе [Overview of Key Management for Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)(Общие сведения об управлении ключами для постоянного шифрования).

При использовании поставщика пользовательского хранилища ключей, может потребоваться реализация собственных средств управления ключами. При использовании ключей, хранящихся в хранилище сертификатов Windows или в хранилище ключей Azure, можно использовать существующие средства, такие как SQL Server Management Studio или PowerShell, чтобы управлять ключами и их подготовки. При использовании ключей, хранящихся в хранилище ключей Java, необходимо подготовить ключи программными средствами. В следующем примере с помощью класса SQLServerColumnEncryptionJavaKeyStoreProvider для шифрования ключа с помощью ключа, хранящегося в хранилище ключей Java.

```
import java.sql.*;
import javax.xml.bind.DatatypeConverter;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programmatically for the Java Key Store.
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
                 * For more details on the syntax, see:
                 * https://docs.microsoft.com/sql/t-sql/statements/create-column-encryption-key-transact-sql
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
         * Following arguments needed by SQLServerColumnEncryptionJavaKeyStoreProvider
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

## <a name="enabling-always-encrypted-for-application-queries"></a>Включение постоянного шифрования для запросов приложений
Является самым простым способом включения шифрования параметров и расшифровки результатов запроса, предназначенные для зашифрованных столбцов, задав значение **columnEncryptionSetting** ключевое слово строки подключения для **включено** .

Следующая строка подключения является примером включения постоянного шифрования в драйвере JDBC:

```
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);
```

Ниже приведен эквивалент примера с помощью объекта SQLServerDataSource:

```
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("localhost");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");
SQLServerConnection con = (SQLServerConnection) ds.getConnection();
```

Постоянное шифрование также можно включить для отдельных запросов. Дополнительные сведения см. в разделе [управление влиянием на производительность постоянного шифрования](#controlling-the-performance-impact-of-always-encrypted). Включение постоянного шифрования недостаточно для шифрования или расшифровки для успешного выполнения. Необходимо также проверить выполнение следующих условий:
- Приложение имеет разрешения *VIEW ANY COLUMN MASTER KEY DEFINITION* и *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* для базы данных, необходимые для доступа к метаданным о ключах постоянного шифрования в базе данных. Дополнительные сведения см. в разделе [разрешений в постоянное шифрование (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
- Приложение может получить доступ к главный ключ столбца, который защищает ключи шифрования столбцов, которые шифрования запрашиваемые столбцы базы данных. Чтобы использовать поставщик хранилища ключей Java, необходимо указать дополнительные учетные данные в строке подключения. Дополнительные сведения см. в разделе [поставщика хранилища ключей с помощью Java](#using-java-key-store-provider).

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Настройка способа отправки значений java.sql.Time сервера
**SendTimeAsDatetime** свойство соединения позволяет настроить порядок отправки значения java.sql.Time на сервер. Если задано значение false, значения времени отправляется как тип времени SQL Server. Если задано значение true, время отправки значение типа datetime. Если столбец времени зашифрован, **sendTimeAsDatetime** свойство должно быть задано значение false, как зашифрованных столбцов не поддерживается преобразование из времени в datetime. Также Обратите внимание, что это свойство по умолчанию true, поэтому при использовании зашифрованных столбцов следует присвоить ему значение false. В противном случае драйвер вызовет исключение. Класс SQLServerConnection, начиная с драйвера версии 6.0, имеет два метода для программной настройки значение этого свойства:
 
* открытые void setSendTimeAsDatetime (логическое sendTimeAsDateTimeValue)
* public boolean getSendTimeAsDatetime()

Дополнительные сведения о данном свойстве см. в разделе [как настройка java.sql.Time отправляются на сервер](configuring-how-java-sql-time-values-are-sent-to-the-server.md).

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>Настройка способа отправки строковые значения сервера
**SendStringParametersAsUnicode** свойство соединения используется для настройки способа отправки строковых значений SQL Server. Если задано значение true, то строковые параметры отправляются на сервер в Юникоде. Если задано значение false, строковые параметры отправляются в формате Юникод, например ASCII или MBCS, а не в Юникоде. Значение по умолчанию для этого свойства равно true. Если постоянное шифрование включено и char/varchar/varchar(max) столбец зашифрован, значение **sendStringParametersAsUnicode** должно быть присвоено значение false. Если это свойство имеет значение true, драйвер вызовет исключение при расшифровке данных из зашифрованного char/varchar/varchar(max) столбца, содержащего символы Юникода. Дополнительные сведения о данном свойстве см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Извлечение и изменение данных в зашифрованных столбцах
После включения постоянного шифрования для запросов приложений можно использовать стандартные API-интерфейсы JDBC извлекать или изменять данные в столбцах зашифрованной базы данных. Если приложение имеет разрешения, необходимые базы данных и может получить доступ к главному ключу столбца, драйвер будет шифровать все параметры запроса, предназначенные для зашифрованных столбцов и расшифровывать данные, полученные из зашифрованных столбцов.

Если постоянное шифрование не включено, выполнение запросов с параметрами, предназначенными для зашифрованных столбцов, завершится ошибкой. Запросы по-прежнему могут получать данные из зашифрованных столбцов, при условии, что запрос не имеет параметров предназначенные для зашифрованных столбцов. Тем не менее драйвер не будет пытаться расшифровать все значения, полученные из зашифрованных столбцов, и приложение будет получать двоичные зашифрованные данные (в виде массивов байтов).

В следующей таблице перечислены поведение запросов в зависимости от того, является ли постоянное шифрование включено или нет:

|Характеристика запроса | Постоянное шифрование включено, и приложение может получать доступ к ключам и метаданным ключей|Постоянное шифрование включено, и приложение не может получать доступ к ключам и метаданным ключей | Постоянное шифрование отключено|
|:---|:---|:---|:---|
| Запросы с параметрами, предназначенными для зашифрованных столбцов. | Значения параметров прозрачно шифруются. | Ошибка | Ошибка|
| Запросы, получающие данные из зашифрованных столбцов без параметров, предназначенных для зашифрованных столбцов.| Результаты из зашифрованных столбцов прозрачно расшифровываются. Приложение получает значения типов данных JDBC, соответствующие типы SQL Server, настроенным для зашифрованных столбцов в открытом тексте. | Ошибка | Результаты из зашифрованных столбцов не расшифровываются. Приложение получает зашифрованные значения в виде массивов байтов (byte[]).

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Вставки и извлечения примеры зашифрованные данные 
В следующих примерах показано получение и изменение данных в зашифрованных столбцах. В этих примерах целевую таблицу со следующей схемой и зашифрованных столбцов SSN и BirthDate. Если вы настроили главный ключ столбца с именем «MyCMK» и ключа шифрования столбца с именем «MyCEK» (как описано в предыдущих разделах поставщиков хранилища ключей), можно создать таблицу с помощью этого сценария:

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

Каждый пример кода Java необходимо вставить код для конкретного хранилища ключей там указано.

При использовании поставщика хранилища ключей хранилища ключей Azure:

```
    String clientID = "<Azure Application ID>";
    String clientKey = "<Azure Application API Key Password>";
    SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
    Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
    keyStoreMap.put(akvProvider.getName(), akvProvider);
    SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
```

При использовании поставщика хранилища ключей хранилища сертификатов Windows:

```
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
```

При использовании хранилища ключей поставщика хранилища ключей Java:

```
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>Пример вставки данных
В этом примере показана вставка строки в таблицу Patients. Обратите внимание, следующие элементы:
- В образце кода нет ничего, связанного с шифрованием. Microsoft JDBC Driver for SQL Server автоматически обнаруживает и шифрует параметры, предназначенные для зашифрованных столбцов. Это делает шифрование прозрачным для приложения.
- Значениях, вставляемых в столбцы базы данных, включая зашифрованные столбцы передаются как параметры, с помощью SQLServerPreparedStatement. При использовании параметров является необязательным при отправке значений в незашифрованные столбцы (хотя, настоятельно рекомендуется, так как он помогает предотвратить внедрение кода SQL), он необходим для значений, предназначенных для зашифрованных столбцов. Если значения, вставленные в зашифрованные столбцы были переданы в качестве литералов, внедренных в инструкции запроса, запрос завершится сбоем, так как драйвер, не сможет определить значения в зашифрованных столбцах, а не сможет зашифровать значения. В результате сервер отклонит их как несовместимые с зашифрованными столбцами.
- Все значения, выводимые программой будет в виде обычного текста, как Microsoft JDBC Driver for SQL Server прозрачно расшифровывает данные, полученные из зашифрованных столбцов.
- При выполнении поиска с помощью предложения WHERE, значение, используемое в предложении WHERE должен будет передан как параметр, чтобы драйвер мог его прозрачно зашифровать перед отправкой в базу данных. В следующем примере номера социального Страхования передается в качестве параметра, но LastName передается как литерал, как LastName не шифруются.
- Метод задания свойства, используемое для параметра, предназначенных для столбца SSN — setString(), которая сопоставляется тип данных SQL Server char/varchar. Если для этого параметра используется метод задания был setNString(), который сопоставляет nchar/nvarchar, запрос завершится ошибкой, как постоянное шифрование не поддерживает преобразования из зашифрованных значений nchar и nvarchar в зашифрованные char/varchar значения.

```
try
{
    <Insert keystore-specific code here>

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

### <a name="retrieving-plaintext-data-example"></a>Обычный текст пример извлечения данных
В следующем примере показана фильтрация данных, на основе зашифрованных значений и получение данных открытого текста из зашифрованных столбцов. Обратите внимание, следующие элементы:
- Значение, используемое в предложении WHERE для фильтрации по столбцу SSN должен будет передан как параметр, чтобы Microsoft JDBC Driver for SQL Server мог его прозрачно зашифровать перед отправкой в базу данных.
- Все значения, выводимые программой будет в виде обычного текста, как Microsoft JDBC Driver for SQL Server прозрачно расшифровывает данные, полученные из столбцов SSN и BirthDate.

> [!NOTE]
> Если столбцы зашифрованы с помощью детерминированного шифрования, запросы можно выполнять сравнение на равенство их. Дополнительные сведения см. в разделе [Выбор детерминированного или случайного шифрования в постоянное шифрование (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```
try
{
    <Insert keystore-specific code here>

    Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
    try (Connection sourceConnection = DriverManager.getConnection(connectionString))
    {
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
    }
}
catch (Exception e)  
{  
    e.printStackTrace();  
}
```
  
### <a name="retrieving-encrypted-data-example"></a>Пример получения зашифрованных данных
Если постоянное шифрование не включено, запрос может получать данные из зашифрованных столбцов, пока для него не будут указаны параметры, предназначенные для зашифрованных столбцов.

В следующем примере показано извлечение двоичных зашифрованных данных из зашифрованных столбцов. Обратите внимание, следующие элементы:
- Так как постоянное шифрование не включено в строке подключения, запрос будет возвращать зашифрованные значения SSN и BirthDate в виде байтовых массивов (программа преобразует значения в строки).
- Запрос, получающий данные из зашифрованных столбцов с отключенным постоянным шифрованием, может иметь параметры при условии, что ни один из параметров не предназначен для зашифрованного столбца. Следующий запрос выполняет фильтрацию по LastName, который не зашифрован в базе данных. Запрос, отфильтрованный по SSN или BirthDate, завершится ошибкой.

```
try
{
    String connectionString  = "jdbc:sqlserver://localhost:1433;" + "databaseName=Clinic;user=sa;password=******";

    Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");
    try (Connection sourceConnection = DriverManager.getConnection(connectionString))
    {
        String filterRecord="SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;";

        try (PreparedStatement selectStatement = sourceConnection.prepareStatement(filterRecord))
        {
            selectStatement.setString(1, "Abel");
            ResultSet rs = selectStatement.executeQuery();
            while (rs.next())
            {
                System.out.println("SSN: " + rs.getString("SSN") +
                    ", FirstName: " + rs.getString("FirstName") +
                    ", LastName:"+ rs.getString("LastName") +
                    ", Date of Birth: " + rs.getString("BirthDate"));
            }
        }
    }
}
catch (Exception e)
{
    e.printStackTrace();
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Как избежать распространенных проблем при запросе зашифрованных столбцов
В этом разделе описываются общие категории ошибок, при запросе зашифрованных столбцов из приложений Java и приводятся рекомендации о том, как их избежать.

### <a name="unsupported-data-type-conversion-errors"></a>Ошибки преобразования неподдерживаемых типов данных
Постоянное шифрование поддерживает несколько преобразований для зашифрованных типов данных. В разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) подробный список поддерживаемых преобразований типов. Вот, что делать, чтобы избежать ошибки преобразования типов данных. Убедитесь, что:

- При передаче значения для параметров, предназначенных для зашифрованных столбцов, используйте методы соответствующие задания. Убедитесь, что тип данных SQL Server параметра точно совпадает с типом целевого столбца или поддерживается преобразование типа данных SQL Server параметра в целевой тип столбца. Были добавлены методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement, SQLServerResultSet, для передачи параметров, соответствующих определенных типов данных SQL Server. Например, если столбец не зашифрован метод setTimestamp() для передачи параметра, datetime2 или к столбцу типа datetime. Но когда столбец зашифрован необходимо использовать конкретный метод, представляющий тип столбца в базе данных. Например можно используйте setTimestamp() передавать значения в столбце зашифрованные datetime2 и использовать setDateTime() для передачи значений в столбец зашифрованные datetime. В разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) полный список новых интерфейсов API.
- Точность и масштаб параметров, предназначенных для столбцов типов данных SQL Server decimal и numeric, соответствуют точности и масштабу, настроенным для целевого столбца. Были добавлены методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement, SQLServerResultSet принять точность и масштаб, а также значения данных для параметров и столбцами, представляющими десятичных и числовых типов данных. В разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) полный список новых и перегруженные API-интерфейсов.  
- доли секунды точность или шкала параметров, предназначенных для столбцов datetime2, datetimeoffset или времени типов данных SQL Server не превышает точность долей секунды или шкала для целевого столбца в запросах, которые изменяют значения целевого столбца . Были добавлены методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement, SQLServerResultSet принять долей секунды точность или шкала вместе со значениями данных для представления этих типов данных параметров. Полный список новых и перегруженные API-интерфейсов, в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).   

### <a name="errors-due-to-incorrect-connection-properties"></a>Ошибки из-за свойства подключения
В этом разделе описывается настройка параметров подключения соответствующим образом, чтобы использовать постоянное шифрование данных. Поскольку зашифрованных типов данных поддерживается только преобразование **sendTimeAsDatetime** и **sendStringParametersAsUnicode** параметры подключения требуется правильная настройка при использовании зашифрованных столбцов. Убедитесь, что: 
- [sendTimeAsDatetime](setting-the-connection-properties.md) подключение установлено значение false при вставке данных в зашифрованные столбцы времени. Дополнительные сведения см. в разделе [Настройка способа отправки значений java.sql.Time сервера](configuring-how-java-sql-time-values-are-sent-to-the-server.md).
- [sendStringParametersAsUnicode](setting-the-connection-properties.md) подключение установлено значение true (или остается по умолчанию) при вставке данных в зашифрованные столбцы char/varchar/varchar(max).

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Ошибки, возникающие из-за передачи значений в виде открытого текста, а не в зашифрованном виде
Любое значение, предназначенное для зашифрованного столбца, должно быть зашифровано внутри приложения. Попытка вставки, изменения или фильтрации по значение открытого текста в зашифрованном столбце приведет к ошибке, следующим образом:

```
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Чтобы избежать таких ошибок, убедитесь, что:
- Постоянное шифрование включено для запросов приложений, предназначенных для зашифрованных столбцов (для строки подключения или для конкретного запроса).
- с помощью подготовленных инструкций и параметры для отправки данных, предназначенных для зашифрованных столбцов. В следующем примере показано, неправильно фильтрует по литералу или константе в зашифрованном столбце (SSN), вместо передачи литерала внутри как параметр запроса. Этот запрос завершится с ошибкой:

```
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>Принудительное шифрование на входные параметры
Функция принудительное шифрование принудительно шифрует параметр при использовании постоянного шифрования. Если используется принудительное шифрование и SQL Server сообщает драйверу, что параметр не должен быть зашифрован, запрос, использующий параметр завершится ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих предоставление клиенту скомпрометированным SQL Server неверных метаданных шифрования, что может привести к раскрытию данных. Набор * методы классов SQLServerPreparedStatement и SQLServerCallableStatement и обновление\* реализованы перегруженные методы в классе SQLServerResultSet принимает логический аргумент, чтобы указать параметр force шифрования. Если значение этого аргумента равно false, драйвер не будет устанавливать параметры шифрования. Если принудительное шифрование задано значение true, то запрос параметра отправляется только если целевой столбец зашифрован и постоянное шифрование включено при соединении или в отчете. С помощью этого свойства обеспечивает дополнительный уровень безопасности, гарантируя, что драйвер не отправляет ошибочно данных в SQL Server как обычный текст, когда он должен быть зашифрован.

Дополнительные сведения о перегруженные методы SQLServerPreparedStatement и SQLServerCallableStatement с помощью параметра force шифрования см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Управление влиянием на производительность постоянного шифрования
Так как постоянное шифрование — это технология шифрования на стороне клиента, большую нагрузку на производительность отражается на стороне клиента, а не в базе данных. Помимо затрат на операции шифрования и дешифрования являются другие источники снижения производительности на стороне клиента:
- Дополнительные обращения к базе данных для получения метаданных для параметров запроса.
- Вызовы хранилища главных ключей столбцов для доступа к главному ключу столбца.

В этом разделе описывается оптимизация производительности, встроенные в драйвере Microsoft JDBC для SQL Server и как можно контролировать влияние двух указанных выше факторов на производительность.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Управление обращениями для получения метаданных для параметров запроса
Если для соединения включено постоянное шифрование, по умолчанию драйвер будет вызывать [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) для каждого параметризованного запроса, передавая инструкцию запроса (без значений параметров) для SQL Server. [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) анализирует инструкцию запроса, чтобы узнать, если любой из параметров должен быть зашифрован и если да, для каждого оно возвращает связанные с шифрованием сведения, позволяющие драйверу шифровать значения параметров. Это поведение обеспечивает высокий уровень прозрачности для клиентского приложения. При условии, что приложение использует параметры для передачи значений, предназначенных для зашифрованных столбцов в драйвере, приложение (и разработчику приложений) не требуется знать, какие запросы получают доступ к зашифрованным столбцам.

### <a name="setting-always-encrypted-at-the-query-level"></a>Задание постоянного шифрования на уровне запроса
Чтобы контролировать влияние на производительность процесса получения метаданных шифрования для параметризованных запросов, можно включить постоянное шифрование для отдельных запросов, а не настраивать его для подключения. Таким образом, убедитесь, что sys.sp_describe_parameter_encryption вызывается только для запросов, которые точно имеют параметры, предназначенные для зашифрованных столбцов. Обратите внимание, что в результате снижается прозрачность шифрования: при изменении свойств шифрования столбцов базы данных, может потребоваться изменить код вашего приложения в соответствии с изменениями схемы.

Для управления поведением постоянного шифрования для отдельных запросов, необходимо настроить объектов отдельные инструкции, передавая Enum SQLServerStatementColumnEncryptionSetting, который указывает отправлено и получено при чтении и записи данных зашифрованные столбцы для этой инструкцией. Ниже приведены некоторые полезные рекомендации.
- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, доступ к зашифрованным столбцам, используйте следующие рекомендации:
    - Задать **columnEncryptionSetting** ключевое слово строки подключения для **включено**.
    - Задайте SQLServerStatementColumnEncryptionSetting.Disabled для отдельных запросов, которые не обращаются к зашифрованным столбцам. Этот параметр отключает возможность вызова sys.sp_describe_parameter_encryption как, так и попытке расшифровки всех значений в результирующем наборе.
    - Задайте SQLServerStatementColumnEncryptionSetting.ResultSet для отдельных запросов, которые не имеют параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Этот параметр отключает возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.
- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных не получить доступ к зашифрованным столбцам, используйте следующие рекомендации:
    - Задать **columnEncryptionSetting** ключевое слово строки подключения для **отключено**.
    - Задайте SQLServerStatementColumnEncryptionSetting.Enabled для отдельных запросов, имеющих параметры, которые требуется зашифровать. Этот параметр будет включена возможность вызова sys.sp_describe_parameter_encryption как, так и расшифровки результатов запроса, полученные из зашифрованных столбцов.
    - Задайте SQLServerStatementColumnEncryptionSetting.ResultSet для запросов, которые не имеют параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Этот параметр отключает возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.

Параметры SQLServerStatementColumnEncryptionSetting не может использоваться для обхода шифрования и получения доступа к данным в виде обычного текста. Дополнительные сведения о том, как настройка шифрования столбцов в инструкции см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

В следующем примере постоянное шифрование отключено для подключения к базе данных. Запрос проблемы приложений содержит параметр, предназначенный для незашифрованного столбца LastName. Запрос получает данные из зашифрованных столбцов SSN и BirthDate. В этом случае вызывать sys.sp_describe_parameter_encryption для получения метаданных шифрования не требуется. Тем не менее расшифровки результатов запроса необходимо включить, чтобы приложение могло получать значения открытого текста из двух зашифрованных столбцов. Чтобы убедиться, что используется параметр SQLServerStatementColumnEncryptionSetting.ResultSet.

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
Чтобы уменьшить количество вызовов к хранилищу главных ключей столбцов для расшифровки ключей шифрования столбцов, Microsoft JDBC Driver for SQL Server кэширует ключи шифрования столбцов открытым текстом в памяти. После получения значения ключа шифрования столбца из метаданных базы данных, драйвер сначала пытается найти ключ шифрования столбца обычный текст, соответствующий зашифрованному значению ключа. Драйвер вызывает хранилище ключей, содержащему главный ключ столбца, только в том случае, если не удается найти значение ключа шифрования зашифрованного столбца в кэше.

Значение срока жизни для записи ключей шифрования столбцов можно настроить в кэш, используя API setColumnEncryptionKeyCacheTtl(), в классе SQLServerConnection. Значение по умолчанию срок жизни для записи ключей шифрования столбцов в кэше: 2 часа. Чтобы отключить кэширование, используйте значение 0. Чтобы задать любое значение срока жизни, используйте следующий API:

```
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

Например чтобы задать значение срока жизни 10 минут, используйте следующую команду:

```
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

Только дней, часов, МИНУТ или СЕКУНД поддерживаются в качестве единицы измерения времени.  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Копирование зашифрованных данных с помощью SQLServerBulkCopy
С SQLServerBulkCopy можно скопировать данные, которые уже зашифрованы и хранятся в одной таблице на другую таблицу без расшифровки данных. Для этого выполните указанные далее действия.

- Убедитесь, что конфигурация шифрования целевой таблицы идентична конфигурации исходной таблицы. В частности обе таблицы должны иметь одинаковые зашифрованные столбцы и столбцы должны быть зашифрованы с помощью те же типы шифрования и ключей шифрования. Любой целевой столбец зашифрован иначе, чем соответствующего столбца источника, вы не сможете расшифровать данные в целевой таблице после операции копирования. Данные будут повреждены.
- Настройте подключения базы данных в исходной таблице и на целевую таблицу без включения постоянного шифрования.
- Задайте параметр allowEncryptedValueModifications. Дополнительные сведения см. в разделе [с помощью массового копирования с драйвером JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

> [!NOTE]
> Будьте внимательны при указании AllowEncryptedValueModifications, как этот параметр может привести к повреждению базы данных, так как Microsoft JDBC Driver for SQL Server не проверяет, если данные шифруются на самом деле или правильность их шифрования с помощью того же шифрования тип, алгоритм и ключ как целевого столбца.

## <a name="see-also"></a>См. также
[Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
