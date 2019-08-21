---
title: Установка подключения с использованием проверки подлинности Azure Active Directory | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b596936010fcdce4eb5c0701c5f0c6631cd9687e
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028125"
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Установка подключения с использованием проверки подлинности Azure Active Directory

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье содержатся сведения о разработке приложений Java для использования функции проверки подлинности Azure Active Directory с драйвером Microsoft JDBC для SQL Server.

Вы можете использовать проверку подлинности Azure Active Directory (AAD), которая является механизмом подключения к базе данных SQL Azure версии 12 с помощью удостоверений в Azure Active Directory. Проверка подлинности Azure Active Directory используется для централизованного управления удостоверениями пользователей базы данных и в качестве альтернативы проверке подлинности SQL Server. Драйвер JDBC позволяет указать учетные данные Azure Active Directory в строке подключения JDBC для подключения к базе данных SQL Azure. Сведения о настройке проверки подлинности Azure Active Directory см. в подсоединении [к базе данных SQL с помощью проверки Подлинности Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Свойства подключения для поддержки проверки подлинности Azure Active Directory в драйвере Microsoft JDBC для SQL Server:
*   **Проверка**подлинности: Используйте это свойство, чтобы указать метод проверки подлинности SQL, используемый для соединения. Возможны следующие значения: 
    * **ActiveDirectoryMSI**
        * Поддерживается, начиная с версии Driver **v 7.2**, `authentication=ActiveDirectoryMSI` можно использовать для подключения к базе данных или хранилищу данных SQL Azure из ресурса Azure с включенной поддержкой "Identity". При необходимости **мсиклиентид** также можно указать в свойствах Connection/DataSource вместе с этим режимом проверки подлинности, который должен содержать идентификатор клиента управляемое удостоверение службы, который будет использоваться для получения **accessToken** для установления соединение.
    * **ActiveDirectoryIntegrated**
        * Поддерживается с версии Driver **v 6.0**, `authentication=ActiveDirectoryIntegrated` которую можно использовать для подключения к базе данных или хранилищу данных SQL Azure с помощью встроенной проверки подлинности. Чтобы использовать этот режим проверки подлинности, необходимо включить в Федерацию локальный службы федерации Active Directory (AD FS) (ADFS) с Azure Active Directory в облаке. После настройки можно подключиться, либо добавив собственную библиотеку "sqljdbc_auth. dll" в путь к классу приложения в ОС Windows, либо установив билет Kerberos для поддержки межплатформенной проверки подлинности. Вы сможете получить доступ к базе данных SQL Azure или ХРАНИЛИЩу данных, не запрашивать учетные данные при входе на компьютер, присоединенный к домену.
    * **ActiveDirectoryPassword**
        * Поддерживается с версии Driver **v 6.0**, `authentication=ActiveDirectoryPassword` которую можно использовать для подключения к базе данных или хранилищу данных SQL Azure с помощью имени и пароля участника Azure AD.
    * **SqlPassword**
        * Используйте `authentication=SqlPassword` для подключения к SQL Server с помощью свойств Username, User и Password.
    * **NotSpecified**
        * Используйте `authentication=NotSpecified` или оставьте значение по умолчанию, если ни один из этих методов проверки подлинности не требуется.

*   **accessToken**: Используйте это свойство соединения для подключения к базе данных SQL с помощью маркера доступа. accessToken можно задать только с помощью параметра Properties метода соединения () в классе диспетчер драйверов. Его нельзя использовать в URL-адресе соединения.  

Дополнительные сведения см. в описании свойства Authentication на странице [Настройка свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) .  


## <a name="client-setup-requirements"></a>Требования к установке клиента
Для проверки подлинности **активедиректоримси** на клиентском компьютере должны быть установлены следующие компоненты:
* Java 8 или более поздней версии
* Microsoft JDBC Driver 7,2 (или более поздней версии) для SQL Server
* Клиентская среда должна быть ресурсом Azure, а поддержка функций "Identity" должна быть включена.
* Пользователь автономной базы данных, представляющий управляемое удостоверение, назначенное системой для ресурса Azure или управляемое удостоверение, или одну из групп, к которым принадлежит ваш MSI-файл, должны существовать в целевой базе данных и иметь разрешение CONNECT.

Для других режимов проверки подлинности на клиентском компьютере должны быть установлены следующие компоненты:
* Java 7 или более поздней версии
* Microsoft JDBC Driver 6,0 (или более поздней версии) для SQL Server
* Если вы используете режим проверки подлинности на основе маркеров доступа, вам потребуется [Azure-ActiveDirectory-Library-для-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и ее зависимости для выполнения примеров из этой статьи. Дополнительные сведения см. в разделе **подключение с помощью маркера доступа** .
* Если вы используете режим проверки подлинности **ActiveDirectoryPassword** , вам потребуется [Azure-ActiveDirectory-Library-для-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и ее зависимости. Дополнительные сведения см. в разделе **подключение с использованием режима проверки подлинности ActiveDirectoryPassword** .
* Если вы используете режим **ActiveDirectoryIntegrated** , вам потребуется Azure-ActiveDirectory-Library-для-Java и ее зависимости. Дополнительные сведения см. в разделе **подключение с использованием режима проверки подлинности ActiveDirectoryIntegrated** .

## <a name="connecting-using-activedirectorymsi-authentication-mode"></a>Подключение с использованием режима проверки подлинности Активедиректоримси
Следующий пример иллюстрирует использование режима `authentication=ActiveDirectoryMSI`. Запустите этот пример из ресурса Azure, e, g виртуальной машины Azure, службы приложений или приложение-функция, которая является Федеративной с Azure Active Directory.

Перед выполнением примера замените имя сервера или базы данных именем сервера или базы данных в следующих строках:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
//Optional
ds.setMsiClientId("94de34e9-8e8c-470a-96df-08110924b814"); // Replace with Client ID of User-Assigned MSI to be used
```

В примере используется режим проверки подлинности Активедиректоримси:

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AAD_MSI {
    public static void main(String[] args) throws Exception {

        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryMSI");
        // Optional
        ds.setMsiClientId("94de34e9-8e8c-470a-96df-08110924b814"); // Replace with Client ID of User-Assigned MSI to be used

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```

Выполнение этого примера на виртуальной машине Azure Извлекает маркер доступа из _назначенного системой управляемого удостоверения_ или _управляемого удостоверения, назначенного пользователем_ (если указано **мсиклиентид** ), и устанавливает подключение с помощью полученного доступа. Лекс. Если подключение установлено, должно отобразиться следующее сообщение:

```bash
You have successfully logged on as: <your MSI username>
```

## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Подключение с использованием режима проверки подлинности ActiveDirectoryIntegrated
В версии 6,4 драйвер Microsoft JDBC добавляет поддержку проверки подлинности ActiveDirectoryIntegrated с помощью билета Kerberos на нескольких платформах (Windows, Linux и macOS).
Дополнительные сведения см. [в статье Установка билета Kerberos для Windows, Linux и Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) . Кроме того, в Windows sqljdbc_auth. dll также можно использовать для проверки подлинности ActiveDirectoryIntegrated с помощью драйвера JDBC.

> [!NOTE]
>  Если вы используете более старую версию драйвера, проверьте эту [ссылку](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) на наличие соответствующих зависимостей, необходимых для использования этого режима проверки подлинности. 

Следующий пример иллюстрирует использование режима `authentication=ActiveDirectoryIntegrated`. Запустите этот пример на компьютере, присоединенном к домену, который включен в Федерацию с Azure Active Directory. Пользователь автономной базы данных, представляющий субъект Azure AD или одну из групп, в которые вы входите, должен существовать в базе данных и иметь разрешение CONNECT. 

Перед построением и запуском примера на клиентском компьютере (на котором необходимо выполнить пример) Скачайте [библиотеку Azure-ActiveDirectory-Library-для-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и ее зависимости, а затем включите их в путь сборки Java.

Перед выполнением примера замените имя сервера или базы данных именем сервера или базы данных в следующих строках:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

В примере используется режим проверки подлинности ActiveDirectoryIntegrated:
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADIntegrated {
    public static void main(String[] args) throws Exception {

        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```

Выполнение этого примера на клиентском компьютере автоматически использует билет Kerberos и пароль не требуется. Если подключение установлено, должно отобразиться следующее сообщение:

```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Установка билета Kerberos в Windows, Linux и Mac

Необходимо настроить билет Kerberos, связывающий текущего пользователя с учетной записью домена Windows. Ниже приведены общие сведения о ключевых шагах.

#### <a name="windows"></a>Windows
JDK поставляется с `kinit`, который можно использовать для получения билета TGT от центр распространения ключей (KDC) на компьютере, присоединенном к домену, который включен в Федерацию с Azure Active Directory.

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>Шаг 1. получение билета предоставления билетов
- **Запустить в**: Windows
- **Действие**:
  - Используйте команду `kinit username@DOMAIN.COMPANY.COM` для получения билета TGT из KDC, после чего появится запрос на ввод пароля домена.
  - Используйте `klist` для просмотра доступных билетов. Если kinit успешно, вы увидите билет из KRBTGT/DOMAIN. COMPANY. COM @ DOMAIN.COMPANY.COM.

> [!NOTE]
>  Может потребоваться указать `.ini` файл с `-Djava.security.krb5.conf` приложением для определения местонахождения KDC.

#### <a name="linux-and-mac"></a>Linux и Mac

##### <a name="requirements"></a>Требования
Доступ к компьютеру, присоединенному к домену Windows, для обращения к контроллеру домена Kerberos.

##### <a name="step-1-find-kerberos-kdc"></a>Шаг 1. Поиск Kerberos KDC
- **Выполнить в**: Командная строка Windows
- **Действие**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (где "domain.Company.com" сопоставляется с именем вашего домена)
- **Образец вывода**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **Сведения для извлечения** Имя контроллера домена, в данном случае`co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>Шаг 2. Настройка KDC в krb5. conf
- **Запуск в**: Linux/Mac
- **Действие**: измените/etc/krb5.conf в любом редакторе. Настройте следующие ключи.
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  Сохраните файл krb5.conf и закройте редактор.

> [!NOTE]
>  Домен должен быть указан прописными буквами.

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>Шаг 3. Тестирование извлечения билета на получение билетов
- **Запуск в**: Linux/Mac
- **Действие**:
  - Используйте команду `kinit username@DOMAIN.COMPANY.COM` для получения билета TGT из KDC, после чего появится запрос на ввод пароля домена.
  - Используйте `klist` для просмотра доступных билетов. Если kinit успешно, вы увидите билет из KRBTGT/DOMAIN. COMPANY. COM @ DOMAIN.COMPANY.COM.

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Подключение с использованием режима проверки подлинности ActiveDirectoryPassword
Следующий пример иллюстрирует использование режима `authentication=ActiveDirectoryPassword`.

Перед сборкой и запуском примера выполните следующие действия.
1.  На клиентском компьютере (на котором необходимо выполнить пример) Скачайте [библиотеку Azure-ActiveDirectory-Library-для-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и ее зависимости, а затем включите их в путь сборки Java.
2.  Нахождение следующих строк кода и замена имени сервера или базы данных именем сервера или базы данных.
    ```java
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  Перейдите к следующим строкам кода и замените имя пользователя именем пользователя AAD, от имени которого вы хотите подключиться.
    ```java
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

В примере используется режим проверки подлинности ActiveDirectoryPassword:
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADUserPassword {
    
    public static void main(String[] args) throws Exception{
        
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        
        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
Если подключение установлено, в качестве выходных данных должно отобразиться следующее сообщение:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Должна существовать автономная база данных пользователя и пользователь автономной базы данных, представляющий указанного пользователя Azure AD или одну из групп, к которой принадлежит указанный пользователь Azure AD, должен существовать в базе данных и иметь разрешение CONNECT (кроме Azure Active Directory Администратор или группа сервера

## <a name="connecting-using-access-token"></a>Подключение с помощью маркера доступа
Приложения и службы могут получить маркер доступа из Azure Active Directory и использовать его для подключения к базе данных или хранилищу данных SQL Azure.

> [!NOTE] 
> **accessToken** можно задать только с помощью параметра Properties метода соединения () в классе диспетчер драйверов. Его нельзя использовать в строке подключения.

Пример ниже содержит простое приложение Java, которое подключается к базе данных или хранилищу данных SQL Azure с помощью проверки подлинности на основе маркеров доступа. Перед сборкой и запуском примера выполните следующие действия.
1.  Создайте учетную запись приложения в Azure Active Directory для своей службы.
    1. Войдите на портал Azure.
    2. Щелкните Azure Active Directory на панели навигации слева.
    3. Перейдите на вкладку "Регистрация приложений".
    4. В ящике щелкните "создать регистрацию приложения".
    5. Введите митокентест в качестве понятного имени для приложения, выберите "веб-приложение или API".
    6. Не требуется URL-адрес для входа. Просто укажите все: "https://mytokentest".
    7. В нижней части щелкните "создать".
    9. Находясь в портал Azure, перейдите на вкладку "Параметры" приложения и откройте вкладку "Свойства".
    10. Найдите значение Application ID (идентификатор клиента) и скопируйте его в сторону, оно понадобится позже при настройке приложения (например, 1846943b-ad04-4808-aa13-4702d908b5c1). См. следующий снимок.
    11. В разделе "ключи" Создайте ключ, заполнив поле "имя", выбрав длительность ключа и сохранив конфигурацию (оставьте поле "значение" пустым). После сохранения поле значения должно быть заполнено автоматически, копировать созданное значение. Это секрет клиента.
    12. Щелкните Azure Active Directory на левой панели. В разделе "Регистрация приложений" найдите вкладку "конечные точки". Скопируйте URL-адрес в КОНЕЧНОЙ точке ТОКЕНа OATH 2,0. это URL-адрес STS.
    
    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Войдите в свою базу данных пользователя Azure SQL Server в качестве администратора Azure Active Directory и с помощью команды T-SQL подготавливает пользователя автономной базы данных к субъекту приложения. Дополнительные сведения см. в статье [Подключение к базе данных SQL или хранилищу данных SQL с помощью Azure Active Directory проверки](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/) подлинности для получения дополнительных сведений о создании Azure Active Directory администратора и пользователя автономной базы данных.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  На клиентском компьютере (на котором необходимо выполнить пример) Скачайте библиотеку [Azure-ActiveDirectory-Library-для-Java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и ее зависимости, а затем включите ее в путь сборки Java. Обратите внимание, что Azure-ActiveDirectory-Library-for-Java требуется только для выполнения этого примера. В примере используются API из этой библиотеки для получения маркера доступа из Azure AAD. Если у вас уже есть маркер доступа, этот шаг можно пропустить. Обратите внимание, что также необходимо удалить раздел в примере, который извлекает маркер доступа.

В следующем примере замените URL-адрес STS, идентификатор клиента, секрет клиента, имя сервера и базы данных значениями.

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD.
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;

public class AADTokenBased {

    public static void main(String[] args) throws Exception {

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
        String clientId = "1846943b-ad04-4808-aa13-4702d908b5c1"; // Replace with your client ID.
        String clientSecret = "..."; // Replace with your client secret.

        AuthenticationContext context = new AuthenticationContext(stsurl, false, Executors.newFixedThreadPool(1));
        ClientCredential cred = new ClientCredential(clientId, clientSecret);

        Future<AuthenticationResult> future = context.acquireToken(spn, cred, null);
        String accessToken = future.get().getAccessToken();

        System.out.println("Access Token: " + accessToken);

        // Connect with the access token.
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name.
        ds.setDatabaseName("demo"); // Replace with your database name.
        ds.setAccessToken(accessToken);

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();
                ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()")) {
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
``` 

Если подключение установлено успешно, в качестве выходных данных должно отобразиться следующее сообщение:

```bash
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
