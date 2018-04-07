---
title: Подключение с использованием проверки подлинности Azure Active Directory | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.technology:
- drivers
ms.topic: article
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: ed4b2623b7a80358622b8153d316428b742ef31e
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Подключение с использованием проверки подлинности Azure Active Directory

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Это статье содержатся сведения о разработке приложений Java, чтобы использовать функцию проверки подлинности Azure Active Directory с Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server.

Можно использовать проверку подлинности Azure Active Directory (AAD), который представляет собой механизм подключения к базе данных SQL Azure версии 12 с использованием удостоверения в Azure Active Directory. Используйте проверку подлинности Azure Active Directory для централизованного управления удостоверениями пользователей базы данных и в качестве альтернативы проверке подлинности SQL Server. Драйвер JDBC можно указать учетные данные Azure Active Directory в строке подключения JDBC для подключения к базе данных SQL Azure. Сведения о настройке проверки подлинности Azure Active Directory [подключение к SQL базы данных с использованием Azure Active Directory проверки подлинности](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/). 

Для поддержки проверки подлинности Azure Active Directory были добавлены два новых свойства подключения:
*   **Проверка подлинности**: используйте это свойство, чтобы указать, какой метод проверки подлинности SQL для подключения. Возможными значениями являются: **ActiveDirectoryIntegrated**, **ActiveDirectoryPassword**, **SqlPassword**и значение по умолчанию **NotSpecified**.
    * Использовать ' authentication = ActiveDirectoryIntegrated "для подключения к базе данных SQL, используя встроенную проверку подлинности Windows. Чтобы использовать этот режим проверки подлинности, необходимо создать федерацию локального федерации Active Directory Services (ADFS) с Azure AD в облаке. После этого настроена и билет Kerberos, становятся доступными базу данных SQL Azure без необходимости вводить учетные данные при входе в компьютер присоединен к домену. 
    * Используйте ' authentication = ActiveDirectoryPassword "для подключения к базе данных SQL с помощью Azure AD основное имя и пароль.
    * Использовать ' authentication = SqlPassword "для подключения к SQL Server, с помощью свойств пользователе или имя пользователя и пароль.
    * Использовать ' authentication = не указан "или оставьте значения по умолчанию, когда ни один из этих методов проверки подлинности необходимы.

*   **accessToken**: это свойство используется для подключения к базе данных SQL с помощью маркера доступа. accessToken можно задать только с помощью свойства параметра метода getConnection() класса DriverManager. Он не может использоваться в URL-АДРЕСЕ соединения.  

Подробные сведения см. свойство проверки подлинности на [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md) страницы.  


