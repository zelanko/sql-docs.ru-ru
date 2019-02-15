---
title: Соединение с использованием проверки подлинности Azure Active Directory | Документы Майкрософт
ms.custom: ''
ms.date: 01/29/2019
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62892cebe5c3c709cedee94b620b2c0e4cfeb258
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737035"
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Соединение с использованием проверки подлинности Azure Active Directory

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье сведения о разработке приложений Java, чтобы использовать функцию проверки подлинности Azure Active Directory с Microsoft JDBC Driver для SQL Server.

Можно использовать проверку подлинности Azure Active Directory (AAD), который представляет собой механизм подключения к базе данных SQL Azure версии 12 с помощью удостоверений в Azure Active Directory. Проверка подлинности Azure Active Directory используется для централизованного управления удостоверениями пользователей базы данных и в качестве альтернативы проверке подлинности SQL Server. Драйвер JDBC можно указать учетные данные Azure Active Directory в строке подключения JDBC для подключения к базе данных SQL Azure. Сведения о том, как настроить проверку подлинности Azure Active Directory [подключение к SQL базы данных с помощью аутентификации Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Ниже приведены свойства соединения для поддержки проверки подлинности Azure Active Directory в Microsoft JDBC Driver для SQL Server.
*   **Проверка подлинности**: это свойство используется, чтобы указать, какой метод проверки подлинности SQL для подключения. Возможны следующие значения: 
    * **ActiveDirectoryMSI**
        * Поддерживается начиная с версии драйвера **v7.2**, `authentication=ActiveDirectoryMSI` может использоваться для подключения к базе данных или хранилище данных SQL Azure из внутри ресурса Azure с поддержкой «Identity». При необходимости **msiClientId** можно также указать в свойствах соединения или источник данных вместе с этот режим проверки подлинности, который должен содержать идентификатор клиента для управляемого удостоверения службы для получения  **accessToken** для установления соединения.
    * **ActiveDirectoryIntegrated**
        * Поддерживается начиная с версии драйвера **версии 6.0**, `authentication=ActiveDirectoryIntegrated` может использоваться для подключения к базе данных или хранилище данных SQL с помощью встроенной проверки подлинности. Чтобы использовать этот режим проверки подлинности, необходимо создать федерацию локальной Active Directory Federation Services (ADFS) с Azure Active Directory в облаке. После его настройки, можно подключить путем добавления собственной библиотеки «sqljdbc_auth.dll» в приложение путь к классу в операционной системе Windows, или настройка билет Kerberos для поддержки проверки подлинности между различными платформами. Можно получить доступ к DB/хранилище данных SQL Azure, не вводя учетные данные при последующем входе систему для присоединения к домену.
    * **ActiveDirectoryPassword**
        * Поддерживается начиная с версии драйвера **версии 6.0**, `authentication=ActiveDirectoryPassword` может использоваться для подключения к базе данных или хранилище данных SQL с помощью имени участника Azure AD и пароль.
    * **SqlPassword**
        * Используйте `authentication=SqlPassword` для подключения к SQL Server, с помощью свойств имени пользователя или пользователя и пароль.
    * **NotSpecified**
        * Используйте `authentication=NotSpecified` или оставить значение по умолчанию, если ни одно из этих методов проверки подлинности не нужно.

*   **/AccessToken:** Используйте это свойство подключения для подключения к базе данных SQL с помощью маркера доступа. accessToken может устанавливаться только с помощью параметра свойства getConnection() метода в классе диспетчер драйверов. Он не может использоваться в URL-АДРЕСЕ соединения.  

Дополнительные сведения см. в разделе свойство проверки подлинности на [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) страницы.  


## <a name="client-setup-requirements"></a>Требования к установке клиента
Для **ActiveDirectoryMSI** проверки подлинности, ниже компоненты должны устанавливаться на клиентском компьютере:
* Java 8 или более поздней версии
* Microsoft JDBC Driver 7.2 (или более поздней версии) для SQL Server
* Клиентская среда должна быть ресурсом Azure и должен иметь включена поддержка функции «Identity».
* Пользователь автономной базы данных, система назначаемое управляемое удостоверение ресурсов Azure или пользователь назначаемое управляемое удостоверение или одной из групп, к которой принадлежит удостоверения MSI, должен существовать в целевой базе данных и должна иметь разрешение CONNECT.

Для других режимов проверки подлинности ниже компоненты должны устанавливаться на клиентском компьютере:
* Java 7 или более поздней версии
* Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server
* Если вы используете режим проверки подлинности на основе маркеров доступа, необходимо [azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимостей для выполнения примеров из этой статьи. Дополнительные сведения см. в разделе **подключение с использованием токена доступа** раздел.
* Если вы используете **ActiveDirectoryPassword** режим проверки подлинности, вам потребуется [azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимости. Дополнительные сведения см. в разделе **подключение с использованием режима аутентификации ActiveDirectoryPassword** раздел.
* Если вы используете **ActiveDirectoryIntegrated** режиме, вам потребуется azure-activedirectory-library-for-java и его зависимости. Дополнительные сведения см. в разделе **подключение с использованием режима проверки подлинности ActiveDirectoryIntegrated** раздел.

## <a name="connecting-using-activedirectorymsi-authentication-mode"></a>Подключение с использованием режима проверки подлинности ActiveDirectoryMSI
Следующий пример иллюстрирует использование режима `authentication=ActiveDirectoryMSI`. Запустите этот пример из внутри ресурса Azure, e, g виртуальной машине Azure, службы приложений или приложения-функции, включенный в федерацию с Azure Active Directory.

Замените имя сервера или базы данных перед выполнением в примере имя сервера или базы данных в следующие строки:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
//Optional
ds.setMsiClientId("94de34e9-8e8c-470a-96df-08110924b814"); // Replace with Client ID of User-Assigned MSI to be used
```

Этот пример с использованием режима проверки подлинности ActiveDirectoryMSI:

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

На виртуальной машине Azure под управлением в этом примере получает маркер доступа из _системы назначаемое управляемое удостоверение_ или _пользователя назначаемое управляемое удостоверение_ (если **msiClientId** указан) и устанавливает соединение с помощью маркера доступа для выбранных. Если подключение установлено, вы увидите следующее сообщение:

```bash
You have successfully logged on as: <your MSI username>
```

## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Подключение с использованием режима проверки подлинности ActiveDirectoryIntegrated
С версии 6.4 Microsoft JDBC Driver добавлена поддержка проверки подлинности ActiveDirectoryIntegrated с использованием билета Kerberos на нескольких платформах (Windows, Linux и macOS).
Дополнительные сведения см. в разделе [билет Kerberos, установить на Windows, Linux и Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) для получения дополнительных сведений. Кроме того в Windows, sqljdbc_auth.dll может также использоваться для проверки подлинности ActiveDirectoryIntegrated с драйвером JDBC.

> [!NOTE]
>  Если вы используете более старую версию драйвера, установите этот флажок, [ссылку](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) для соответствующих зависимостей, которые требуются для использования этого режима проверки подлинности. 

Следующий пример иллюстрирует использование режима `authentication=ActiveDirectoryIntegrated`. Выполните этот пример компьютер присоединен к домену, включенный в федерацию с Azure Active Directory. Пользователь автономной базы данных, представляющий субъектом-Azure AD или одну из групп, членом которых вы являетесь, должен существовать в базе данных и должна иметь разрешение CONNECT. 

Перед построением и запуском примера, на клиентском компьютере (на котором, будут выполняться в примере), загрузите [библиотеки azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимости и включать их в путь сборки Java

Замените имя сервера или базы данных перед выполнением в примере имя сервера или базы данных в следующие строки:

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

Этот пример с использованием режима проверки подлинности ActiveDirectoryIntegrated:
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

Рассмотрение этого примера на клиентском компьютере автоматически использует ваш билет Kerberos и пароль не требуется. Если подключение установлено, вы увидите следующее сообщение:

```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Задать билет Kerberos в Windows, Linux и Mac

Необходимо настроить билет Kerberos, связывание с учетной записью домена Windows текущего пользователя. Ниже приведены Сводка ключевых шагов.

#### <a name="windows"></a>Windows
JDK поставляется с `kinit`, который можно использовать для получения TGT из центра распространения ключей (KDC) в домене присоединен компьютер, включенный в федерацию с Azure Active Directory.

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>Шаг 1. Получение билета предоставления билета
- **Запустите на**: Windows
- **Действие**:
  - Используйте команду `kinit username@DOMAIN.COMPANY.COM` для получения TGT из центра распространения КЛЮЧЕЙ, затем он предложит вам ввести пароль для домена.
  - Используйте `klist` для просмотра доступных билеты. При успешном выполнении kinit вы увидите, что запрос в службу krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

> [!NOTE]
>  Необходимо указать `.ini` файл с `-Djava.security.krb5.conf` для вашего приложения найти центр распространения КЛЮЧЕЙ.

#### <a name="linux-and-mac"></a>Linux и Mac

##### <a name="requirements"></a>Требования
Доступ к машине присоединенных к домену Windows и запрашивать в контроллере домена Kerberos.

##### <a name="step-1-find-kerberos-kdc"></a>Шаг 1. Найти центр распространения КЛЮЧЕЙ Kerberos
- **Запустите на**: командной строки Windows
- **Действие**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (где «DOMAIN.COMPANY.COM» сопоставляет имя вашего домена)
- **Образец вывода**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **Сведения для извлечения** назовите контроллер домена, в этом случае `co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>Этап 2. Настройка контроллера Kerberos-домена в krb5.conf
- **Запустите на**: Linux и Mac
- **Действие**: Измените /etc/krb5.conf в редакторе по своему усмотрению. Настройте следующие ключи
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  Затем сохраните файл krb5.conf и выхода

> [!NOTE]
>  Домен должен быть прописными буквами.

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>Шаг 3. Тестирования получения билета предоставления билета
- **Запустите на**: Linux и Mac
- **Действие**:
  - Используйте команду `kinit username@DOMAIN.COMPANY.COM` для получения TGT из центра распространения КЛЮЧЕЙ, затем он предложит вам ввести пароль для домена.
  - Используйте `klist` для просмотра доступных билеты. При успешном выполнении kinit вы увидите, что запрос в службу krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Подключение с использованием режима аутентификации ActiveDirectoryPassword
Следующий пример иллюстрирует использование режима `authentication=ActiveDirectoryPassword`.

Перед построением и запуском примера:
1.  На клиентском компьютере (на котором, будут выполняться в примере), загрузите [библиотеки azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимости и включать их в путь сборки Java
2.  Найдите следующие строки кода и заменить имя сервера или базы данных с именем вашего сервера или базы данных.
    ```java
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  Найдите следующие строки кода и замените имя пользователя, имя пользователя AAD, который вы хотите подключиться от имени.
    ```java
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

Этот пример с использованием режима аутентификации ActiveDirectoryPassword:
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
Если соединение установлено, вы увидите следующее сообщение как выходные данные:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Должен существовать в базе данных автономного пользователя и пользователя автономной базы данных, представляющий указанный пользователем Azure AD или одной из групп, указанного Azure AD пользователь принадлежит, должен существовать в базе данных и должна иметь разрешение CONNECT (за исключением Azure Active Directory Администратор сервера или группы)

## <a name="connecting-using-access-token"></a>Подключение с использованием маркера доступа
Приложения и службы можно получить маркер доступа из Azure Active Directory и использовать ее для подключения к хранилищу данных базы данных SQL Azure.

> [!NOTE] 
> **accessToken** можно задать только с помощью параметра свойства getConnection() метода в классе диспетчер драйверов. Он не может использоваться в строке подключения.

В приведенном ниже примере имеется простое приложение Java, который подключается к базе данных или хранилище данных SQL с использованием проверки подлинности на основе маркеров доступа. Перед построением и запуском примера, выполните следующие действия:
1.  Создайте учетную запись приложения в Azure Active Directory для службы.
    1. Войдите на портал Azure.
    2. На панели навигации слева щелкните Azure Active Directory.
    3. Перейдите на вкладку «Регистрация приложений».
    4. В панели нажмите кнопку «Регистрация нового приложения».
    5. Введите понятное имя для приложения mytokentest, выберите «веб-приложение или API».
    6. Мы не требуется URL-адрес входа. Просто укажите ничего: "https://mytokentest«.
    7. Нажмите кнопку «Создать» в нижней.
    9. Хотя по-прежнему на портале Azure, перейдите на вкладку «Параметры» вашего приложения и перейдите на вкладку «Свойства».
    10. Найдите значение «Application ID» (то есть идентификатор клиента) и скопируйте его, потребуется позже при настройке приложения (например, 1846943b-ad04-4808-aa13-4702d908b5c1). См. в разделе следующего моментального снимка.
    11. В разделе «Ключи» создайте ключ, заполнив поле имя, выбрав продолжительность ключа и сохранения конфигурации (оставьте пустым поле значения). После сохранения поле значение должно быть заполнено автоматически, скопируйте созданное значение. Это секрет клиента.
    12. На левой панели щелкните Azure Active Directory. В разделе «Регистрация приложений» найдите вкладку «Конечные точки». Скопируйте URL-адрес в разделе «OATH конечная точка МАРКЕРА 2.0» — это URL-адрес службы маркеров безопасности.
    
    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Войдите в базу данных сервера SQL Azure как администратор Azure Active Directory и пользователь автономной базы данных с помощью подготовки команды T-SQL, для основного приложения. Дополнительные сведения см. в разделе [подключение к базе данных SQL или SQL данные хранилища с помощью аутентификации Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/) Дополнительные сведения о создании администратора Azure Active Directory и пользователь автономной базы данных.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  На клиентском компьютере (на котором, будут выполняться в примере), загрузите [azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) библиотеки и его зависимости и включать их в путь сборки Java. Обратите внимание на то, что azure-activedirectory-library-for-java требуется только для выполнения этого конкретного примера. В примере используется API-интерфейсы из этой библиотеки для получения маркера доступа из Azure AAD. Если у вас уже есть маркер доступа, этот шаг можно пропустить. Обратите внимание на то, что необходимо удалить в разделе в пример, который получает маркер доступа.

В следующем примере замените URL-адрес службы маркеров безопасности, идентификатор клиента, секрет клиента, сервера и базы данных имя значения.

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

Если подключение установлено успешно, вы увидите следующее сообщение как выходные данные:

```bash
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
