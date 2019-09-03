---
title: Использование Azure Active Directory с драйвером ODBC | Документация Майкрософт для SQL Server
ms.custom: ''
ms.date: 11/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c0f9d73dace4e17d87e1c93da703786fc920b2fb
ms.sourcegitcommit: 3b1f873f02af8f4e89facc7b25f8993f535061c9
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/30/2019
ms.locfileid: "70176166"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Использование Azure Active Directory с драйвером ODBC
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Назначение

Microsoft ODBC Driver for SQL Server с версией 13,1 или выше позволяет приложениям ODBC подключаться к экземпляру SQL Azure с помощью федеративного удостоверения в Azure Active Directory с именем пользователя и паролем, маркером доступа Azure Active Directory, Azure Active Управляемое удостоверение службы каталогов или встроенная проверка подлинности Windows (_только для драйверов Windows_). Для драйвера ODBC версии 13,1 Azure Active Directory проверки подлинности маркера доступа является _только Windows_. Драйвер ODBC версии 17 и выше поддерживает эту проверку подлинности на всех платформах (Windows, Linux и Mac). В драйвере ODBC версии 17,1 для Windows введена новая Azure Active Directoryная Интерактивная проверка подлинности с ИДЕНТИФИКАТОРом входа. Новый метод проверки подлинности управляемого удостоверения службы Azure Active Directory был добавлен в драйвер ODBC версии 17.3.1.1 для назначенных системой и назначенных пользователю удостоверений. Все эти действия выполняются с помощью новых ключевых слов DSN и строк подключения, а также атрибутов соединения.

> [!NOTE]
> Драйвер ODBC в Linux и macOS не поддерживает службы федерации Active Directory (AD FS). Если вы используете Azure Active Directory проверку имени пользователя и пароля из клиента Linux или macOS, а конфигурация Active Directory включает федеративные службы, проверка подлинности может завершиться ошибкой.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Новые и/или измененные ключевые слова DSN и строки подключения

`Authentication` Ключевое слово можно использовать при соединении с именем DSN или строкой подключения для управления режимом проверки подлинности. Значение, заданное в строке соединения, переопределяет указанное в DSN имя, если оно предоставлено. Значение`Authentication` _предварительного атрибута_ параметра — это значение, вычисленное на основе строки подключения и значений DSN.

|Имя|Значения|По умолчанию|Описание|
|-|-|-|-|
|`Authentication`|(не задано), (пустая строка `SqlPassword`) `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`,,,`ActiveDirectoryMsi` |(не задано)|Управляет режимом проверки подлинности.<table><tr><th>Значение<th>Описание<tr><td>(не задано)<td>Режим проверки подлинности определяется другими ключевыми словами (существующие параметры устаревшего соединения).<tr><td>(пустая строка)<td>Справка по строке подключения Переопределение и `Authentication` удаление значения, заданного в имени DSN.<tr><td>`SqlPassword`<td>Выполнить прямую проверку подлинности в экземпляре SQL Server с помощью имени пользователя и пароля.<tr><td>`ActiveDirectoryPassword`<td>Проверка подлинности с помощью удостоверения Azure Active Directory с использованием имени пользователя и пароля.<tr><td>`ActiveDirectoryIntegrated`<td>_Только драйвер Windows_. Проверка подлинности с помощью удостоверения Azure Active Directory с использованием встроенной проверки подлинности.<tr><td>`ActiveDirectoryInteractive`<td>_Только драйвер Windows_. Проверка подлинности с помощью удостоверения Azure Active Directory с использованием интерактивной проверки подлинности.<tr><td>`ActiveDirectoryMsi`<td>Проверка подлинности с помощью удостоверения Azure Active Directory с использованием управляемого удостоверения службы. Для назначаемого пользователем удостоверения в качестве идентификатора пользователя указывается идентификатор объекта удостоверения пользователя.</table>|
|`Encrypt`|(не задано), `Yes`, `No`|(см. описание)|Управляет шифрованием соединения. Если значение `Authentication` параметра, предшествующее атрибуту, не равно _None_ в имени DSN или строке подключения, значение по умолчанию — `Yes`. В противном случае значение по умолчанию — `No`. Если атрибут `SQL_COPT_SS_AUTHENTICATION` переопределяет `Authentication`значение предварительного атрибута, явно задайте значение параметра Encryption в имени DSN или в строке подключения или атрибуте соединения. Значение шифрования, предшествующее атрибуту, `Yes` равно, если значение `Yes` установлено в DSN или в строке подключения.|

