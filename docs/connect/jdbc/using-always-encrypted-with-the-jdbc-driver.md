---
title: С помощью постоянного шифрования с драйвером JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 3/14/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
caps.latest.revision: 64
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c53479e3e94206645382e0c7b2d930a0b63075f
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/11/2018
ms.locfileid: "37982268"
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Использование функции Always Encrypted с драйвером JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Эта страница содержит сведения о том, как разрабатывать приложения Java с использованием [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.

Функция Always Encrypted позволяет шифровать конфиденциальные данные в клиентах, не раскрывая данные или ключи шифрования для SQL Server или базы данных SQL Azure. Драйвер с поддержкой Always Encrypted, такой как Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server, реализует это за счет прозрачного шифрования и расшифровки конфиденциальных данных в клиентском приложении. Драйвер автоматически определяет, какой запрос параметров соответствуют столбцам базы данных Always Encrypted и шифрует значения этих параметров перед их отправкой в SQL Server или базы данных SQL Azure. Аналогичным образом драйвер прозрачно расшифровывает данные, полученные из зашифрованных столбцов базы в результатах запроса. Дополнительные сведения см. в разделе [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

## <a name="prerequisites"></a>предварительные требования
- Убедитесь, что Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server должен быть установлен на компьютере разработки. 
- Скачайте и установите файлы политики юрисдикции неограниченной стойкости Java Cryptography Extension (JCE).  Обязательно прочитайте содержащийся в ZIP-архиве файл сведений, чтобы получить инструкции по установке и сопутствующие сведения о возможных проблемах экспорта и импорта.  

    - При использовании mssql-jdbc-X.X.X.jre7.jar или sqljdbc41.jar файлы политики можно скачать на странице [скачивания файлов политики юрисдикции неограниченной стойкости Java Cryptography Extension (JCE) 7](http://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html).

    - При использовании mssql-jdbc-X.X.X.jre8.jar или sqljdbc42.jar файлы политики можно скачать на странице [скачивания файлов политики юрисдикции неограниченной стойкости Java Cryptography Extension (JCE) 8](http://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html).

    - Если с помощью mssql-jdbc-X.X.X.jre9.jar, нет файл политики необходимо загрузить. Политики юрисдикции в Java 9 неограниченное стойкость шифрования по умолчанию.

## <a name="working-with-column-master-key-stores"></a>Работа с хранилищами главных ключей столбцов
Для шифрования или расшифровки данных для зашифрованных столбцов, SQL Server поддерживает ключи шифрования столбцов. Ключи шифрования столбцов хранятся в зашифрованном виде в метаданных базы данных. Каждый ключ шифрования столбца имеет соответствующий главный ключ столбца, который используется для шифрования ключа шифрования столбца. Метаданные базы данных не содержит главные ключи столбцов. Эти ключи хранятся только с помощью клиента. Тем не менее метаданных базы данных содержат сведения о том, где хранятся главные ключи столбцов относительно клиента. Например метаданных базы данных может сказать, что хранилище ключей, удерживая главный ключ столбца является Store сертификатов Windows и конкретного сертификата, используемого для шифрования и расшифровки расположен в указанную папку в Store сертификатов Windows. Если клиент имеет доступ к этому сертификату в Store сертификатов Windows, его можно получить сертификат. Сертификат можно затем использовать для расшифровки ключа шифрования столбца. Вы можете использовать этот ключ шифрования для расшифровки или шифрования данных для зашифрованных столбцов, использующих этот ключ шифрования столбца.

Microsoft JDBC Driver для SQL Server взаимодействует с помощью хранилища ключей с помощью поставщика хранилища главного ключа столбца, который является экземпляром класса, производным от **SQLServerColumnEncryptionKeyStoreProvider**.

### <a name="using-built-in-column-master-key-store-providers"></a>Использование встроенных поставщиков хранилища главных ключей столбцов
Microsoft JDBC Driver для SQL Server в состав следующих поставщиков хранилища главных ключей встроенный столбец. Некоторые из этих поставщиков предварительно зарегистрированы с конкретными именами поставщиков (используется для поиска поставщика), а некоторые требуют дополнительные учетные данные или явной регистрации.

| Class | Описание | Имя поставщика |Предварительно зарегистрировать?|
|:---|:---|:---|:---|
|**SQLServerColumnEncryptionAzureKeyVaultProvider**| Поставщик хранилища ключей для хранилища ключей Azure.| AZURE_KEY_VAULT|нет|
|**SQLServerColumnEncryptionCertificateStoreProvider**| Поставщик для хранилища сертификатов Windows.|MSSQL_CERTIFICATE_STORE|Да
|**SQLServerColumnEncryptionJavaKeyStoreProvider**| Поставщик для хранилище ключей Java|MSSQL_JAVA_KEYSTORE|Да|

Для поставщиков хранилища ключей предварительно зарегистрированы не требуется вносить изменения кода приложения для использования этих поставщиков, но иметь в виду следующее:

- Вы (или ваш администратор баз данных) должны проверить правильность имени поставщика, настроенного в метаданных главного ключа столбца, и убедиться в том, что путь к главному ключу столбца соответствует формату пути к ключу, который является допустимым для данного поставщика. Для настройки ключей рекомендуется использовать средство, такое как среда SQL Server Management Studio, которое при выполнении инструкции CREATE COLUMN MASTER KEY (Transact-SQL) автоматически создает допустимые имена поставщиков и пути к ключам.
- Убедитесь, что приложение может получить доступ к ключ в хранилище ключей. Для этого может потребоваться предоставить приложению доступ к ключу или хранилищу ключей (в зависимости от хранилища ключей) либо выполнить другие действия по настройке конкретного хранилища ключей. Например при помощи SQLServerColumnEncryptionJavaKeyStoreProvider необходимо указать расположение и пароль хранилища ключей в свойствах соединения. 

Все эти поставщики хранилища ключей описаны более подробно в последующих разделах. Необходимо реализовать один поставщик хранилища ключей для использования постоянного шифрования.

### <a name="using-azure-key-vault-provider"></a>Использование поставщика хранилища ключей Azure
Хранилище Azure Key Vault удобно для хранения главных ключей столбцов для Always Encrypted и управления ими, особенно в том случае, если приложение размещено в Azure. Microsoft JDBC Driver для SQL Server включает в себя встроенного поставщика, SQLServerColumnEncryptionAzureKeyVaultProvider, для приложений, имеющих ключи, хранящиеся в хранилище ключей Azure. Этот поставщик называется AZURE_KEY_VAULT. Чтобы использовать поставщик хранилища Azure Key Vault, разработчик приложения должен создавать хранилища и ключи в хранилище ключей Azure и создать регистрацию приложения в Azure Active Directory. Зарегистрированное приложение должно быть предоставлено получить, Decrypt, Encrypt, распаковку ключа, Wrap Key и проверьте разрешения в политике доступа, определенных для хранилища ключей, созданных для использования с Always Encrypted. Дополнительные сведения о том, как настроить хранилище ключей и создайте главный ключ столбца, см. в разделе [Azure Key Vault — шаг за шагом](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) и [Создание главных ключей столбцов в хранилище ключей Azure](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault).

Для примеров на этой странице, если вы создали хранилище ключей Azure на основе главного ключа столбца и ключа шифрования столбца с помощью SQL Server Management Studio, сценарий T-SQL для повторного создания их может выглядеть как в этом примере с определенные **KEY_ ПУТЬ** и **ENCRYPTED_VALUE**:

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

Чтобы использовать хранилище ключей Azure, клиентских приложений необходимо создать экземпляр SQLServerColumnEncryptionAzureKeyVaultProvider и зарегистрируйте его с помощью драйвера.

Вот пример инициализации SQLServerColumnEncryptionAzureKeyVaultProvider:  

```
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**clientID** идентификатор приложения регистрацию приложения в экземпляре Azure Active Directory. **clientKey** пароль ключа использованной при регистрации приложения, которая предоставляет доступ к API в хранилище ключей Azure.

После того как приложение создаст экземпляр SQLServerColumnEncryptionAzureKeyVaultProvider, приложение необходимо зарегистрировать экземпляр с помощью драйвера, с помощью метода SQLServerConnection.registerColumnEncryptionKeyStoreProviders(). Настоятельно рекомендуется, что экземпляр зарегистрирован с именем Уточняющий запрос по умолчанию, AZURE_KEY_VAULT, который можно получить, вызвав SQLServerColumnEncryptionAzureKeyVaultProvider.getName() API. С именем по умолчанию позволит вам использовать средства, такие как SQL Server Management Studio или PowerShell для подготовки и управления ключами, Always Encrypted (средства используйте имя по умолчанию для создания объекта метаданных для главного ключа столбца). В следующем примере показано, регистрация поставщика хранилища ключей Azure. Дополнительные сведения о методе SQLServerConnection.registerColumnEncryptionKeyStoreProviders(), см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

```
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Если вы используете поставщик хранилища ключей Azure Key Vault, в Azure Key Vault метода драйвер JDBC имеет зависимости от этих библиотек (из GitHub), которые должен быть включен в ваше приложение:
>
>  [Azure sdk для java](https://github.com/Azure/azure-sdk-for-java)
>
>  [библиотеки Azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> Пример того, как включить эти зависимости в проект Maven, см. в разделе [загрузить ADAL4J и AKV зависимости с помощью Apache Maven](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven)

### <a name="using-windows-certificate-store-provider"></a>С помощью Windows Certificate Store поставщика
The SQLServerColumnEncryptionCertificateStoreProvider можно использовать для хранения главных ключей столбцов в хранилище сертификатов Windows. Используйте мастер постоянного шифрования SQL Server Management Studio (SSMS) или других поддерживаемых средств для создания главного ключа столбца и шифрование столбцов определений для ключей в базе данных. Тот же мастер можно использовать для создания самозаверяющего сертификата в Store сертификатов Windows, который может использоваться в качестве главного ключа столбца для постоянного шифрования данных. Дополнительные сведения о главном ключе столбца и синтаксиса T-SQL для ключа шифрования столбца, см. в разделе [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md) и [Создание ключа ШИФРОВАНИЯ СТОЛБЦА](../../t-sql/statements/create-column-encryption-key-transact-sql.md) соответственно.

Имя SQLServerColumnEncryptionCertificateStoreProvider является MSSQL_CERTIFICATE_STORE и может запрашиваться getName() API объекта поставщика. Он автоматически регистрируется с помощью драйвера и может использоваться в легко без изменения приложения.

Для примеров на этой странице, если вы создали сертификат Windows Store на основе главного ключа столбца и ключа шифрования столбца с помощью SQL Server Management Studio, сценарий T-SQL для повторного создания их может выглядеть как в этом примере с определенные **KEY_PATH** и **ENCRYPTED_VALUE**:

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
> На всех платформах, поддерживаемых драйвером доступны другие поставщики хранилища ключей, в этой статье, реализация SQLServerColumnEncryptionCertificateStoreProvider драйвера JDBC доступна Windows только в операционных системах. Он имеет зависимость от sqljdbc_auth.dll, которая доступна в пакете драйверов. Чтобы использовать этот поставщик, скопируйте файл sqljdbc_auth.dll в системный каталог Windows на компьютере, на котором установлен драйвер JDBC. Или можно задать системное свойство java.libary.path для указания каталога, в котором содержится файл sqljdbc_auth.dll. При использовании 32-разрядной виртуальной машины Java (JVM) следует использовать файл sqljdbc_auth.dll в папке x86 folder, даже если используется операционная система x64. При использовании 64-разрядной виртуальной машины и процессора x64 используйте файл sqljdbc_auth.dll в папке x64. Например, если используется 32-разрядная виртуальная машина Java и драйвер JDBC установлен в каталоге по умолчанию, можно указать местоположение файла DLL, использовав следующий аргумент виртуальной машины при запуске приложения Java: `-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>С помощью поставщика Key Store Java
Драйвер JDBC поставляется со встроенной реализацией поставщика хранилища ключей для хранилища ключей Java. Если **keyStoreAuthentication** свойство строки соединения в строке подключения и он становится равным «JavaKeyStorePassword», драйвер автоматически создает и регистрирует поставщик для Java Key Store. Имя поставщика ключа Store Java — MSSQL_JAVA_KEYSTORE. Это имя также можно запросить с помощью SQLServerColumnEncryptionJavaKeyStoreProvider.getName() API. 

Существует три свойства строки подключения, которые позволяют клиентскому приложению указать учетные данные, которые этот драйвер должен проходить проверку подлинности в Store ключ Java. Драйвер Инициализирует поставщика на основе значений из этих трех свойств в строке подключения.

**keyStoreAuthentication:** идентифицирует Store ключ Java для использования. С Microsoft JDBC Driver 6.0 и более поздней версии для SQL Server могут проходить Store ключ Java только через это свойство. Для Store ключ Java, значение этого свойства должно быть `JavaKeyStorePassword`.

**keyStoreLocation:** путь к файлу ключа Store Java, который сохраняет главный ключ столбца. Путь содержит имя файла хранилища ключей.

**keyStoreSecret:** секретный код или пароль, используемый для хранилище ключей, а также как и для ключа. Для использования Store ключ Java, хранилище ключей, а пароль ключа должны совпадать.

Ниже приведен пример предоставления эти учетные данные в строке подключения:

```
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

Кроме того, можно также получить или задать эти параметры, с помощью объекта SQLServerDataSource. Дополнительные сведения см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

Драйвер JDBC автоматически создает экземпляр SQLServerColumnEncryptionJavaKeyStoreProvider, если эти учетные данные в свойства соединения.

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Создание главного ключа столбца для Store ключ Java
SQLServerColumnEncryptionJavaKeyStoreProvider может использоваться с типами хранилища ключей JKS или PKCS12. Чтобы создать или импортировать ключ, используемый с этим поставщиком используйте Java [keytool](http://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) служебной программы. Ключ должен иметь тот же пароль, что хранилище ключей, сам. Вот пример того, как создать открытый ключ и связанный с ним закрытый ключ с помощью служебной программы keytool:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

Эта команда создает открытый ключ и переносит его в самозаверяющий сертификат, который хранится в хранилище ключей «keystore.jks», а также его закрытого ключа X.509. Эта запись в хранилище ключей определяется псевдоним «AlwaysEncryptedKey».

Ниже приведен пример использования тем же типом хранилища PKCS12:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

Если хранилище ключей типа PKCS12, программа keytool не запрашивает пароль ключа и должен предоставить с параметром - keypass SQLServerColumnEncryptionJavaKeyStoreProvider требуется, то хранилище ключей и ключ имеют одинаковый пароль ключа пароль.

Можно также экспортировать сертификат из хранилища сертификатов Windows в формате PFX и использовать его с SQLServerColumnEncryptionJavaKeyStoreProvider. Экспортированный сертификат можно также импортировать Store ключ Java как тип хранилища ключей JKS.

После создания записи keytool, создайте метаданные главного ключа столбца в базе данных, которую требуется имя поставщика хранилища ключей и путь к ключу. Дополнительные сведения о том, как создать метаданные главного ключа столбца, см. в разделе [CREATE COLUMN MASTER KEY](../../t-sql/statements/create-column-master-key-transact-sql.md). Для SQLServerColumnEncryptionJavaKeyStoreProvider путь к ключу, — это просто псевдоним ключа и SQLServerColumnEncryptionJavaKeyStoreProvider называется «MSSQL_JAVA_KEYSTORE». Можно также запросить это имя, с помощью общедоступного API getName() SQLServerColumnEncryptionJavaKeyStoreProvider класса. 

Используется следующий синтаксис T-SQL для создания главного ключа столбца:

```
CREATE COLUMN MASTER KEY [<CMK_name>]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'<key_alias>'
)
```

Для «AlwaysEncryptedKey» созданную выше будет определения главного ключа столбца:

```
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```

> [!NOTE]
> Встроенные SQL Server management Studio функции не удается создать определения главного ключа столбца для Store ключ Java. Команды T-SQL необходимо использовать программным способом.

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Создание ключа шифрования столбца для Store ключ Java
В SQL Server Management Studio или любой другой инструмент не может использоваться для создания столбца ключей шифрования с помощью главных ключей столбцов в Store ключ Java. Клиентское приложение необходимо создать программно с помощью класса SQLServerColumnEncryptionJavaKeyStoreProvider ключа шифрования столбца. Дополнительные сведения см. в разделе [с помощью поставщиков хранилища главных ключей столбцов для программной подготовки ключей](#using-column-master-key-store-providers-for-programmatic-key-provisioning).

### <a name="implementing-a-custom-column-master-key-store-provider"></a>Реализация настраиваемого поставщика хранилища главных ключей столбцов
Чтобы сохранить главные ключи столбцов в хранилище ключей, не поддерживаемом существующим поставщиком, можно реализовать настраиваемый поставщик, расширив класс SQLServerColumnEncryptionKeyStoreProvider и зарегистрировав поставщик с помощью метода SQLServerConnection.registerColumnEncryptionKeyStoreProviders().

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
При доступе к зашифрованным столбцам драйвер Microsoft JDBC Driver для SQL Server прозрачно находит и вызывает нужный поставщик хранилища главных ключей столбцов, чтобы расшифровать ключи шифрования столбцов. Как правило, обычный код приложения не вызывает поставщики хранилища главных ключей напрямую. Тем не менее, может создать экземпляр и вызвать поставщик программным способом для подготовки и управления ключами постоянного шифрования. Это действие может выполнить для создания ключа шифрования зашифрованного столбца и расшифровки ключа шифрования столбца как смены главного ключа столбца части, например. Дополнительные сведения см. в разделе [Overview of Key Management for Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)(Общие сведения об управлении ключами для постоянного шифрования).

Если используется настраиваемый поставщик хранилища ключей, может потребоваться реализация собственных средств управления ключами. При использовании ключей, хранящихся в Windows Store сертификата или в хранилище ключей Azure, можно использовать существующие средства, такие как SQL Server Management Studio или PowerShell, чтобы управлять ключами и их подготовки. При использовании ключей, хранящихся в Store ключ Java, можно использовать для подготовки ключей программным способом. В следующем примере с помощью класса SQLServerColumnEncryptionJavaKeyStoreProvider для шифрования ключа с ключом, хранящимся в Store ключ Java.

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
Самым простым способом включения шифрования параметров и расшифровки результатов запросов к зашифрованным столбцам является установка для ключевого слова строки подключения **columnEncryptionSetting** значения **Enabled**.

Следующая строка подключения является примером включения постоянного шифрования в драйвере JDBC:

```
String connectionString = "jdbc:sqlserver://localhost;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionString);
```

Ниже приведен эквивалентный пример, с помощью объекта SQLServerDataSource.

```
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("localhost");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");
SQLServerConnection con = (SQLServerConnection) ds.getConnection();
```

Постоянное шифрование также можно включить для отдельных запросов. Дополнительные сведения см. в разделе [управление влиянием на производительность функции постоянного шифрования](#controlling-the-performance-impact-of-always-encrypted). Включение функции Always Encrypted недостаточно для успешного шифрования или расшифровки. Необходимо также проверить выполнение следующих условий:
- Приложение имеет разрешения *VIEW ANY COLUMN MASTER KEY DEFINITION* и *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* для базы данных, необходимые для доступа к метаданным о ключах постоянного шифрования в базе данных. Дополнительные сведения см. в разделе [Разрешения в Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
- Приложение может получить доступ к главному ключу столбца, который защищает ключи шифрования столбцов, шифрующие запрашиваемые столбцы базы данных. Чтобы воспользоваться поставщиком Store ключ Java, необходимо указать дополнительные учетные данные в строке подключения. Дополнительные сведения см. в разделе [Using Java Key Store provider](#using-java-key-store-provider).

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Настройка способа отправки значений java.sql.Time на сервер
**SendTimeAsDatetime** свойство подключения позволяет настроить порядок отправки значения java.sql.Time на сервер. Если задано значение false, значения времени отправляется как тип времени SQL Server. Если задано значение true, время отправки значение как тип даты и времени. Если в них столбец времени зашифрован, **sendTimeAsDatetime** свойство должно быть задано значение false, так как зашифрованные столбцы не поддерживают преобразование из времени в дату и время. Также Обратите внимание, что это свойство по умолчанию true, поэтому при использовании зашифрованных столбцов необходимо присвоить ему значение false. В противном случае драйвер вызовет исключение. Класс SQLServerConnection, начиная с версии 6.0 драйвера, используются два метода для программной настройки значение этого свойства.
 
* открытый void setSendTimeAsDatetime (логическое sendTimeAsDateTimeValue)
* public boolean getSendTimeAsDatetime()

Дополнительные сведения об этом свойстве см. в разделе [java.sql.Time настройке как значения отправляются на сервер](configuring-how-java-sql-time-values-are-sent-to-the-server.md).

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>Настройка способа отправки на сервер строковых значений
**SendStringParametersAsUnicode** свойство соединения используется для настройки способа отправки строковых значений SQL Server. Если задано значение true, строковые параметры отправляются на сервер в Юникоде. Если набор значение равно false, то строковые параметры отправляются в формате Юникод, например ASCII или MBCS, а не в Юникоде. Значение этого свойства по умолчанию — true. Если постоянное шифрование включено и char/varchar/varchar(max) столбец зашифрован, значение **sendStringParametersAsUnicode** должно быть присвоено значение false. Если это свойство имеет значение true, драйвер вызовет исключение при расшифровке данных из зашифрованного char/varchar/varchar(max) столбца, содержащего символы Юникода. Дополнительные сведения об этом свойстве см. в разделе [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Получение и изменение данных в зашифрованных столбцах
После включения постоянного шифрования для запросов приложений, можно использовать стандартные API JDBC для извлечения или изменения данных в зашифрованных столбцах базы данных. Если приложение имеет разрешения нужную базу данных и может получить доступ к главному ключу столбца, драйвер будет шифровать все параметры запроса, предназначенные для зашифрованных столбцов и расшифровывать данные, полученные из зашифрованных столбцов.

Если постоянное шифрование не включено, выполнение запросов с параметрами, предназначенными для зашифрованных столбцов, завершится ошибкой. Запросы по-прежнему могут получать данные из зашифрованных столбцов, пока для них не будут указаны параметры, предназначенные для зашифрованных столбцов. Однако драйвер не будет пытаться расшифровать все значения, полученные из зашифрованных столбцов, и приложение будет получать двоичные зашифрованные данные (в виде массивов байтов).

В приведенной ниже таблице описывается поведение запросов в зависимости от того, включена ли функция Always Encrypted.

|Характеристика запроса | Постоянное шифрование включено, и приложение может получать доступ к ключам и метаданным ключей|Постоянное шифрование включено, и приложение не может получать доступ к ключам и метаданным ключей | Постоянное шифрование отключено|
|:---|:---|:---|:---|
| Запросы с параметрами, предназначенными для зашифрованных столбцов. | Значения параметров прозрачно шифруются. | Ошибка | Ошибка|
| Запросы, получающие данные из зашифрованных столбцов, без параметров, предназначенных для зашифрованных столбцов.| Результаты из зашифрованных столбцов прозрачно расшифровываются. Приложение получает в виде открытого текста значения типов данных JDBC, которые соответствуют типам SQL Server, настроенным для зашифрованных столбцов. | Ошибка | Результаты из зашифрованных столбцов не расшифровываются. Приложение получает зашифрованные значения в виде массивов байтов (byte[]).

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Вставка и извлечение зашифрованных данных примеров 
В следующих примерах показано получение и изменение данных в зашифрованных столбцах. В примерах предполагается целевую таблицу со следующей схемой и зашифрованных столбцов SSN и BirthDate. Если вы настроили главного ключа столбца с именем «MyCMK» и ключа шифрования столбца с именем «MyCEK» (как описано в предыдущих разделах поставщиков хранилища ключей), можно создать таблицу, с помощью этого сценария:

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

Для каждого примера кода Java необходимо вставить код для конкретного хранилища ключей, расположенную там указаны.

Если при использовании поставщика хранилища ключей Azure Key Vault:

```
    String clientID = "<Azure Application ID>";
    String clientKey = "<Azure Application API Key Password>";
    SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
    Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
    keyStoreMap.put(akvProvider.getName(), akvProvider);
    SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
```

Если вы используете поставщик хранилища ключей Windows Certificate Store:

```
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;";
```

Если вы используете поставщик хранилища ключей ключ Store Java:

```
    String connectionString = "jdbc:sqlserver://localhost:1433;databaseName=Clinic;user=sa;password=******;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>Пример вставки данных
В этом примере показана вставка строки в таблицу Patients. Обратите внимание на следующие моменты:
- В образце кода нет ничего, связанного с шифрованием. Microsoft JDBC Driver для SQL Server автоматически обнаруживает и шифрует параметры, предназначенные для зашифрованных столбцов. Благодаря этому шифрование является прозрачным для приложения.
- Значениях, вставляемых в столбцы базы данных, включая зашифрованные столбцы, передаются как параметры, с помощью SQLServerPreparedStatement. Несмотря на то, что при отправке значений в незашифрованные столбцы использовать параметры необязательно (но настоятельно рекомендуется, так как они помогают предотвратить внедрение кода SQL), они требуются для значений, предназначенных для зашифрованных столбцов. Если значения, вставляемые в зашифрованные столбцы были переданы в качестве литералов, внедренных в инструкции запроса, выполнение запроса завершится ошибкой, так как драйвер, не сможет определить значения в зашифрованных столбцах, и не сможет зашифровать значения. В результате сервер отклонит их как несовместимые с зашифрованными столбцами.
- Все значения, выводимые программой будет в виде обычного текста, как Microsoft JDBC Driver для SQL Server прозрачно расшифровывает данные, полученные из зашифрованных столбцов.
- Если вы выполняете поиск с использованием предложения WHERE, значение, используемое в предложении WHERE должен передается как параметр, чтобы драйвер мог его прозрачно зашифровать перед их отправкой в базу данных. В следующем примере номера социального Страхования передается в качестве параметра, но LastName передается в качестве литерала, так как LastName не зашифрована.
- Метод задания свойства, используемое для параметра, предназначенных для столбца SSN — а методы setString(), который сопоставляется с типом данных SQL Server char и varchar. Если для этого параметра использовался метод задания setNString(), который сопоставляется с типом данных nchar или nvarchar, выполнение запроса завершится ошибкой, так как функция Always Encrypted не поддерживает преобразования из зашифрованных значений nchar и nvarchar в зашифрованные значения char и varchar.

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

### <a name="retrieving-plaintext-data-example"></a>Пример получения данных в виде открытого текста
В приведенном ниже примере показана фильтрация данных на основе зашифрованных значений и получение данных в виде открытого текста из зашифрованных столбцов. Обратите внимание на следующие моменты:
- Значение, используемое в предложении WHERE для фильтрации по столбцу SSN, необходимо передать как параметр, чтобы драйвер Microsoft JDBC Driver для SQL Server мог его прозрачно зашифровать перед отправкой в базу данных.
- Все значения, выводимые программой, будут представлены в виде обычного текста, так как драйвер Microsoft JDBC Driver для SQL Server прозрачно расшифровывает данные, полученные из столбцов SSN и BirthDate.

> [!NOTE]
> Если столбцы шифруются с помощью детерминированного шифрования, запросы могут выполнять сравнение на равенство для них. Дополнительные сведения см. в разделе [Выбор детерминированного или случайного шифрования в Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

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

В приведенном ниже примере показано извлечение двоичных зашифрованных данных из зашифрованных столбцов. Обратите внимание на следующие моменты:
- Так как функция Always Encrypted не включена в строке подключения, запрос будет возвращать зашифрованные значения SSN и BirthDate в виде байтовых массивов (программа преобразует значения в строки).
- Запрос, получающий данные из зашифрованных столбцов с отключенным постоянным шифрованием, может иметь параметры при условии, что ни один из параметров не предназначен для зашифрованного столбца. Приведенный ниже запрос выполняет фильтрацию по столбцу LastName, который не зашифрован в базе данных. Запрос, отфильтрованный по SSN или BirthDate, завершится ошибкой.

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
В этом разделе описываются общие категории ошибок, возникающих при выполнении запросов к зашифрованным столбцам из приложений Java, и приводятся рекомендации о том, как их избежать.

### <a name="unsupported-data-type-conversion-errors"></a>Ошибки преобразования неподдерживаемых типов данных
Постоянное шифрование поддерживает несколько преобразований для зашифрованных типов данных. Подробный список поддерживаемых преобразований типов см. в статье [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Далее приведены действия, позволяющие избежать ошибок при преобразовании типов данных. Убедитесь, что:

- При передаче значений для параметров, предназначенных для зашифрованных столбцов, используйте методы соответствующие задания. Убедитесь, что тип данных SQL Server параметра точно совпадал с типом целевого столбца или поддерживается преобразование типа данных SQL Server параметра в целевой тип столбца. Добавлены методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement, SQLServerResultSet для передачи параметров, соответствующих определенных типов данных SQL Server. Например, если столбец не зашифрован setTimestamp() метод можно использовать для передачи параметра, datetime2 или столбца данных типа datetime. Но при шифровании столбца необходимо использовать конкретный метод, представляющий тип столбца в базе данных. Например используйте setTimestamp() передавать значения в столбец зашифрованных datetime2 и использовать setDateTime() для передачи значений в столбец зашифрованных даты и времени. См. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) полный список новых интерфейсов API.
- Точность и масштаб параметров, предназначенных для столбцов типов данных SQL Server decimal и numeric, соответствуют точности и масштабу, настроенным для целевого столбца. Добавлены методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement, SQLServerResultSet принимать точность и масштаб, а также значения данных для параметров/столбцами, представляющими десятичных и числовых типов данных. См. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) полный список новых/перегружены API-интерфейсов.  
- Точность долей секунды/масштаб параметров, предназначенных для столбцов datetime2, datetimeoffset или типы данных SQL Server времени не больше, чем точность долей секунды или масштаб для целевого столбца в запросах, которые изменяют значения целевого столбца . Добавлены методы API для классов SQLServerPreparedStatement и SQLServerCallableStatement, SQLServerResultSet принимать долей секунды точностью или масштабом вместе со значениями данных для представления этих типов данных параметров. Полный список новых/перегружены API-интерфейсов, см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).   

### <a name="errors-due-to-incorrect-connection-properties"></a>Ошибки из-за свойства неправильное соединения
В этом разделе описывается настройка параметров подключения должным образом, для использования постоянного шифрования данных. Поскольку зашифрованные данные типы поддерживают ограниченные преобразования **sendTimeAsDatetime** и **sendStringParametersAsUnicode** параметры подключения требуется правильная конфигурация, при использовании зашифрованных столбцов. Убедитесь, что: 
- [sendTimeAsDatetime](setting-the-connection-properties.md) при вставке данных в зашифрованные столбцы времени подключения имеет значение false. Дополнительные сведения см. в разделе [Настройка способа отправки значений java.sql.Time на сервер](configuring-how-java-sql-time-values-are-sent-to-the-server.md).
- [sendStringParametersAsUnicode](setting-the-connection-properties.md) подключение установлено значение true (или остается по умолчанию) при вставке данных в зашифрованные столбцы char/varchar/varchar(max).

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Ошибки, возникающие из-за передачи значений в виде открытого текста, а не в зашифрованном виде
Любое значение, предназначенное для зашифрованного столбца, должно быть зашифровано внутри приложения. Попытка вставки, изменения или фильтрации по значению в виде открытого текста в зашифрованном столбце приведет к возникновению ошибки, подобной следующей:

```
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Чтобы избежать таких ошибок, убедитесь, что:
- функция Always Encrypted включена для запросов приложений, предназначенных для зашифрованных столбцов (для строки подключения или конкретного запроса);
- с помощью подготовленных инструкций и параметры для отправки данных, предназначенных для зашифрованных столбцов. В примере ниже показан запрос, который вместо передачи литерала как параметра неправильно фильтрует по литералу или константе в зашифрованном столбце (SSN). Этот запрос завершится ошибкой:

```
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>Принудительное шифрование на входные параметры
Функция принудительное шифрование обеспечивает шифрование параметра, при использовании функции постоянного шифрования. Если используется принудительное шифрование и SQL Server сообщает драйверу, что параметр не должен быть зашифрован, запрос, использующий параметр, завершится ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих предоставление клиенту скомпрометированным SQL Server неверных метаданных шифрования, что может привести к раскрытию данных. Set * методы классов SQLServerPreparedStatement и SQLServerCallableStatement и обновление\* являются перегруженными методами в классе SQLServerResultSet для принимает логический аргумент, чтобы указать параметр force шифрования. Если значение этого аргумента равно false, драйвер не будет принудительно выполнять шифрование на параметры. Если принудительное шифрование имеет значение true, в запросе параметр отправляется только если целевой столбец зашифрован и постоянное шифрование включено для соединения или в отчете. Используя это свойство предоставляет дополнительный уровень безопасности, гарантируя, что драйвер не отправляют ошибочно данные для SQL Server как обычный текст, когда он должен быть зашифрован.

Дополнительные сведения о перегруженные методы SQLServerPreparedStatement и SQLServerCallableStatement с помощью параметра force шифрования, см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Управление влиянием Always Encrypted на производительность
Так как Always Encrypted является технологией шифрования на стороне клиента, значительное влияние на производительность происходит на стороне клиента, а не в базе данных. Помимо затрат на операции шифрования и расшифровки, существуют и другие источники снижения производительности на стороне клиента:
- Дополнительные обращения к базе данных для получения метаданных для параметров запроса.
- Вызовы хранилища главных ключей столбцов для доступа к главному ключу столбца.

В этом разделе описываются процессы оптимизации производительности, встроенные в Microsoft JDBC Driver для SQL Server, и способы управления влиянием двух указанных выше факторов на производительность.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Управление обращениями для получения метаданных для параметров запроса
Если для соединения включена функция Always Encrypted, по умолчанию драйвер будет вызывать [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) для каждого параметризованного запроса, передавая инструкцию запроса (без значений параметров) в SQL Server. [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) анализирует инструкцию запроса и для каждого параметра, который должен быть зашифрован, возвращает связанные с шифрованием сведения, позволяющие драйверу шифровать значения параметров. Такое поведение обеспечивает высокий уровень прозрачности для клиентского приложения. До тех пор, пока приложение использует параметры для передачи значений, предназначенных для зашифрованных столбцов к драйверу, оно (и разработчику приложений) не должны знать, какие запросы получают доступ к зашифрованным столбцам.

### <a name="setting-always-encrypted-at-the-query-level"></a>Задание постоянного шифрования на уровне запроса
Для управления влиянием получения метаданных шифрования для параметризованных запросов на производительность можно включить функцию Always Encrypted для отдельных запросов, а не настраивать ее для соединения. Таким образом, это гарантирует, что sys.sp_describe_parameter_encryption вызывается только для запросов, которые точно имеют параметры, предназначенные для зашифрованных столбцов. Обратите внимание, что в этом случае снижается прозрачность шифрования: при изменении свойств шифрования столбцов базы данных может потребоваться изменить код приложения в соответствии с изменениями схемы.

Для управления поведением постоянного шифрования отдельных запросов, необходимо настроить объектов отдельные инструкции, передавая перечисления, SQLServerStatementColumnEncryptionSetting, который указывает отправлено и получено при чтении и записи данных зашифрованные столбцы для этой инструкцией. Ниже приведены некоторые полезные рекомендации.
- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, получает доступ к зашифрованным столбцам, следуйте приведенным ниже рекомендациям.
    - Задайте для ключевого слова строки подключения **columnEncryptionSetting** значение **Enabled**.
    - Задайте SQLServerStatementColumnEncryptionSetting.Disabled для отдельных запросов, которые не обращаются к зашифрованным столбцам. Таким образом будет отключена возможность вызова sys.sp_describe_parameter_encryption и расшифровки всех значений в результирующем наборе.
    - Задайте SQLServerStatementColumnEncryptionSetting.ResultSet для отдельных запросов, которые не имеют параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Таким образом будет отключена возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.
- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, не получает доступ к зашифрованным столбцам, следуйте приведенным ниже рекомендациям.
    - Задайте для ключевого слова строки подключения **columnEncryptionSetting** значение **Disabled**.
    - Задайте SQLServerStatementColumnEncryptionSetting.Enabled для отдельных запросов, имеющих параметры, которые требуется зашифровать. Таким образом будет включена возможность вызова sys.sp_describe_parameter_encryption и расшифровки результатов запроса, полученных из зашифрованных столбцов.
    - Задайте SQLServerStatementColumnEncryptionSetting.ResultSet для отдельных запросов, которые не имеют параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Таким образом будет отключена возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.

Параметры SQLServerStatementColumnEncryptionSetting не может использоваться для обхода шифрования и получить доступ к данным в виде обычного текста. Дополнительные сведения о том, как настройка шифрования столбцов в инструкции см. в разделе [всегда зашифрованы Справочник по API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

В приведенном ниже примере функция Always Encrypted отключена для подключения к базе данных. Запрос, выполняемый приложением, имеет параметр, предназначенный для незашифрованного столбца LastName. Запрос получает данные из зашифрованных столбцов SSN и BirthDate. В этом случае вызывать sys.sp_describe_parameter_encryption для получения метаданных шифрования не требуется. Однако необходимо включить расшифровку результатов запроса, чтобы приложение могло получать значения в виде обычного текста из двух зашифрованных столбцов. Чтобы убедиться, что используется параметр SQLServerStatementColumnEncryptionSetting.ResultSet.

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
Чтобы уменьшить количество вызовов к хранилищу главных ключей столбцов для расшифровки ключей шифрования столбцов, драйвер Microsoft JDBC Driver для SQL Server кэширует ключи шифрования столбцов с открытым текстом в памяти. После получения значения ключа шифрования зашифрованного столбца из метаданных базы данных драйвер сначала пытается найти ключ шифрования столбца с открытым текстом, соответствующий зашифрованному значению ключа. Драйвер обращается к хранилищу ключей, содержащему главный ключ столбца, только в том случае, если ему не удается найти значение ключа шифрования зашифрованных столбцов в кэше.

Можно настроить значение времени жизни для записи ключей шифрования столбцов в кэше, используя файловый API, setColumnEncryptionKeyCacheTtl(), в классе SQLServerConnection. Значение для записи ключей шифрования столбцов в кэше, время жизни по умолчанию — два часа. Чтобы отключить кэширование, используйте значение 0. Чтобы задать любое значение времени жизни, используйте следующие API:

```
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

Например чтобы задать значение времени жизни 10 минут, используйте следующую команду:

```
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

Только дней, часов, МИНУТ или СЕКУНД поддерживаются в качестве единицы времени.  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Копирование зашифрованных данных с помощью SQLServerBulkCopy
С помощью SQLServerBulkCopy можно скопировать данные, которые уже зашифрованы и хранятся в одной таблице, в другую таблицу, не расшифровывая их. Для этого выполните указанные далее действия.

- Убедитесь, что конфигурация шифрования целевой таблицы идентична конфигурации исходной таблицы. В частности, обе таблицы должны иметь одинаковые зашифрованные столбцы, которые должны быть зашифрованы с помощью одних и тех же типов шифрования и ключей шифрования. Если способ шифрования какого-либо конечного столбца отличается от способа шифрования соответствующего исходного столбца, вы не сможете расшифровать данные в конечной таблице после операции копирования. Данные будут повреждены.
- Настройте подключения базы данных к исходной и конечной таблицам без включения функции Always Encrypted.
- Задайте параметр allowEncryptedValueModifications. Дополнительные сведения см. в разделе [с помощью массового копирования с драйвером JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

> [!NOTE]
> Будьте внимательны при указании параметра AllowEncryptedValueModifications, так как это может привести к повреждению базы данных, поскольку драйвер Microsoft JDBC Driver для SQL Server не проверяет необходимость шифрования данных или правильность их шифрования с помощью тех же типа шифрования, алгоритма и ключа, что и для конечного столбца.

## <a name="see-also"></a>См. также:
[Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