## <a name="client-setup-requirements"></a>Требования к установке клиента
Убедитесь, что на клиентском компьютере установлены следующие компоненты:
* Java 7 или более поздней версии
*   Драйвер Microsoft JDBC Driver 6.0 (или более поздней версии) для SQL Server
*   Если вы используете режим проверки подлинности на основе маркеров доступа, необходимо [azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимости, для выполнения примеров в данной статье. Дополнительные сведения см. в разделе **подключение с помощью токена доступа** раздела.
*   Если вы используете ActiveDirectoryPassword режим проверки подлинности, необходимо [azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимости. Дополнительные сведения см. в разделе **подключении с использованием режима проверки подлинности ActiveDirectoryPassword** раздела.
*   При использовании режима ActiveDirectoryIntegrated требуется azure-activedirectory библиотека for-java и его зависимости. Дополнительные сведения см. в разделе **подключении с использованием режима проверки подлинности ActiveDirectoryIntegrated** раздела.
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>Подключение с использованием режима проверки подлинности ActiveDirectoryIntegrated
 С помощью версии 6.4 драйвера JDBC добавляет поддержку для ActiveDirectoryIntegrated проверки подлинности с использованием билета Kerberos для нескольких платформ (Windows, Linux и Mac).
В разделе [билет Kerberos, задайте в Windows, Linux и Mac](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) для получения дополнительных сведений. Кроме того в Windows, sqljdbc_auth.dll может также использоваться для проверки подлинности ActiveDirectoryIntegrated с драйвером JDBC.

> [!NOTE]
>  Если вы используете старую версию драйвера, установите этот флажок, [ссылку](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) для соответствующих зависимостей, которые требуются для использования этого режима проверки подлинности. 

Приведенный ниже показано, как использовать ' authentication = ActiveDirectoryIntegrated "режим. Этот пример можно выполнить на компьютер присоединен к домену, который входит в федерацию с Azure Active Directory. Пользователь автономной базы данных, представляющий на основном Azure AD или одной из групп, вам принадлежит, должен существовать в базе данных и должна иметь разрешение CONNECT. 

Перед построением и запуском примера на клиентском компьютере (на котором, вы хотите запустить в примере), загрузите [библиотеки azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) и его зависимостей и включать их в путь построения Java

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
Выполнение этого примера на клиентском компьютере автоматически использует ваш билета Kerberos и пароль не требуется. Если подключение установлено, появится следующее сообщение:
```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Задать билет Kerberos в Windows, Mac и Linux

Необходимо настроить билет Kerberos, связывание текущего пользователя с учетной записью домена Windows. Ниже приведены Сводка ключевых шагов.

#### <a name="windows"></a>Windows
JDK поставляется с `kinit` которому можно использовать для получения TGT из центра распространения КЛЮЧЕЙ (центр распространения ключей) в домене соединение машины, которая включена в федерацию с Azure Active Directory.

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>Шаг 1: Получение билет предоставления билета
- **Запустите на**: Windows
- **Действие**:
  - Команда `kinit username@DOMAIN.COMPANY.COM` Чтобы получить БИЛЕТ предоставления билета KDC, затем он предложит ввести пароль для домена.
  - Используйте `klist` для просмотра доступных билетов. При успешном выполнении kinit, вы увидите, что билет krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

> [!NOTE]
>  Необходимо указать `.ini` файл с `-Djava.security.krb5.conf` для вашего приложения найти центр распространения КЛЮЧЕЙ.

#### <a name="linux-and-mac"></a>Linux и Mac

##### <a name="requirements"></a>Требования
Доступ к компьютером присоединенных к домену Windows, чтобы выполнять запросы к контроллеру домена Kerberos

##### <a name="step-1-find-kerberos-kdc"></a>Шаг 1: Найти центр распространения КЛЮЧЕЙ Kerberos
- **Запустите на**: командной строки Windows
- **Действие**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (где «DOMAIN.COMPANY.COM» сопоставляет имя вашего домена)
- **Образец вывода**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **Сведения для извлечения** имя контроллера домена, в этом случае `co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>Шаг 2: Настройка KDC в krb5.conf
- **Запустите на**: Linux или Mac
- **Действие**: изменение /etc/krb5.conf в редакторе по своему усмотрению. Настройте следующие ключи
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  Затем сохраните файл krb5.conf и выход

> [!NOTE]
>  Домен должен быть в прописными буквами.

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>Шаг 3: Проверка получения билета предоставления билета
- **Запустите на**: Linux или Mac
- **Действие**:
  - Команда `kinit username@DOMAIN.COMPANY.COM` Чтобы получить БИЛЕТ предоставления билета KDC, затем он предложит ввести пароль для домена.
  - Используйте `klist` для просмотра доступных билетов. При успешном выполнении kinit, вы увидите, что билет krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.

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
Если соединение установлено, в качестве выходных данных должны появиться следующее сообщение:
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> Пользователь автономной базы данных должен существовать и пользователя автономной базы данных, представляющий указанный пользователя Azure AD или одной из групп, указанной Azure принадлежит пользователя AD, должен существовать в базе данных и должен иметь разрешение на ПОДКЛЮЧЕНИЕ (за исключением Azure Active Directory Администратор сервера или группы)


## <a name="connecting-using-access-token"></a>Подключение с помощью токена доступа
Приложений и служб можно получить маркер доступа из Azure Active Directory и используйте его для подключения к базе данных SQL Azure. Обратите внимание, что accessToken можно задать только с помощью свойства параметра метода getConnection() класса DriverManager. Он не может использоваться в строке подключения.
 
В приведенном ниже примере содержит простое приложение Java, которое подключается к базе данных SQL Azure с помощью проверки подлинности на основе маркера доступа. Перед построением и запуском примера, выполните следующие действия:
1.  Создайте учетную запись приложения в Azure Active Directory для службы.
    1. Войдите в портал управления Azure
    2. В панели навигации слева щелкните Azure Active Directory
    3. Перейдите на вкладку «Регистрация приложения».
    4. В ящике нажмите кнопку «Регистрация нового приложения».
    5. Введите понятное имя для приложения mytokentest, выберите «веб-приложения и API».
    6. URL-адрес входа не требуется. Дайте ничего: «http://mytokentest».
    7. Нажмите кнопку «Создать» в нижней.
    9. Хотя по-прежнему на портале Azure на вкладке «Параметры», приложения и откройте вкладку «Свойства».
    10. Найти значение «Идентификатор приложения» (также НАЗЫВАЕМОГО идентификатор клиента) и скопируйте его, потребуется позднее при настройке приложения (например, 1846943b-ad04-4808-aa13-4702d908b5c1). См. в следующем моментальном снимке.
    11. Найти значение «URL-адрес идентификатор приложения» и скопируйте его, это URL-адрес службы маркеров безопасности.
    12. В разделе «Ключи» создайте ключ, заполнив поля «имя», выбрав длительность ключа и сохранения конфигурации (оставьте пустым поле значения). После сохранения, значение поля должно иметь заполняется автоматически, скопируйте сформированное значение. Это секрет клиента.

    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Войдите на сервер SQL Azure пользовательской базы данных как администратора Azure Active Directory и пользователь автономной базы данных с помощью резервов команды T-SQL, для основного приложения. В разделе [подключение к базе данных SQL или SQL данные хранилища с использованием Azure Active Directory проверки подлинности](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/) Дополнительные сведения о создании администратора Azure Active Directory и пользователь автономной базы данных.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  На клиентском компьютере (на котором, вы хотите запустить в примере), загрузите [azure-activedirectory библиотека for-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) библиотеки и ее зависимости и включать их в путь построения Java. Обратите внимание, что azure-activedirectory библиотека for-java требуется только для запуска этот конкретный пример, как оно использует API-интерфейсы из этой библиотеки для получения токена доступа из Azure AD. Если уже имеется маркер доступа, этот шаг можно пропустить. Обратите внимание, что необходимо удалить раздел в примере, который получает маркер доступа.

В следующем примере замените имя URL-адрес службы маркеров безопасности, идентификатор клиента, секрет клиента, сервера и базы данных значения.

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
        String stsurl = "https://microsoft.onmicrosoft.com/..."; // Replace with your STS URL.
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