## <a name="new-andor-modified-connection-attributes"></a>Новые и/или измененные атрибуты соединения

Для поддержки Azure Active Directory проверки подлинности были введены или изменены следующие атрибуты подключения перед подключением. Если атрибут Connection имеет соответствующую строку соединения или ключевое слово DSN и задан, то приоритет имеет атрибут Connection.

|attribute|Тип|Значения|По умолчанию|Описание|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_AD_MSI`, `SQL_AU_RESET`|(не задано)|См. Описание `Authentication` ключевого слова выше. `SQL_AU_NONE`предоставляется для явного переопределения значения SET `Authentication` в имени DSN и (или) строки подключения, а также при `SQL_AU_RESET` отустановке атрибута, если он был задан, что позволяет использовать для имени DSN или строки подключения значение приоритета.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Указатель на `ACCESSTOKEN` или null|NULL|Если значение не равно null, указывает используемый маркер доступа AzureAD. Указание маркера доступа, а `UID`также ключевых слов строки `Authentication` подключения `Trusted_Connection`, `PWD`,, или их эквивалентных атрибутов является ошибкой. <br> **Примечание.** Драйвер ODBC версии 13,1 поддерживает только _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(см. описание)|Управляет шифрованием соединения. `SQL_EN_OFF`и `SQL_EN_ON` отключение и включение шифрования соответственно. Если значение `Authentication` параметра до атрибута не равно _None_ или `SQL_COPT_SS_ACCESS_TOKEN` задано и `Encrypt` не указано ни в имени DSN, ни в строке подключения, значение по умолчанию — `SQL_EN_ON`. В противном случае значение по умолчанию — `SQL_EN_OFF`. Если атрибут `SQL_COPT_SS_AUTHENTICATION` Connection имеет значение Not _None_, явно задайте `SQL_COPT_SS_ENCRYPT` требуемое значение, если `Encrypt` оно не было указано в DSN или строке подключения. Эффективное значение этого атрибута определяет [, будет ли использоваться шифрование для соединения.](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Не поддерживается в Azure Active Directory, так как изменения паролей в субъектах AAD не могут быть выполнены через соединение ODBC. <br><br>Истечение срока действия пароля для проверки подлинности SQL Server было введено в SQL Server 2005. Добавлен `SQL_COPT_SS_OLDPWD` атрибут, позволяющий клиенту предоставить старый и новый пароль для соединения. Если задано это свойство, поставщик не будет использовать пул соединений для первого и последующих соединений, поскольку строка подключения будет содержать «старый пароль», который уже изменен.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|Не _рекомендуется_; `SQL_AU_AD_INTEGRATED` вместо `SQL_COPT_SS_AUTHENTICATION` этого используйте параметр. <br><br>Принудительное использование проверки подлинности Windows (Kerberos в Linux и macOS) для проверки доступа при входе на сервер. При использовании проверки подлинности Windows драйвер не учитывает значения идентификатора пользователя и пароля, указанные в процессе `SQLConnect`обработки `SQLDriverConnect`, или `SQLBrowseConnect` .|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Дополнения пользовательского интерфейса для Azure Active Directory (только для драйверов Windows)

Дополнительные параметры, необходимые для использования проверки подлинности в Azure AD, дополнены дополнительными параметрами, необходимыми для установки имени DSN и пользовательского интерфейса подключения драйвера.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Создание и изменение имен DSN в пользовательском интерфейсе

При создании или изменении существующего имени DSN с помощью пользовательского интерфейса установки драйвера можно использовать новые варианты проверки подлинности Azure AD:

`Authentication=ActiveDirectoryIntegrated` для интегрированной аутентификации в SQL Azure с использованием Azure Active Directory

![CreateNewDSN_ADIntegrated. png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword`для Azure Active Directory проверку подлинности имени пользователя и пароля в SQL Azure

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` для интерактивной проверки подлинности Azure Active Directory в SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword`Проверка подлинности имени пользователя и пароля для SQL Server (Azure или иным способом)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes`для встроенной проверки подлинности Windows Legacy SSPI

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

`Trusted_Connection=Yes` Пять параметров соответствуют (существующая устаревшая встроенная проверка подлинности Windows SSPI `Authentication=` ) и `ActiveDirectoryPassword` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryInteractive`и соответственно.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect Prompt (только драйвер Windows)

