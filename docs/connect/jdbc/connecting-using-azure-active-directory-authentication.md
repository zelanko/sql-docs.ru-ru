---
title: "Подключение с использованием проверки подлинности Azure Active Directory | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.topic: article
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 83d5ad3bae131b58dd344c3f5f9bfc7f5d0c4f5a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-using-azure-active-directory-authentication"></a>Подключение с использованием проверки подлинности Azure Active Directory
Это статье содержатся сведения о разработке приложений Java, чтобы использовать функцию проверки подлинности Azure Active Directory с Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.

Начиная с Microsoft JDBC Driver 6.0 для SQL Server, можно использовать проверки подлинности Active Direcoty Azure (AAD), который представляет собой механизм подключения к базе данных SQL Azure версии 12 с использованием удостоверения в Azure Active Directory. Используйте проверку подлинности Azure Active Directory для централизованного управления удостоверениями пользователей базы данных и в качестве альтернативы проверке подлинности SQL Server. Драйвер JDBC 6.0 (или более поздней версии) позволяет указать учетные данные Azure Active Directory в строке подключения JDBC для подключения к базе данных SQL Azure. Сведения о настройке проверки подлинности Azure Active Directory [подключение к SQL базы данных с использованием Azure Active Directory проверки подлинности](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Для поддержки проверки подлинности Azure Active Directory были добавлены два новых свойства подключения:
*   **Проверка подлинности**: используйте это свойство, чтобы указать, какой метод проверки подлинности SQL для подключения. Возможными значениями являются: **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword** и значение по умолчанию **NotSpecified** .
    * Использовать ' authentication = ActiveDirectoryIntegrated "для подключения к базе данных SQL, используя встроенную проверку подлинности Windows. Чтобы использовать этот режим проверки подлинности, необходимо создать федерацию локального федерации Active Directory Services (ADFS) с Azure AD в облаке. После установки, можно получить доступ к базе данных SQL Azure без необходимости вводить ceredentials при входе в компьютер присоединен к домену. 
    * Используйте ' authentication = ActiveDirectoryPassword "для подключения к базе данных SQL с помощью Azure AD основное имя и пароль.
    * Использовать ' authentication = SqlPassword "для подключения к SQL Server, с помощью свойств пользователе или имя пользователя и пароль.
    * Используйте ' authentication = не указан "или оставьте его значения по умолчанию, если ни один из этих методов проверки подлинности необходимо.

*   **accessToken**: это свойство используется для подключения к базе данных SQL с помощью маркера доступа. accessToken можно задать только с помощью свойства параметра метода getConnection() класса DriverManager. Он не может использоваться в URL-АДРЕСЕ соединения.  

Подробные сведения см. свойство проверки подлинности на [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) страницы.  


## <a name="client-setup-requirements"></a>Требования к установке клиента
Убедитесь, что на клиентском компьютере установлены следующие компоненты:
* Java 7 или более поздней версии
*   Драйвер Microsoft JDBC Driver 6.2 (или более поздней версии) для SQL Server
*   Если вы используете режим токена проверки подлинности на основе доступа, необходимо будет [azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимости, для выполнения примеров в данной статье. В разделе **подключение с помощью токена доступа** более подробные сведения.
*   При использовании режима проверки подлинности ActiveDirectoryPassword потребуется [azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимости. В разделе **подключении с использованием режима проверки подлинности ActiveDirectoryPassword** более подробные сведения.
*   Если вы используете режим ActiveDirectoryIntegrated, необходимо установить библиотеку аутентификации Active Directory для SQL Server (ADALSQL. Библиотека DLL) и sqljdbc_auth.dll.
    * ADALSQL. Библиотека DLL позволяет проверять подлинность приложений в базе данных SQL Microsoft Azure с помощью Azure Active Directory. Загрузка библиотеки DLL из [библиотека проверки подлинности Microsoft Active Directory для Microsoft SQL Server](http://www.microsoft.com/en-us/download/details.aspx?id=48742)
    * Для ADALSQL. Библиотека DLL два двоичных версиях X86- и X64 доступны для загрузки. Если установлена неправильная версия двоичный или если отсутствует библиотека DLL, в драйвере возникнет следующая ошибка: «не удалось загрузить adalsql.dll (Authentication =...). Код ошибки: 0x2.». В этом случае загрузите нужную версию ADALSQL. БИБЛИОТЕКИ DLL. 
    * sqljdbc_auth.dll доступен в пакете драйверов. Скопируйте файл sqljdbc_auth.dll в каталог в пути системы Windows на компьютере, где установлен драйвер JDBC. Или можно задать системное свойство java.libary.path для указания каталога, в котором содержится файл sqljdbc_auth.dll. 
    * При использовании 64-разрядной виртуальной машины и процессора x64 используйте файл sqljdbc_auth.dll в папке x64. 
    * При использовании 32-разрядной виртуальной машины Java (JVM) следует использовать файл sqljdbc_auth.dll в папке x86 folder, даже если используется операционная система x64. 
    * Например если вы используете 32-разрядной виртуальной машины Java и JDBC драйвера в каталог по умолчанию, можно указать расположение библиотеки DLL с помощью следующий аргумент виртуальной машины (VM) при запуске приложения Java:  
        ```
        -Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86
        ```
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Подключение с использованием режима проверки подлинности ActiveDirectoryIntegrated
Приведенный ниже показано, как использовать ' authentication = ActiveDirectoryIntegrated "режим. Этот пример можно выполнить на компьютер присоединен к домену, который входит в федерацию с Azure Active Directory. Пользователь автономной базы данных, представляющий на основном Azure AD или одной из групп, вам принадлежит, должен существовать в базе данных и должна иметь разрешение CONNECT. 
    
Замените имя сервера и базы данных перед выполнением в примере имя сервера или базы данных в следующих строках:

```
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

Этот пример с использованием режима проверки подлинности ActiveDirectoryIntegrated:
```
import java.sql.Connection;
import java.sql.ResultSet;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class IntegratedExample {

    public static void main(String[] args) throws Exception {
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");
        ds.setHostNameInCertificate("*.database.windows.net");

        Connection connection = ds.getConnection();

        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
```
Выполнение данного примера на компьютере, присоединенных к домену, который входит в федерацию с Azure Active Directory будут автоматически использовать учетные данные Windows и пароль не требуется. Если соединение установлено, появится следующее сообщение:
```
You have successfully logged on as: <your domain user name>
```

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>Подключение с использованием режима проверки подлинности ActiveDirectoryPassword
Приведенный ниже показано, как использовать ' authentication = ActiveDirectoryPassword "режим.

Перед построением и запуском примера:
1.  На клиентском компьютере (на котором, вы хотите запустить в примере), загрузите [библиотеки azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимостей и включать их в путь построения Java
2.  Найдите следующие строки кода и введите имя сервера или базы данных имя базы данных сервера.
    ```
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  Найдите следующие строки кода и замените имя пользователя, имя пользователя Azure AD, который вы хотите подключиться от имени.
    ```
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

Этот пример с использованием режима проверки подлинности ActiveDirectoryPassword:
```
import java.sql.Connection;
import java.sql.ResultSet;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class UserPasswordExample {
    
    public static void main(String[] args) throws Exception{
        SQLServerDataSource ds = new SQLServerDataSource();
        
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        ds.setHostNameInCertificate("*.database.windows.net");
        
        Connection connection = ds.getConnection();
        
        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
```
Если соединение установлено, появится следующее сообщение в качестве выходных данных:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Пользователь автономной базы данных должен существовать и пользователя автономной базы данных, представляющий указанный пользователя Azure AD или одной из групп, указанной Azure пользователя AD принадлежит, должен существовать в базе данных и должен иметь разрешение на ПОДКЛЮЧЕНИЕ (за исключением Azure Active Directory Администратор сервера или группы)


## <a name="connecting-using-access-token"></a>Подключение с помощью токена доступа
Приложений и служб можно получить маркер доступа из Azure Active Directory и используйте его для подключения к базе данных SQL Azure. Обратите внимание, что accessToken можно задать только с помощью свойства параметра метода getConnection() класса DriverManager. Он не может использоваться в строке подключения.
 
В приведенном ниже примере содержит простое приложение Java, которое подключается к базе данных SQL Azure с помощью проверки подлинности на основе токена доступа. Перед построением и запуском примера, выполните следующие действия:
1.  Создайте учетную запись приложения в Azure Active Directory для службы.
    1. Войдите в портал управления Azure
    2. В панели навигации слева щелкните Azure Active Directory
    3. Щелкните клиент каталога, которую вы хотите зарегистрировать образца приложения. Это должен быть том же каталоге, который связан с базой данных (сервер размещения базы данных).
    4. Щелкните вкладку "приложения".
    5. В ящике нажмите кнопку "Добавить".
    6. Нажмите кнопку «Добавить приложение, разрабатываемое моей организацией».
    7. Введите mytokentest как понятное имя для приложения, выберите «Веб-приложение и/или Web API» и нажмите кнопку Далее.
    8. При условии, что это приложение является управляющей программы или службы и не веб-приложения, оно не содержит знак в URL-адрес или URI идентификатора приложения. Для этих двух полей введите http://mytokentest
    9. Хотя по-прежнему на портале Azure на вкладке Настройка приложения
    10. Найдите значение идентификатора клиента и скопируйте его, он потребуется позже при настройке приложения (т. е.  a4bbfe26-dbaa-4fec-8ef5-223d229f647d). См. ниже моментального снимка.
    11. В разделе «Ключи» выберите длительность ключ, сохранить конфигурацию и скопируйте ключ для последующего использования. Это секрет клиента.
    12. Внизу щелкните «Просмотреть конечные точки» и скопируйте URL-адрес в разделе «ENDPOINT АВТОРИЗАЦИИ OAUTH 2.0» для последующего использования. Это URL-адрес службы маркеров безопасности.


![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)


2. Войдите в пользовательской базе данных сервера SQL Azure, как администратора Azure Active Directory и пользователь автономной базы данных с помощью резервов команды T-SQL, для вашего приложения субъекта. В разделе [подключение к базе данных SQL или SQL данные хранилища с использованием Azure Active Directory проверки подлинности](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/) Дополнительные сведения о создании администратора Azure Active Directory и пользователь автономной базы данных.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  На клиентском компьютере (на котором, вы хотите запустить в примере), загрузите [azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) библиотеки и ее зависимости и включать их в путь построения Java. Обратите внимание, что azure-activedirectory библиотека for-java требуется только для запуска этот конкретный пример, как оно использует API-интерфейсы из этой библиотеки для получения токена доступа из Azure AD. Если уже имеется маркер доступа, этот шаг можно пропустить. Обратите внимание, что также будет необходимо удалить раздел в примере, который получает маркер доступа.

В следующем примере замените STS URL-адрес, идентификатор клиента, секрет клиента, сервера и имя базы данных с помощью этих значений.

```
import java.sql.Connection;
import java.sql.ResultSet;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD. 
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;


public class TokenBasedExample {

    public static void main(String[] args) throws Exception{

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
        String clientId = "a4bbfe26-dbaa-4fec-8ef5-223d229f647d"; // Replace with your client ID.
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

        Connection connection = ds.getConnection();

        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
``` 

Если соединение установлено успешно, появится следующее сообщение в качестве выходных данных:
```
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
