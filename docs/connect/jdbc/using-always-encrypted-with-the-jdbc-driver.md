---
title: Использование постоянного шифрования с драйвером JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 271c0438-8af1-45e5-b96a-4b1cabe32707
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e1f15e490a8d0e803bf0936c07d2e739009e1bf5
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026645"
---
# <a name="using-always-encrypted-with-the-jdbc-driver"></a>Использование функции Always Encrypted с драйвером JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Эта страница содержит сведения о том, как разрабатывать приложения Java с использованием [Always Encrypted](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.

Функция Always Encrypted позволяет шифровать конфиденциальные данные в клиентах, не раскрывая данные или ключи шифрования для SQL Server или базы данных SQL Azure. Драйвер с поддержкой Always Encrypted, такой как Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server, реализует это за счет прозрачного шифрования и расшифровки конфиденциальных данных в клиентском приложении. Драйвер автоматически определяет, какие параметры запроса соответствуют столбцам базы данных Always Encrypted и шифрует значения этих параметров перед их отправкой в SQL Server или Базу данных SQL Azure. Аналогичным образом драйвер прозрачно расшифровывает данные, полученные из зашифрованных столбцов базы в результатах запроса. Дополнительные сведения см. в разделе [Always encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md) и Справочнике по [API Always ENCRYPTED для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

## <a name="prerequisites"></a>предварительные требования
- Убедитесь, что на компьютере разработки установлен драйвер Microsoft JDBC 6,0 (или более поздней версии) для SQL Server. 
- Скачайте и установите файлы политики юрисдикции неограниченной стойкости Java Cryptography Extension (JCE).  Обязательно прочитайте содержащийся в ZIP-архиве файл сведений, чтобы получить инструкции по установке и сопутствующие сведения о возможных проблемах экспорта и импорта.  

    - При использовании mssql-jdbc-X.X.X.jre7.jar или sqljdbc41.jar файлы политики можно скачать на странице [скачивания файлов политики юрисдикции неограниченной стойкости Java Cryptography Extension (JCE) 7](https://www.oracle.com/technetwork/java/javase/downloads/jce-7-download-432124.html).

    - При использовании mssql-jdbc-X.X.X.jre8.jar или sqljdbc42.jar файлы политики можно скачать на странице [скачивания файлов политики юрисдикции неограниченной стойкости Java Cryptography Extension (JCE) 8](https://www.oracle.com/technetwork/java/javase/downloads/jce8-download-2133166.html).

    - При использовании Мсскл-ждбк-КС. X. X. jre9. jar файл политики не требуется скачивать. Политика юрисдикции в Java 9 по умолчанию имеет неограниченное стойкое шифрование.

## <a name="working-with-column-master-key-stores"></a>Работа с хранилищами главных ключей столбцов
Для шифрования или расшифровки данных в зашифрованных столбцах SQL Server сохраняет ключи шифрования столбцов. Ключи шифрования столбцов хранятся в зашифрованном виде в метаданных базы данных. Каждый ключ шифрования столбца имеет соответствующий главный ключ столбца, который используется для шифрования ключа шифрования столбца. Метаданные базы данных не содержат главных ключей столбцов. Эти ключи удерживаются только клиентом. Однако метаданные базы данных содержат сведения о том, где хранятся главные ключи столбцов относительно клиента. Например, метаданные базы данных могут сказать, что хранилище ключей, содержащее главный ключ столбца, является хранилищем сертификатов Windows, а конкретный сертификат, используемый для шифрования и расшифровки, расположен по указанному пути в хранилище сертификатов Windows. Если у клиента есть доступ к этому сертификату в хранилище сертификатов Windows, он может получить сертификат. Затем сертификат можно использовать для расшифровки ключа шифрования столбца. Затем этот ключ шифрования можно использовать для расшифровки или шифрования данных в зашифрованных столбцах, использующих этот ключ шифрования столбца.

Драйвер Microsoft JDBC для SQL Server взаимодействует с хранилищем ключей с помощью поставщика хранилища главных ключей столбцов, который является экземпляром класса, производного от **склсерверколумненкриптионкэйсторепровидер**.

### <a name="using-built-in-column-master-key-store-providers"></a>Использование встроенных поставщиков хранилища главных ключей столбцов
Драйвер Microsoft JDBC для SQL Server поставляется со следующими встроенными поставщиками хранилища главных ключей столбцов. Некоторые из этих поставщиков предварительно зарегистрированы с определенными именами поставщиков (используемыми для поиска поставщика), а для некоторых требуется либо дополнительные учетные данные, либо явная регистрация.

| Class                                                 | Описание                                        | Имя поставщика  | Предварительно зарегистрировано? |
| :---------------------------------------------------- | :------------------------------------------------- | :---------------------- | :----------------- |
| **SQLServerColumnEncryptionAzureKeyVaultProvider**    | Поставщик хранилища ключей для Azure Key Vault. | AZURE_KEY_VAULT         | нет                 |
| **SQLServerColumnEncryptionCertificateStoreProvider** | Поставщик для хранилища сертификатов Windows.      | MSSQL_CERTIFICATE_STORE | Да                |
| **склсерверколумненкриптионжавакэйсторепровидер**     | Поставщик для хранилища ключей Java                   | MSSQL_JAVA_KEYSTORE     | Да                |

Для предварительно зарегистрированных поставщиков хранилища ключей не нужно вносить изменения в код приложения для использования этих поставщиков, но обратите внимание на следующие элементы:

- Вы (или ваш администратор баз данных) должны проверить правильность имени поставщика, настроенного в метаданных главного ключа столбца, и убедиться в том, что путь к главному ключу столбца соответствует формату пути к ключу, который является допустимым для данного поставщика. Для настройки ключей рекомендуется использовать такое средство, как среда SQL Server Management Studio, которое при выполнении инструкции CREATE COLUMN MASTER KEY (Transact-SQL) автоматически создает допустимые имена поставщиков и пути к ключам.
- Убедитесь, что приложение может получить доступ к ключу в хранилище ключей. Для этого может потребоваться предоставить приложению доступ к ключу или хранилищу ключей (в зависимости от хранилища ключей) либо выполнить другие действия по настройке конкретного хранилища ключей. Например, для использования Склсерверколумненкриптионжавакэйсторепровидер необходимо указать расположение и пароль для хранилища ключей в свойствах соединения. 

Все эти поставщики хранилища ключей подробно описаны в следующих разделах. Для использования Always Encrypted необходимо реализовать только один поставщик хранилища ключей.

### <a name="using-azure-key-vault-provider"></a>Использование поставщика хранилища ключей Azure
Хранилище Azure Key Vault удобно для хранения главных ключей столбцов для Always Encrypted и управления ими, особенно в том случае, если приложение размещено в Azure. Драйвер Microsoft JDBC для SQL Server включает встроенный поставщик Склсерверколумненкриптионазурекэйваултпровидер для приложений с ключами, хранящимися в Azure Key Vault. Имя этого поставщика — AZURE_KEY_VAULT. Чтобы использовать поставщик хранилища Azure Key Vault, разработчику приложения необходимо создать хранилище и ключи в Azure Key Vault и создать регистрацию приложения в Azure Active Directory. Зарегистрированному приложению должно быть предоставлено получение, расшифровка, шифрование, распаковка ключа, ключ переноса и проверка разрешений в политиках доступа, определенных для хранилища ключей, созданного для использования с Always Encrypted. Дополнительные сведения о настройке хранилища ключей и создании главного ключа столбца см. в разделе [Azure Key Vault —](https://blogs.technet.microsoft.com/kv/2015/06/02/azure-key-vault-step-by-step/) пошаговые инструкции и [Создание главных ключей столбцов в Azure Key Vault](../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md#creating-column-master-keys-in-azure-key-vault).

Примеры на этой странице, если вы создали Azure Key Vault главный ключ столбца и ключ шифрования столбца с помощью SQL Server Management Studio, скрипт T-SQL для их повторного создания может выглядеть так же, как в этом примере, с собственным **KEY_PATH** и **ENCRYPTED_VALUE**:

```sql
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

Чтобы использовать Azure Key Vault, клиентским приложениям необходимо создать экземпляр Склсерверколумненкриптионазурекэйваултпровидер и зарегистрировать его с помощью драйвера.

Ниже приведен пример инициализации Склсерверколумненкриптионазурекэйваултпровидер:  

```java
SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
```

**clientID** — это идентификатор приложения для регистрации приложения в экземпляре Azure Active Directory. **clientKey** — это ключевой пароль, зарегистрированный в этом приложении, который предоставляет доступ к Azure Key Vault через API.

После того как приложение создаст экземпляр Склсерверколумненкриптионазурекэйваултпровидер, приложение должно зарегистрировать экземпляр с драйвером с помощью метода SQLServerConnection. registerColumnEncryptionKeyStoreProviders (). Настоятельно рекомендуется зарегистрировать экземпляр с помощью имени поиска по умолчанию AZURE_KEY_VAULT, которое можно получить, вызвав API Склсерверколумненкриптионазурекэйваултпровидер. Зовите (). Использование имени по умолчанию позволит использовать такие средства, как SQL Server Management Studio или PowerShell, для инициализации ключей Always Encrypted и управления ими (средства используют имя по умолчанию для создания объекта метаданных для главного ключа столбца). В следующем примере показана регистрация поставщика Azure Key Vault. Дополнительные сведения о методе SQLServerConnection. registerColumnEncryptionKeyStoreProviders () см. в [справочнике по Always ENCRYPTED API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

```java
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(akvProvider.getName(), akvProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

> [!IMPORTANT]
>  Если вы используете Azure Key Vault поставщика хранилища ключей, Azure Key Vault реализация драйвера JDBC имеет зависимости от этих библиотек (из GitHub), которые должны быть включены в приложение:
>
>  [azure-sdk-for-java](https://github.com/Azure/azure-sdk-for-java)
>
>  [azure-activedirectory-library-for-java libraries](https://github.com/AzureAD/azure-activedirectory-library-for-java)
>
> Пример включения этих зависимостей в проект Maven см. в статье [скачивание зависимостей ADAL4J и AKV с помощью Apache Maven](https://github.com/Microsoft/mssql-jdbc/wiki/Download-ADAL4J-And-AKV-Dependencies-with-Apache-Maven) .

### <a name="using-windows-certificate-store-provider"></a>Использование поставщика хранилища сертификатов Windows
The SQLServerColumnEncryptionCertificateStoreProvider можно использовать для хранения главных ключей столбцов в хранилище сертификатов Windows. Используйте мастер Always Encrypted SQL Server Management Studio (SSMS) или другие поддерживаемые инструменты для создания определений главного ключа столбца и ключа шифрования столбцов в базе данных. Этот же мастер можно использовать для создания самозаверяющего сертификата в хранилище сертификатов Windows, который можно использовать в качестве главного ключа столбца для Always Encrypted данных. Дополнительные сведения о синтаксисе T-SQL для главного ключа столбца и ключа шифрования столбцов см. в статьях [Создание главного ключа столбца](../../t-sql/statements/create-column-master-key-transact-sql.md) и [Создание ключа шифрования столбца](../../t-sql/statements/create-column-encryption-key-transact-sql.md) соответственно.

Имя Склсерверколумненкриптионцертификатесторепровидер — MSSQL_CERTIFICATE_STORE, и его можно запрашивать через API-имя () объекта поставщика. Он автоматически регистрируется драйвером и может использоваться без каких бы то ни было изменений в приложении.

Примеры на этой странице, если вы создали главный ключ столбца и ключ шифрования столбца на основе хранилища сертификатов Windows с помощью SQL Server Management Studio, скрипт T-SQL для их повторного создания может выглядеть примерно так, как в этом примере, с собственным **KEY_ ПУТЬ** и **ENCRYPTED_VALUE**:

```sql
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
> В то время как другие поставщики хранилища ключей в этой статье доступны на всех платформах, поддерживаемых драйвером, реализация Склсерверколумненкриптионцертификатесторепровидер драйвера JDBC доступна только в операционных системах Windows. Он зависит от файла sqljdbc_auth. dll, который доступен в пакете драйверов. Чтобы использовать этот поставщик, скопируйте файл sqljdbc_auth.dll в системный каталог Windows на компьютере, на котором установлен драйвер JDBC. Или можно задать системное свойство java.libary.path для указания каталога, в котором содержится файл sqljdbc_auth.dll. При использовании 32-разрядной виртуальной машины Java (JVM) следует использовать файл sqljdbc_auth.dll в папке x86 folder, даже если используется операционная система x64. При использовании 64-разрядной виртуальной машины и процессора x64 используйте файл sqljdbc_auth.dll в папке x64. Например, если используется 32-разрядная виртуальная машина Java и драйвер JDBC установлен в каталоге по умолчанию, можно указать местоположение файла DLL, использовав следующий аргумент виртуальной машины при запуске приложения Java: `-Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86`

### <a name="using-java-key-store-provider"></a>Использование поставщика хранилища ключей Java
Драйвер JDBC поставляется со встроенной реализацией поставщика хранилища ключей для хранилища ключей Java. Если свойство строки подключения **keyStoreAuthentication** содержится в строке подключения и имеет значение "JavaKeyStorePassword", драйвер автоматически создает экземпляр и регистрирует поставщик для хранилища ключей Java. Имя поставщика хранилища ключей Java — MSSQL_JAVA_KEYSTORE. Это имя можно также запрашивать с помощью API Склсерверколумненкриптионжавакэйсторепровидер. Зовите (). 

Существует три свойства строки подключения, позволяющие клиентскому приложению указывать учетные данные, необходимые драйверу для проверки подлинности в хранилище ключей Java. Драйвер Инициализирует поставщик на основе значений этих трех свойств в строке подключения.

**keyStoreAuthentication:** Определяет используемое хранилище ключей Java. При использовании Microsoft JDBC Driver 6,0 и более поздних версий для SQL Server можно пройти проверку подлинности в хранилище ключей Java только с помощью этого свойства. Для хранилища ключей Java значение этого свойства должно быть `JavaKeyStorePassword`.

**keyStoreLocation:** Путь к файлу хранилища ключей Java, в котором хранится главный ключ столбца. Путь включает имя файла хранилища ключей.

**keyStoreSecret:** Секрет или пароль, используемые для хранилища ключей, а также для ключа. Для использования хранилища ключей Java ключи ключей и пароль должны быть одинаковыми.

Ниже приведен пример предоставления этих учетных данных в строке подключения:

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path_to_the_keystore_file>;keyStoreSecret=<keystore_key_password>";
```

Эти параметры также можно получить или задать с помощью объекта SQLServerDataSource. Дополнительные сведения см. [в справочнике по Always ENCRYPTED API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

Драйвер JDBC автоматически создает экземпляр Склсерверколумненкриптионжавакэйсторепровидер, если эти учетные данные имеются в свойствах соединения.

### <a name="creating-a-column-master-key-for-the-java-key-store"></a>Создание главного ключа столбца для хранилища ключей Java
Склсерверколумненкриптионжавакэйсторепровидер можно использовать с типами хранилища ключей JKS-или PKCS12. Чтобы создать или импортировать ключ для использования с этим поставщиком, используйте служебную программу Java [keytool](https://docs.oracle.com/javase/7/docs/technotes/tools/windows/keytool.html) . Ключ должен иметь тот же пароль, что и сам хранилище ключей. Ниже приведен пример создания открытого ключа и связанного с ним закрытого ключа с помощью служебной программы keytool.

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.jks -storepass mypassword -validity 360 -keysize 2048 -storetype jks
```

Эта команда создает открытый ключ и заносит его в самозаверяющий сертификат X. 509, который хранится в хранилище ключей "хранилище ключей. JKS-" вместе со связанным закрытым ключом. Эта запись в хранилище ключей идентифицируется псевдонимом "Алвайсенкриптедкэй".

Ниже приведен пример такого же использования типа хранилища PKCS12:

```
keytool -genkeypair -keyalg RSA -alias AlwaysEncryptedKey -keystore keystore.pfx -storepass mypassword -validity 360 -keysize 2048 -storetype pkcs12 -keypass mypassword
```

Если хранилище ключей имеет тип PKCS12, служебная программа keytool не запрашивает пароль ключа и пароль ключа должен предоставляться с параметром-кэйпасс, так как Склсерверколумненкриптионжавакэйсторепровидер требует, чтобы хранилище ключей и ключ совпадали. пароль.

Вы также можете экспортировать сертификат из хранилища сертификатов Windows в формате PFX и использовать его с параметром Склсерверколумненкриптионжавакэйсторепровидер. Экспортированный сертификат можно также импортировать в хранилище ключей Java в качестве типа JKS-.

После создания записи keytool создайте в базе данных метаданные главного ключа столбца, для которой требуется имя поставщика хранилища ключей и путь к ключу. Дополнительные сведения о создании метаданных главного ключа столбца см. в [статье Создание главного ключа столбца](../../t-sql/statements/create-column-master-key-transact-sql.md). Для Склсерверколумненкриптионжавакэйсторепровидер путь к ключу — это просто псевдоним ключа, а имя Склсерверколумненкриптионжавакэйсторепровидер — MSSQL_JAVA_KEYSTORE. Вы также можете запросить это имя с помощью открытого API-имени () класса Склсерверколумненкриптионжавакэйсторепровидер. 

Для создания главного ключа столбца используется следующий синтаксис T-SQL:

```sql
CREATE COLUMN MASTER KEY [<CMK_name>]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'<key_alias>'
)
```

Для Алвайсенкриптедкэй, созданного выше, определение главного ключа столбца будет выглядеть следующим образом:

```sql
CREATE COLUMN MASTER KEY [MyCMK]
WITH
(
    KEY_STORE_PROVIDER_NAME = N'MSSQL_JAVA_KEYSTORE',
    KEY_PATH = N'AlwaysEncryptedKey'
)
```

> [!NOTE]
> Встроенные функции SQL Server Management Studio не могут создавать определения главных ключей столбцов для хранилища ключей Java. Команды T-SQL должны использоваться программно.

### <a name="creating-a-column-encryption-key-for-the-java-key-store"></a>Создание ключа шифрования столбца для хранилища ключей Java
SQL Server Management Studio или любой другой инструмент нельзя использовать для создания ключей шифрования столбцов с помощью главных ключей столбцов в хранилище ключей Java. Клиентское приложение должно программно создавать ключ шифрования столбца с помощью класса Склсерверколумненкриптионжавакэйсторепровидер. Дополнительные сведения см. [в статье Использование поставщиков хранилища главных ключей столбцов для программной подготовки ключей](#using-column-master-key-store-providers-for-programmatic-key-provisioning).

### <a name="implementing-a-custom-column-master-key-store-provider"></a>Реализация настраиваемого поставщика хранилища главных ключей столбцов
Чтобы сохранить главные ключи столбцов в хранилище ключей, не поддерживаемом существующим поставщиком, можно реализовать настраиваемый поставщик, расширив класс SQLServerColumnEncryptionKeyStoreProvider и зарегистрировав поставщик с помощью метода SQLServerConnection.registerColumnEncryptionKeyStoreProviders().

```java
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

```java
SQLServerColumnEncryptionKeyStoreProvider storeProvider = new MyCustomKeyStore();
Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
keyStoreMap.put(storeProvider.getName(), storeProvider);
SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
```

## <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>Использование поставщиков хранилищ главных ключей столбцов для программной подготовки ключей
При доступе к зашифрованным столбцам драйвер Microsoft JDBC Driver для SQL Server прозрачно находит и вызывает нужный поставщик хранилища главных ключей столбцов, чтобы расшифровать ключи шифрования столбцов. Как правило, обычный код приложения не вызывает поставщики хранилища главных ключей напрямую. Однако вы можете создать экземпляр и вызвать поставщик программным способом для предоставления ключей Always Encrypted и управления ими. Этот шаг можно выполнить, чтобы создать ключ шифрования зашифрованного столбца и расшифровать ключ шифрования столбца как смену главного ключа столбца части, например. Дополнительные сведения см. в разделе [Overview of Key Management for Always Encrypted](../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)(Общие сведения об управлении ключами для постоянного шифрования).

Если используется настраиваемый поставщик хранилища ключей, может потребоваться реализация собственных средств управления ключами. При использовании ключей, хранящихся в хранилище сертификатов Windows или в Azure Key Vault, можно использовать существующие средства, такие как SQL Server Management Studio или PowerShell, для управления и инициализации ключей. При использовании ключей, хранящихся в хранилище ключей Java, необходимо подготавливать ключи программным способом. В следующем примере показано использование класса Склсерверколумненкриптионжавакэйсторепровидер для шифрования ключа с ключом, хранящимся в хранилище ключей Java.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionJavaKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerColumnEncryptionKeyStoreProvider;
import com.microsoft.sqlserver.jdbc.SQLServerException;

/**
 * This program demonstrates how to create a column encryption key programmatically for the Java Key Store.
 */
public class AlwaysEncrypted {
    // Alias of the key stored in the keystore.
    private static String keyAlias = "<provide key alias>";

    // Name by which the column master key will be known in the database.
    private static String columnMasterKeyName = "MyCMK";

    // Name by which the column encryption key will be known in the database.
    private static String columnEncryptionKey = "MyCEK";

    // The location of the keystore.
    private static String keyStoreLocation = "C:\\Dev\\Always Encrypted\\keystore.jks";

    // The password of the keystore and the key.
    private static char[] keyStoreSecret = "********".toCharArray();

    /**
     * Name of the encryption algorithm used to encrypt the value of the column encryption key. The algorithm for the system providers must be
     * RSA_OAEP.
     */
    private static String algorithm = "RSA_OAEP";

    public static void main(String[] args) {
        String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";

        try (Connection connection = DriverManager.getConnection(connectionUrl);
                Statement statement = connection.createStatement();) {

            // Instantiate the Java Key Store provider.
            SQLServerColumnEncryptionKeyStoreProvider storeProvider = new SQLServerColumnEncryptionJavaKeyStoreProvider(keyStoreLocation,
                    keyStoreSecret);

            byte[] encryptedCEK = getEncryptedCEK(storeProvider);

            /**
             * Create column encryption key For more details on the syntax, see:
             * https://docs.microsoft.com/sql/t-sql/statements/create-column-encryption-key-transact-sql Encrypted column encryption key first needs
             * to be converted into varbinary_literal from bytes, for which byteArrayToHex() is used.
             */
            String createCEKSQL = "CREATE COLUMN ENCRYPTION KEY "
                    + columnEncryptionKey
                    + " WITH VALUES ( "
                    + " COLUMN_MASTER_KEY = "
                    + columnMasterKeyName
                    + " , ALGORITHM =  '"
                    + algorithm
                    + "' , ENCRYPTED_VALUE =  0x"
                    + byteArrayToHex(encryptedCEK)
                    + " ) ";
            statement.executeUpdate(createCEKSQL);
            System.out.println("Column encryption key created with name : " + columnEncryptionKey);
        }
        // Handle any errors that may have occurred.
        catch (SQLException e) {
            e.printStackTrace();
        }
    }

    private static byte[] getEncryptedCEK(SQLServerColumnEncryptionKeyStoreProvider storeProvider) throws SQLServerException {
        String plainTextKey = "You need to give your plain text";

        // plainTextKey has to be 32 bytes with current algorithm supported
        byte[] plainCEK = plainTextKey.getBytes();

        // This will give us encrypted column encryption key in bytes
        byte[] encryptedCEK = storeProvider.encryptColumnEncryptionKey(keyAlias, algorithm, plainCEK);

        return encryptedCEK;
    }

    public static String byteArrayToHex(byte[] a) {
        StringBuilder sb = new StringBuilder(a.length * 2);
        for (byte b : a)
            sb.append(String.format("%02x", b).toUpperCase());
        return sb.toString();
    }
}
```

## <a name="enabling-always-encrypted-for-application-queries"></a>Включение постоянного шифрования для запросов приложений
Самым простым способом включения шифрования параметров и расшифровки результатов запросов к зашифрованным столбцам является установка для ключевого слова строки подключения **columnEncryptionSetting** значения **Enabled**.

Следующая строка подключения является примером включения Always Encrypted в драйвере JDBC:

```java
String connectionUrl = "jdbc:sqlserver://<server>:<port>;user=<user>;password=<password>;databaseName=<database>;columnEncryptionSetting=Enabled;";
SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
```

Следующий код является эквивалентным примером с помощью объекта SQLServerDataSource:

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(<port>);
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setDatabaseName("<database>");
ds.setColumnEncryptionSetting("Enabled");
SQLServerConnection con = (SQLServerConnection) ds.getConnection();
```

Постоянное шифрование также можно включить для отдельных запросов. См. подробнее об [управлении влиянием функции Always Encrypted на производительность](#controlling-the-performance-impact-of-always-encrypted). Включения функции Always Encrypted недостаточно для успешного шифрования или расшифровки. Необходимо также проверить выполнение следующих условий:
- Приложение имеет разрешения *VIEW ANY COLUMN MASTER KEY DEFINITION* и *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* для базы данных, необходимые для доступа к метаданным о ключах постоянного шифрования в базе данных. Дополнительные сведения см. в разделе [Разрешения в Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#database-permissions).
- Приложение может получить доступ к главному ключу столбца, который защищает ключи шифрования столбцов, шифрующие запрашиваемые столбцы базы данных. Чтобы использовать поставщик хранилища ключей Java, необходимо указать дополнительные учетные данные в строке подключения. Дополнительные сведения см. [в разделе Использование поставщика хранилища ключей Java](#using-java-key-store-provider).

### <a name="configuring-how-javasqltime-values-are-sent-to-the-server"></a>Настройка способа отправки значений java.sql.Time на сервер
Для настройки порядка отправки значения java.sql.Time используется свойство **sendTimeAsDatetime**. При установке значения false значение времени отправляется как тип SQL Server времени. При установке значения true значение времени отправляется как тип DateTime. Если столбец времени зашифрован, свойство **сендтимеасдатетиме** должно иметь значение false, так как зашифрованные столбцы не поддерживают преобразование из времени в DateTime. Также обратите внимание, что это свойство по умолчанию имеет значение true, поэтому при использовании зашифрованных столбцов времени необходимо задать для него значение false. В противном случае драйвер выдаст исключение. Начиная с версии 6,0 драйвера класс SQLServerConnection имеет два метода для настройки значения этого свойства программным способом:
 
* Public void setSendTimeAsDatetime (Boolean Сендтимеасдатетимевалуе)
* public boolean getSendTimeAsDatetime()

Дополнительные сведения об этом свойстве см. в разделе [Настройка отправки значений Java. SQL. Time на сервер](configuring-how-java-sql-time-values-are-sent-to-the-server.md).

### <a name="configuring-how-string-values-are-sent-to-the-server"></a>Настройка отправки строковых значений на сервер
Свойство соединения **sendStringParametersAsUnicode** используется для настройки отправки строковых значений в SQL Server. Если задано значение true, строковые параметры отправляются на сервер в Юникоде. Если задано значение false, то строковые параметры отправляются в формате, отличном от Юникода, например в ASCII или MBCS, а не в Юникоде. Значение этого свойства по умолчанию — true. Если Always Encrypted включен, а столбец char/varchar/varchar (max) зашифрован, значение **sendStringParametersAsUnicode** должно быть равно false. Если это свойство имеет значение true, драйвер выдаст исключение при расшифровке данных из зашифрованного столбца char/varchar/varchar (max), имеющего символы Юникода. Дополнительные сведения об этом свойстве см. [в разделе Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).
  
## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>Получение и изменение данных в зашифрованных столбцах
После включения Always Encrypted для запросов приложений можно использовать стандартные API-интерфейсы JDBC для извлечения или изменения данных в зашифрованных столбцах базы данных. Если приложение имеет необходимые разрешения базы данных и имеет доступ к главному ключу столбца, драйвер шифрует все параметры запроса, предназначенные для зашифрованных столбцов, и расшифровывает данные, полученные из зашифрованных столбцов.

Если функция Always Encrypted не включена, выполнение запросов с параметрами, предназначенными для зашифрованных столбцов, завершится ошибкой. Запросы по-прежнему могут получать данные из зашифрованных столбцов, пока для них не будут указаны параметры, предназначенные для зашифрованных столбцов. Но драйвер не будет пытаться расшифровать все значения, полученные из зашифрованных столбцов, и приложение будет получать двоичные зашифрованные данные (в виде массивов байтов).

В приведенной ниже таблице описывается поведение запросов в зависимости от того, включена ли функция Always Encrypted.

| Характеристика запроса                                                                           | Постоянное шифрование включено, и приложение может получать доступ к ключам и метаданным ключей                                                                                                                        | Функция Always Encrypted включена, и приложение не может получать доступ к ключам и метаданным ключей | Постоянное шифрование отключено                                                                                        |
| :--------------------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-------------------------------------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------ |
| Запросы с параметрами, предназначенными для зашифрованных столбцов.                                           | Значения параметров прозрачно шифруются.                                                                                                                                                           | Ошибка                                                                             | Ошибка                                                                                                               |
| Запросы, получающие данные из зашифрованных столбцов, без параметров, предназначенных для зашифрованных столбцов. | Результаты из зашифрованных столбцов прозрачно расшифровываются. Приложение получает в виде открытого текста значения типов данных JDBC, которые соответствуют типам SQL Server, настроенным для зашифрованных столбцов. | Ошибка                                                                             | Результаты из зашифрованных столбцов не расшифровываются. Приложение получает зашифрованные значения в виде массивов байтов (byte[]). |

### <a name="inserting-and-retrieving-encrypted-data-examples"></a>Примеры вставки и извлечения зашифрованных данных

В следующих примерах показано получение и изменение данных в зашифрованных столбцах. В примерах предполагается, что Целевая таблица имеет следующую схему, а также зашифрованные столбцы SSN и ДеньРождения. Если вы настроили главный ключ столбца с именем "Микмк" и ключ шифрования столбца с именем "Мицек" (как описано в предыдущих разделах поставщиков хранилища ключей), можно создать таблицу с помощью этого скрипта:

```sql
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

Для каждого примера кода Java необходимо вставить код, относящийся к хранилищу ключей, в указанном расположении.

Если вы используете Azure Key Vault поставщика хранилища ключей:

```java
    String clientID = "<Azure Application ID>";
    String clientKey = "<Azure Application API Key Password>";
    SQLServerColumnEncryptionAzureKeyVaultProvider akvProvider = new SQLServerColumnEncryptionAzureKeyVaultProvider(clientID, clientKey);
    Map<String, SQLServerColumnEncryptionKeyStoreProvider> keyStoreMap = new HashMap<String, SQLServerColumnEncryptionKeyStoreProvider>();
    keyStoreMap.put(akvProvider.getName(), akvProvider);
    SQLServerConnection.registerColumnEncryptionKeyStoreProviders(keyStoreMap);
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Если вы используете поставщик хранилища сертификатов Windows:

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;";
```

Если вы используете поставщик хранилища ключей Java:

```java
    String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;columnEncryptionSetting=Enabled;keyStoreAuthentication=JavaKeyStorePassword;keyStoreLocation=<path to jks or pfx file>;keyStoreSecret=<keystore secret/password>";
```

### <a name="inserting-data-example"></a>Пример вставки данных

В этом примере показана вставка строки в таблицу Patients. Обратите внимание на следующие моменты:

- В примере кода нет ничего, связанного с шифрованием. Драйвер Microsoft JDBC для SQL Server автоматически обнаруживает и шифрует параметры, предназначенные для зашифрованных столбцов. Благодаря этому шифрование является прозрачным для приложения.
- Значения, вставляемые в столбцы базы данных, включая зашифрованные столбцы, передаются как параметры с помощью SQLServerPreparedStatement. При отправке значений в незашифрованные столбцы использовать параметры необязательно (но настоятельно рекомендуется, так как они помогают предотвратить внедрение кода SQL), но они требуются для значений, предназначенных для зашифрованных столбцов. Если значения, вставленные в зашифрованные столбцы, были переданы в виде литералов, внедренных в инструкцию запроса, запрос завершится ошибкой, так как драйвер не сможет определить значения в целевых зашифрованных столбцах и не будет шифровать значения. В результате сервер отклонит их как несовместимые с зашифрованными столбцами.
- Все значения, выводимые программой, будут представлены в виде обычного текста, так как драйвер Microsoft JDBC Driver для SQL Server прозрачно расшифровывает данные, полученные из зашифрованных столбцов.
- При выполнении поиска с помощью предложения WHERE значение, используемое в предложении WHERE, должно быть передано в качестве параметра, чтобы драйвер мог его прозрачно зашифровать перед отправкой в базу данных. В следующем примере SSN передается в качестве параметра, а LastName передается в виде литерала, так как LastName не шифруется.
- Метод задания, используемый для параметра, предназначенного для столбца SSN, — это setString (), который сопоставляется с типом данных char/varchar SQL Server. Если для этого параметра использовался метод задания setNString(), который сопоставляется с типом данных nchar или nvarchar, выполнение запроса завершится ошибкой, так как функция Always Encrypted не поддерживает преобразования из зашифрованных значений nchar и nvarchar в зашифрованные значения char и varchar.

```java
// <Insert keystore-specific code here>
try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
        PreparedStatement insertStatement = sourceConnection.prepareStatement("INSERT INTO [dbo].[Patients] VALUES (?, ?, ?, ?)")) {
    insertStatement.setString(1, "795-73-9838");
    insertStatement.setString(2, "Catherine");
    insertStatement.setString(3, "Abel");
    insertStatement.setDate(4, Date.valueOf("1996-09-10"));
    insertStatement.executeUpdate();
    System.out.println("1 record inserted.\n");
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="retrieving-plaintext-data-example"></a>Пример получения данных в виде открытого текста

В приведенном ниже примере показана фильтрация данных на основе зашифрованных значений и получение данных в виде открытого текста из зашифрованных столбцов. Обратите внимание на следующие моменты:

- Значение, используемое в предложении WHERE для фильтрации по столбцу SSN, необходимо передать как параметр, чтобы драйвер Microsoft JDBC Driver для SQL Server мог его прозрачно зашифровать перед отправкой в базу данных.
- Все значения, выводимые программой, будут представлены в виде обычного текста, так как драйвер Microsoft JDBC Driver для SQL Server прозрачно расшифровывает данные, полученные из столбцов SSN и BirthDate.

> [!NOTE]
> Если столбцы шифруются с помощью детерминированного шифрования, запросы могут выполнять сравнение на равенство для них. Дополнительные сведения см. в разделе [Выбор детерминированного или случайного шифрования в Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md#selecting--deterministic-or-randomized-encryption).

```java
// <Insert keystore-specific code here>
try (Connection connection = DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = connection
                .prepareStatement("\"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN = ?;\"");) {
    selectStatement.setString(1, "795-73-9838");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("SSN: " + rs.getString("SSN") + ", FirstName: " + rs.getString("FirstName") + ", LastName:"
                + rs.getString("LastName") + ", Date of Birth: " + rs.getString("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="retrieving-encrypted-data-example"></a>Пример получения зашифрованных данных

Если функция Always Encrypted не включена, запрос может получать данные из зашифрованных столбцов, пока для него не будут указаны параметры, предназначенные для зашифрованных столбцов.

В приведенном ниже примере показано извлечение двоичных зашифрованных данных из зашифрованных столбцов. Обратите внимание на следующие моменты:

- Так как функция Always Encrypted не включена в строке подключения, запрос будет возвращать зашифрованные значения SSN и BirthDate в виде байтовых массивов (программа преобразует значения в строки).
- Запрос, получающий данные из зашифрованных столбцов с отключенным постоянным шифрованием, может иметь параметры при условии, что ни один из параметров не предназначен для зашифрованного столбца. Приведенный ниже запрос позволяет выполнить фильтрацию по столбцу LastName, который не зашифрован в базе данных. Запрос, отфильтрованный по SSN или BirthDate, завершится ошибкой.

```java
try (Connection sourceConnection = DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = sourceConnection
                .prepareStatement("SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE LastName = ?;");) {

    selectStatement.setString(1, "Abel");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("SSN: " + rs.getString("SSN") + ", FirstName: " + rs.getString("FirstName") + ", LastName:"
                + rs.getString("LastName") + ", Date of Birth: " + rs.getString("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>Как избежать распространенных проблем при запросе зашифрованных столбцов

В этом разделе описываются общие категории ошибок, возникающих при выполнении запросов к зашифрованным столбцам из приложений Java, и приводятся рекомендации о том, как их избежать.

### <a name="unsupported-data-type-conversion-errors"></a>Ошибки преобразования неподдерживаемых типов данных

Постоянное шифрование поддерживает несколько преобразований для зашифрованных типов данных. Подробный список поддерживаемых преобразований типов см. в статье [Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md). Далее приведены действия, позволяющие избежать ошибок при преобразовании типов данных. Убедитесь, что:

- при передаче значений для параметров, предназначенных для зашифрованных столбцов, используются правильные методы задания. Убедитесь, что тип данных SQL Server параметра точно совпадает с типом целевого столбца, или преобразование SQL Serverного типа данных параметра в целевой тип столбца поддерживается. Методы API были добавлены в классы SQLServerPreparedStatement, SQLServerCallableStatement и SQLServerResultSet для передачи параметров, соответствующих конкретным SQL Serverным типам данных. Например, если столбец не зашифрован, можно использовать метод setTimestamp () для передачи параметра в datetime2 или в столбец datetime. Однако при шифровании столбца необходимо использовать точный метод, представляющий тип столбца в базе данных. Например, используйте setTimestamp () для передачи значений в зашифрованный столбец datetime2 и используйте Сетдатетиме () для передачи значений в зашифрованный столбец datetime. Полный список новых API-интерфейсов см. [в справочнике по Always ENCRYPTED API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) .
- Точность и масштаб параметров, предназначенных для столбцов типов данных SQL Server decimal и numeric, соответствуют точности и масштабу, настроенным для целевого столбца. К классам SQLServerPreparedStatement, SQLServerCallableStatement и SQLServerResultSet были добавлены методы API для принятия точности и масштабирования вместе со значениями данных для параметров и столбцов, представляющих десятичные и числовые типы данных. Полный список новых или перегруженных API см. [в справочнике по api Always encrypted для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) .  
- точность или масштаб доли секунды, предназначенные для столбцов с типами данных datetime2, DateTimeOffset или time SQL Server, не превышает точность или масштаб доли секунды для целевого столбца в запросах, изменяющих значения целевого столбца . К классам SQLServerPreparedStatement, SQLServerCallableStatement и SQLServerResultSet были добавлены методы API для принятия значений точности и масштаба доли секунды вместе со значениями данных для параметров, представляющих эти типы данных. Полный список новых или перегруженных API см. в справочнике по [Always ENCRYPTED API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).

### <a name="errors-due-to-incorrect-connection-properties"></a>Ошибки из-за неправильного свойства соединения

В этом разделе описано, как правильно настроить параметры подключения для использования Always Encrypted данных. Так как зашифрованные типы данных поддерживают ограниченные преобразования, параметры подключения **сендтимеасдатетиме** и **sendStringParametersAsUnicode** должны иметь правильную конфигурацию при использовании зашифрованных столбцов. Убедитесь, что:

- параметр подключения [сендтимеасдатетиме](setting-the-connection-properties.md) имеет значение false при вставке данных в зашифрованные столбцы времени. Дополнительные сведения см. в разделе [Настройка отправки значений Java. SQL. Time на сервер](configuring-how-java-sql-time-values-are-sent-to-the-server.md).
- для параметра подключения [sendStringParametersAsUnicode](setting-the-connection-properties.md) задано значение true (или значение по умолчанию) при вставке данных в зашифрованные столбцы char/varchar/varchar (max).

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>Ошибки, возникающие из-за передачи значений в виде открытого текста, а не в зашифрованном виде

Любое значение, предназначенное для зашифрованного столбца, должно быть зашифровано внутри приложения. Попытка вставки, изменения или фильтрации по значению в виде открытого текста в зашифрованном столбце приведет к возникновению ошибки, подобной следующей:

```java
com.microsoft.sqlserver.jdbc.SQLServerException: Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'MyCEK', column_encryption_key_database_name = 'ae') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

Чтобы избежать таких ошибок, убедитесь, что:

- функция Always Encrypted включена для запросов приложений, предназначенных для зашифрованных столбцов (для строки подключения или конкретного запроса);
- для отправки данных, предназначенных для зашифрованных столбцов, используются подготовленные инструкции и параметры. В примере ниже показан запрос, который вместо передачи литерала как параметра неправильно фильтрует по литералу или константе в зашифрованном столбце (SSN). Этот запрос завершится ошибкой:

```java
ResultSet rs = connection.createStatement().executeQuery("SELECT * FROM Customers WHERE SSN='795-73-9838'");
```

## <a name="force-encryption-on-input-parameters"></a>Принудительное шифрование входных параметров

Функция принудительного шифрования обеспечивает шифрование параметра при использовании Always Encrypted. Если используется принудительное шифрование и SQL Server сообщает драйверу, что параметр не должен быть зашифрован, запрос, использующий параметр, завершится ошибкой. Это свойство обеспечивает дополнительную защиту от атак на систему безопасности, включающих предоставление клиенту скомпрометированным SQL Server неверных метаданных шифрования, что может привести к раскрытию данных. Методы Set * в классах SQLServerPreparedStatement и SQLServerCallableStatement и методы обновления\* в классе SQLServerResultSet перегружены, чтобы принять логический аргумент для указания параметра принудительного шифрования. Если значение этого аргумента равно false, драйвер не будет принудительно выполнять шифрование параметров. Если для параметра Принудительное шифрование установлено значение true, параметр запроса отправляется только в том случае, если целевой столбец зашифрован, а Always Encrypted включен в соединении или в инструкции. Использование этого свойства обеспечивает дополнительный уровень безопасности, гарантируя, что драйвер не отправляет данные по ошибке в SQL Server в виде открытого текста, когда ожидается его шифрование.

Дополнительные сведения о методах SQLServerPreparedStatement и SQLServerCallableStatement, которые перегружаются с параметром принудительного шифрования, см. в разделе [Справочник по API Always encrypted для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md) .  

## <a name="controlling-the-performance-impact-of-always-encrypted"></a>Управление влиянием Always Encrypted на производительность

Так как Always Encrypted является технологией шифрования на стороне клиента, значительное влияние на производительность происходит на стороне клиента, а не в базе данных. Помимо затрат на операции шифрования и расшифровки, существуют и другие источники снижения производительности на стороне клиента:

- Дополнительные обращения к базе данных для получения метаданных для параметров запроса.
- Вызовы хранилища главных ключей столбцов для доступа к главному ключу столбца.

В этом разделе описываются процессы оптимизации производительности, встроенные в Microsoft JDBC Driver для SQL Server, и способы управления влиянием двух указанных выше факторов на производительность.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>Управление обращениями для получения метаданных для параметров запроса

Если для соединения включена функция Always Encrypted, по умолчанию драйвер будет вызывать [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) для каждого параметризованного запроса, передавая инструкцию запроса (без значений параметров) в SQL Server. [sys.sp_describe_parameter_encryption](../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md) анализирует инструкцию запроса и для каждого параметра, который должен быть зашифрован, возвращает связанные с шифрованием сведения, позволяющие драйверу шифровать значения параметров. Такое поведение обеспечивает высокий уровень прозрачности для клиентского приложения. Пока приложение использует параметры для передачи значений, нацеленных на зашифрованные столбцы драйверу, приложению (и разработчику приложения) не нужно знать, какие запросы обращаются к зашифрованным столбцам.

### <a name="setting-always-encrypted-at-the-query-level"></a>Задание постоянного шифрования на уровне запроса

Для управления влиянием получения метаданных шифрования для параметризованных запросов на производительность можно включить функцию Always Encrypted для отдельных запросов, а не настраивать ее для соединения. Таким образом, это гарантирует, что sys.sp_describe_parameter_encryption вызывается только для запросов, которые точно имеют параметры, предназначенные для зашифрованных столбцов. Обратите внимание, что в этом случае снижается прозрачность шифрования: при изменении свойств шифрования столбцов базы данных может потребоваться изменить код приложения в соответствии с изменениями схемы.

Для управления Always Encryptedм поведением отдельных запросов необходимо настроить отдельные объекты инструкции, передав перечисление, Склсерверстатементколумненкриптионсеттинг, которое указывает, каким образом данные будут отправлены и получены при чтении и записи. зашифрованные столбцы для этого конкретного оператора. Ниже приведены некоторые полезные рекомендации.

- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, получает доступ к зашифрованным столбцам, следуйте приведенным ниже рекомендациям.

    - Задайте для ключевого слова строки подключения **columnEncryptionSetting** значение **Enabled**.
    - Задайте SQLServerStatementColumnEncryptionSetting.Disabled для отдельных запросов, которые не обращаются к зашифрованным столбцам. Таким образом будет отключена возможность вызова sys.sp_describe_parameter_encryption и расшифровки всех значений в результирующем наборе.
    - Задайте SQLServerStatementColumnEncryptionSetting.ResultSet для отдельных запросов, которые не содержат параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Таким образом будет отключена возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.

- Если большинство запросов, отправляемых клиентским приложением через подключение к базе данных, не получают доступ к зашифрованным столбцам, следуйте приведенным ниже рекомендациям:

    - Задайте для ключевого слова строки подключения **columnEncryptionSetting** значение **Disabled**.
    - Задайте SQLServerStatementColumnEncryptionSetting.Enabled для отдельных запросов, имеющих параметры, которые требуется зашифровать. Таким образом будет включена возможность вызова sys.sp_describe_parameter_encryption и расшифровки результатов запроса, полученных из зашифрованных столбцов.
    - Задайте SQLServerStatementColumnEncryptionSetting.ResultSet для запросов, которые не содержат параметров, требующих шифрования, но получают данные из зашифрованных столбцов. Таким образом будет отключена возможность вызова sys.sp_describe_parameter_encryption и шифрования параметров. Запрос сможет расшифровывать результаты из столбцов шифрования.

Параметры Склсерверстатементколумненкриптионсеттинг нельзя использовать для обхода шифрования и получения доступа к данным в виде открытого текста. Дополнительные сведения о настройке шифрования столбцов для инструкции см. в справочнике по [Always ENCRYPTED API для драйвера JDBC](../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md).  

В приведенном ниже примере функция Always Encrypted отключена для подключения к базе данных. Запрос, создаваемый приложением, содержит параметр, предназначенный для незашифрованного столбца LastName. Запрос получает данные из зашифрованных столбцов SSN и BirthDate. В этом случае вызывать sys.sp_describe_parameter_encryption для получения метаданных шифрования не требуется. Однако необходимо включить расшифровку результатов запроса, чтобы приложение могло получать значения в виде обычного текста из двух зашифрованных столбцов. Чтобы убедиться в этом, используется параметр Склсерверстатементколумненкриптионсеттинг. Results.

```java
// Assumes the same table definition as in Section "Retrieving and modifying data in encrypted columns"
// where only SSN and BirthDate columns are encrypted in the database.
String connectionUrl = "jdbc:sqlserver://<server>:<port>;databaseName=<database>;user=<user>;password=<password>;" 
        + "keyStoreAuthentication=JavaKeyStorePassword;"
        + "keyStoreLocation=<keyStoreLocation>" 
        + "keyStoreSecret=<keyStoreSecret>;";

String filterRecord = "SELECT FirstName, LastName, SSN, BirthDate FROM " + tableName + " WHERE LastName = ?";

try (SQLServerConnection connection = (SQLServerConnection) DriverManager.getConnection(connectionUrl);
        PreparedStatement selectStatement = connection.prepareStatement(filterRecord, ResultSet.TYPE_FORWARD_ONLY, ResultSet.CONCUR_READ_ONLY,
                connection.getHoldability(), SQLServerStatementColumnEncryptionSetting.ResultSetOnly);) {

    selectStatement.setString(1, "Abel");
    ResultSet rs = selectStatement.executeQuery();
    while (rs.next()) {
        System.out.println("First name: " + rs.getString("FirstName"));
        System.out.println("Last name: " + rs.getString("LastName"));
        System.out.println("SSN: " + rs.getString("SSN"));
        System.out.println("Date of Birth: " + rs.getDate("BirthDate"));
    }
}
// Handle any errors that may have occurred.
catch (SQLException e) {
    e.printStackTrace();
}
```

### <a name="column-encryption-key-caching"></a>Кэширование ключа шифрования столбца

Чтобы уменьшить количество вызовов к хранилищу главных ключей столбцов для расшифровки ключей шифрования столбцов, драйвер Microsoft JDBC Driver для SQL Server кэширует ключи шифрования столбцов с открытым текстом в памяти. После получения значения ключа шифрования зашифрованного столбца из метаданных базы данных драйвер сначала пытается найти ключ шифрования столбца с открытым текстом, соответствующий зашифрованному значению ключа. Драйвер обращается к хранилищу ключей, содержащему главный ключ столбца, только в том случае, если ему не удается найти значение ключа шифрования зашифрованных столбцов в кэше.

Вы можете настроить значение срока жизни для записей ключей шифрования столбцов в кэше с помощью API Сетколумненкриптионкэйкачеттл () в классе SQLServerConnection. Значение срока жизни по умолчанию для записей ключей шифрования столбцов в кэше составляет два часа. Чтобы отключить кэширование, используйте значение 0. Чтобы задать любое значение срока жизни, используйте следующий API:

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (int columnEncryptionKeyCacheTTL, TimeUnit unit)
```

Например, чтобы установить значение срока жизни в 10 минут, используйте:

```java
SQLServerConnection.setColumnEncryptionKeyCacheTtl (10, TimeUnit.MINUTES)
```

В качестве единицы времени поддерживаются только дни, часы, минуты или секунды.  

## <a name="copying-encrypted-data-using-sqlserverbulkcopy"></a>Копирование зашифрованных данных с помощью SQLServerBulkCopy

С помощью SQLServerBulkCopy можно скопировать данные, которые уже зашифрованы и хранятся в одной таблице, в другую таблицу, не расшифровывая их. Для этого выполните указанные далее действия.

- Убедитесь, что конфигурация шифрования целевой таблицы идентична конфигурации исходной таблицы. В частности, обе таблицы должны иметь одинаковые зашифрованные столбцы, которые должны быть зашифрованы с помощью одних и тех же типов шифрования и ключей шифрования. Если способ шифрования какого-либо конечного столбца отличается от способа шифрования соответствующего исходного столбца, вы не сможете расшифровать данные в конечной таблице после операции копирования. Данные будут повреждены.
- Настройте подключения базы данных к исходной и конечной таблицам без включения функции Always Encrypted.
- Задайте параметр allowEncryptedValueModifications. Дополнительные сведения см. в статье [Использование команды "выполнить групповое копирование" с помощью драйвера JDBC](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md).

> [!NOTE]
> Будьте внимательны при указании параметра AllowEncryptedValueModifications, так как это может привести к повреждению базы данных, поскольку драйвер Microsoft JDBC Driver для SQL Server не проверяет необходимость шифрования данных или правильность их шифрования с помощью тех же типа шифрования, алгоритма и ключа, что и для конечного столбца.

## <a name="see-also"></a>См. также раздел

[Always Encrypted (ядро СУБД)](../../relational-databases/security/encryption/always-encrypted-database-engine.md)