Диалоговое окно приглашения, отображаемое SQLDriverConnect при запросе сведений, необходимых для завершения подключения, содержит три новых параметра для проверки подлинности Azure AD:

![ServerLogin.png](windows/ServerLogin.png)

Эти параметры соответствуют одному из пяти доступных в пользовательском интерфейсе установки DSN.

### <a name="example-connection-strings"></a>Примеры строк подключения
1. Проверка подлинности SQL Server-устаревший синтаксис. Сертификат сервера не проверяется, а шифрование используется только в том случае, если сервер применяет его. Имя пользователя и пароль передаются в строку подключения.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. Проверка подлинности SQL — новый синтаксис. Клиент запрашивает шифрование `Encrypt` (значение по умолчанию — `true`), а сертификат сервера проверяется независимо от параметра шифрования `true`(если `TrustServerCertificate` не задано значение). Имя пользователя и пароль передаются в строку подключения.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Встроенная проверка подлинности Windows (Kerberos в Linux и macOS) с использованием SSPI (для SQL Server или IaaS SQL) — текущий синтаксис. Сертификат сервера не проверяется, если не используется шифрование. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Только для драйверов Windows_.) Встроенная проверка подлинности Windows с использованием SSPI (если целевая база данных находится в SQL Server или IaaS SQL) — новый синтаксис. Клиент запрашивает шифрование `Encrypt` (значение по умолчанию — `true`), а сертификат сервера проверяется независимо от параметра шифрования `true`(если `TrustServerCertificate` не задано значение). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Проверка подлинности имени пользователя AAD и пароля (если целевая база данных находится в Azure SQL DB). Сертификат сервера проверяется независимо от параметра шифрования (если `TrustServerCertificate` не `true`задано значение). Имя пользователя и пароль передаются в строку подключения. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Только для драйверов Windows_.) Встроенная проверка подлинности Windows с помощью ADAL, которая включает учетные данные учетной записи Windows для маркера доступа, выданного AAD, предполагая, что Целевая база данных находится в базе данных SQL Azure. Сертификат сервера проверяется независимо от параметра шифрования (если `TrustServerCertificate` не `true`задано значение). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Только для драйверов Windows_.) При интерактивной проверке подлинности AAD для настройки подключения используется технология многофакторной идентификации Azure. В этом режиме, указав идентификатор входа, активируется диалоговое окно проверки подлинности Azure, которое позволяет пользователю ввести пароль для завершения подключения. Имя пользователя передается в строке подключения.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![Виндовсазуреаус. png](windows/WindowsAzureAuth.png)

8. При проверке подлинности AAD Управляемое удостоверение службы использует назначенное системой или пользователю удостоверение для проверки подлинности, чтобы настроить подключение. Для назначенного пользователем удостоверения в качестве идентификатора пользователя задается идентификатор объекта удостоверения пользователя.<br>
Для назначенного системой удостоверения:<br>
`server=Server;database=Database;Authentication=ActiveDirectoryMsi;`<br>
Для назначенного пользователем удостоверения с ИДЕНТИФИКАТОРом объекта, равным Мйобжектид,<br>
`server=Server;database=Database;UID=myObjectId;Authentication=ActiveDirectoryMsi;`

> [!NOTE] 
>- При использовании новых параметров Active Directory с драйвером Windows ODBC убедитесь, что [Библиотека проверки подлинности Active Directory для SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) установлен. При использовании драйверов Linux и macOS убедитесь, что `libcurl` установлен. Для драйвера версии 17,2 и более поздней эта зависимость не является явной, поскольку она не является обязательной для других методов проверки подлинности или операций ODBC.
>- Чтобы подключиться с помощью имени пользователя и пароля учетной записи SQL Server, теперь можно использовать `SqlPassword` новый параметр, который рекомендуется для SQL Azure, так как этот параметр обеспечивает более безопасные значения по умолчанию для подключений.
>- Чтобы подключиться с помощью имени пользователя и пароля учетной записи `Authentication=ActiveDirectoryPassword` Azure Active Directory, укажите в строке подключения `UID` и `PWD` ключевые слова и с именем пользователя и паролем соответственно.
>- Чтобы подключиться с помощью встроенной проверки подлинности Windows или встроенной Active Directory ( `Authentication=ActiveDirectoryIntegrated` только драйвер Windows), укажите в строке подключения. Драйвер автоматически выбирает правильный режим проверки подлинности. `UID`и `PWD` не должны быть указаны.
>- Для подключения с использованием Active Directory интерактивной проверки подлинности `UID` (только драйвер Windows) необходимо указать.

