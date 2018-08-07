---
title: Соединение с использованием проверки подлинности Azure Active Directory | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c86fc615bcf3dec2a87581bbb09f482c8befc943
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/02/2018
ms.locfileid: "39452648"
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Соединение с использованием проверки подлинности Azure Active Directory

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В этой статье сведения о том, как разрабатывать приложения Java, чтобы использовать функцию проверки подлинности Azure Active Directory с Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.

Можно использовать проверку подлинности Azure Active Directory (AAD), который представляет собой механизм подключения к базе данных SQL Azure версии 12 с помощью удостоверений в Azure Active Directory. Проверка подлинности Azure Active Directory используется для централизованного управления удостоверениями пользователей базы данных и в качестве альтернативы проверке подлинности SQL Server. Драйвер JDBC можно указать учетные данные Azure Active Directory в строке подключения JDBC для подключения к базе данных SQL Azure. Сведения о том, как настроить проверку подлинности Azure Active Directory [подключение к SQL базы данных с помощью аутентификации Azure Active Directory](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Для поддержки проверки подлинности Azure Active Directory были добавлены два новых свойства подключения:
*   **Проверка подлинности**: это свойство используется, чтобы указать, какой метод проверки подлинности SQL для подключения. Возможными значениями являются: **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword**и значение по умолчанию **NotSpecified**.
    * Используйте "Проверка подлинности = ActiveDirectoryIntegrated" для подключения к базе данных SQL, используя встроенную проверку подлинности Windows. Чтобы использовать этот режим проверки подлинности, необходимо создать федерацию локальной федерации Active Directory Services (ADFS) с помощью AAD в облаке. После это можно сделать и билет Kerberos, становятся доступными базы данных SQL Azure, не вводя учетные данные при входе в компьютер присоединен к домену. 
    * Используйте "Проверка подлинности = ActiveDirectoryPassword" для подключения к базе данных SQL с помощью имени участника Azure AD и пароль.
    * Используйте "Проверка подлинности = SqlPassword" для подключения к SQL Server, с помощью свойств имени пользователя или пользователя и пароль.
    * Используйте "Проверка подлинности = NotSpecified" или оставьте значение по умолчанию, когда ни один из этих методов проверки подлинности необходимы.

*   **accessToken**: это свойство используется для подключения к базе данных SQL с помощью маркера доступа. accessToken может устанавливаться только с помощью параметра свойства getConnection() метода в классе диспетчер драйверов. Он не может использоваться в URL-АДРЕСЕ соединения.  

Дополнительные сведения см. в разделе свойство проверки подлинности на [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) страницы.  


## <a name="client-setup-requirements"></a>Требования к установке клиента
Убедитесь, что на клиентском компьютере установлены следующие компоненты:
* Java 7 или более поздней версии
*   Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server
*   Если вы используете режим проверки подлинности на основе маркеров доступа, необходимо [azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимостей для выполнения примеров из этой статьи. Дополнительные сведения см. в разделе **подключение с использованием токена доступа** раздел.
*   При использовании режима аутентификации ActiveDirectoryPassword необходимо [azure-activedirectory-library-for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимости. Дополнительные сведения см. в разделе **подключение с использованием режима аутентификации ActiveDirectoryPassword** раздел.
*   Если вы используете режим ActiveDirectoryIntegrated, требуется azure-activedirectory-library-for-java и его зависимости. Дополнительные сведения см. в разделе **подключение с использованием режима проверки подлинности ActiveDirectoryIntegrated** раздел.
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Подключение с использованием режима проверки подлинности ActiveDirectoryIntegrated
 С версии 6.4 Microsoft JDBC Driver добавлена поддержка проверки подлинности ActiveDirectoryIntegrated с использованием билета Kerberos на нескольких платформах (Windows/Linux и Mac).
Дополнительные сведения см. в разделе [билет Kerberos, установить на Windows, Linux и Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) для получения дополнительных сведений. Кроме того в Windows, sqljdbc_auth.dll может также использоваться для проверки подлинности ActiveDirectoryIntegrated с драйвером JDBC.

> [!NOTE]
>  Если вы используете более старую версию драйвера, установите этот флажок, [ссылку](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) для соответствующих зависимостей, которые требуются для использования этого режима проверки подлинности. 

В следующем примере показано, как использовать "Проверка подлинности = ActiveDirectoryIntegrated" режим. Выполните этот пример компьютер присоединен к домену, включенный в федерацию с Azure Active Directory. Пользователя автономной базы данных, представляющий субъектом-Azure AD или одну из групп, вам принадлежит, должен существовать в базе данных и должна иметь разрешение CONNECT. 

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
        ds.setHostNameInCertificate("*.database.windows.net");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {
            
            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
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

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>Шаг 1: Получение билета предоставления билета
- **Запустите на**: Windows
- **Действие**:
  - Используйте команду `kinit username@DOMAIN.COMPANY.COM` для получения TGT из центра распространения КЛЮЧЕЙ, затем он предложит вам ввести пароль для домена.
  - Используйте `klist` для просмотра доступных билеты. При успешном выполнении kinit вы увидите, что запрос в службу krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

> [!NOTE]
>  Необходимо указать `.ini` файл с `-Djava.security.krb5.conf` для вашего приложения найти центр распространения КЛЮЧЕЙ.

#### <a name="linux-and-mac"></a>Linux и Mac

##### <a name="requirements"></a>Требования
Доступ к машине присоединенных к домену Windows и запрашивать в контроллере домена Kerberos.

##### <a name="step-1-find-kerberos-kdc"></a>Шаг 1: Поиск центра распространения КЛЮЧЕЙ Kerberos
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

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>Шаг 2: Настройка KDC в krb5.conf
- **Запустите на**: Linux и Mac
- **Действие**: изменение /etc/krb5.conf в редакторе по своему усмотрению. Настройте следующие ключи
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

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>Шаг 3: Проверка получения билета предоставления билета
- **Запустите на**: Linux и Mac
- **Действие**:
  - Используйте команду `kinit username@DOMAIN.COMPANY.COM` для получения TGT из центра распространения КЛЮЧЕЙ, затем он предложит вам ввести пароль для домена.
  - Используйте `klist` для просмотра доступных билеты. При успешном выполнении kinit вы увидите, что запрос в службу krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Подключение с использованием режима аутентификации ActiveDirectoryPassword
В следующем примере показано, как использовать "Проверка подлинности = ActiveDirectoryPassword" режим.

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
        ds.setHostNameInCertificate("*.database.windows.net");
        
        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {
            
            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
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
Приложения и службы можно получить маркер доступа из Azure Active Directory и использовать ее для подключения к базе данных SQL Azure.

> [!NOTE] 
> **accessToken** можно задать только с помощью параметра свойства getConnection() метода в классе диспетчер драйверов. Он не может использоваться в строке подключения.

В приведенном ниже примере содержит простое приложение Java, которое подключается к базе данных SQL Azure с использованием проверки подлинности на основе маркеров доступа. Перед построением и запуском примера, выполните следующие действия:
1.  Создайте учетную запись приложения в Azure Active Directory для службы.
    1. Войдите на портал Azure.
    2. На панели навигации слева щелкните Azure Active Directory.
    3. Перейдите на вкладку «Регистрация приложений».
    4. В панели нажмите кнопку «Регистрация нового приложения».
    5. Введите понятное имя для приложения mytokentest, выберите «веб-приложение или API».
    6. Мы не требуется URL-адрес входа. Просто укажите ничего: "http://mytokentest«.
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
        ds.setHostNameInCertificate("*.database.windows.net");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {

            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
``` 

Если подключение установлено успешно, вы увидите следующее сообщение как выходные данные:
```java
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