## <a name="authenticating-with-an-access-token"></a>Проверка подлинности с помощью маркера доступа

Атрибут `SQL_COPT_SS_ACCESS_TOKEN` предварительного подключения позволяет использовать маркер доступа, полученный из Azure AD, для проверки подлинности вместо имени пользователя и пароля, а также обходит согласование и получение маркера доступа драйвером. Чтобы использовать маркер доступа, задайте `SQL_COPT_SS_ACCESS_TOKEN` для атрибута соединения указатель `ACCESSTOKEN` на структуру:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

— Это структура переменной _длины_, состоящая из 4-байтовой _длины_ , за которой следует длина байт непрозрачных данных, образующих маркер доступа. `ACCESSTOKEN` Из-за того, как SQL Server обрабатывает маркеры доступа, один из них, полученный с помощью ответа JSON [2,0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) , должен быть расширен таким образом, чтобы за каждым байтом был байт нулевого отступа, аналогично строке UCS-2, содержащей только символы ASCII. Однако маркер является непрозрачным значением, а длина, указанная в байтах, не должна содержать знак завершения null. Из-за существенных ограничений длины и формата этот метод проверки подлинности доступен только программно `SQL_COPT_SS_ACCESS_TOKEN` через атрибут Connection. отсутствует соответствующее ключевое слово DSN или строка подключения. Строка подключения не должна содержать `UID`ключевые слова, `Authentication` `PWD`, или `Trusted_Connection` .

> [!NOTE]
> Драйвер ODBC версии 13,1 поддерживает только эту проверку подлинности в _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Образец кода проверки подлинности Azure Active Directory

В следующем примере показан код, необходимый для подключения к SQL Server с помощью Azure Active Directory с ключевыми словами подключения. Обратите внимание, что нет необходимости изменять сам код приложения. Строка подключения или DSN, если она используется, является единственным изменением, необходимым для использования AAD для проверки подлинности:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
В следующем примере показан код, необходимый для подключения к SQL Server с помощью Azure Active Directory с проверкой подлинности на основе маркеров доступа. В этом случае необходимо изменить код приложения для обработки маркера доступа и установить связанный атрибут соединения.
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server}"
    SQLCHAR accessToken[] = "eyJ0eXAiOi..."; // In the format extracted from an OAuth JSON response
    ...
    DWORD dataSize = 2 * strlen(accessToken);
    ACCESSTOKEN *pAccToken = malloc(sizeof(ACCESSTOKEN) + dataSize);
    pAccToken->dataSize = dataSize;
    // Expand access token with padding bytes
    for(int i = 0, j = 0; i < dataSize; i += 2, j++) {
        pAccToken->data[i] = accessToken[j];
        pAccToken->data[i+1] = 0;
    }
    ...
    SQLSetConnectAttr(hDbc, SQL_COPT_SS_ACCESS_TOKEN, (SQLPOINTER)pAccToken, SQL_IS_POINTER);
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);      
    ...
    free(pAccToken);
~~~
Ниже приведен пример строки подключения для использования с Azure Active Directoryной интерактивной проверкой подлинности. Обратите внимание, что он не содержит поле PWD, так как пароль будет использоваться на экране проверки подлинности Azure.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~
Ниже приведен пример строки подключения для использования с проверкой подлинности Azure Active Directory Управляемое удостоверение службы. Учтите, что идентификатор пользователя указывается идентификатору объекта удостоверения пользователя для назначаемого пользователем удостоверения.
~~~
// For system-assigned identity,
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};Authentication=ActiveDirectoryMsi"
...
// For user-assigned identity with object ID equals to myObjectId
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myObjectId;Authentication=ActiveDirectoryMsi"
~~~

## <a name="see-also"></a>См. также:
[Поддержка проверки подлинности на основе маркеров для базы данных SQL Azure с помощью проверки подлинности Azure AD](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

