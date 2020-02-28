---
title: Использование Azure Active Directory с драйвером ODBC | Документация Майкрософт для SQL
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
ms.openlocfilehash: e32889ceafa78d6c6eac716fca213f17badc5cea
ms.sourcegitcommit: 12051861337c21229cfbe5584e8adaff063fc8e3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2020
ms.locfileid: "77363223"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Использование Azure Active Directory с драйвером ODBC
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Назначение

Microsoft ODBC Driver for SQL Server версии 13.1 или более поздней позволяет приложениям ODBC подключаться к экземпляру SQL Azure по федеративному удостоверению Azure Active Directory с использованием имени пользователя и пароля, маркера доступа или управляемого удостоверения службы Azure Active Directory либо с помощью встроенной проверки подлинности Windows (_только драйвер Windows_). Для драйвера ODBC версии 13.1 проверка подлинности с помощью маркера доступа Azure Active Directory выполняется _только для Windows_. Драйвер ODBC версии 17 и более поздней поддерживает эту проверку подлинности на всех платформах (Windows, Linux и Mac). В драйвере ODBC версии 17.1 для Windows представлена новая интерактивная проверка подлинности Azure Active Directory с именем для входа. Новый метод проверки подлинности с помощью управляемого удостоверения службы Azure Active Directory был добавлен в драйвер ODBC версии 17.3.1.1 и поддерживается для назначенных системой и назначенных пользователем удостоверений. Все эти действия выполняются с помощью новых ключевых слов строки подключения и имени DSN, а также атрибутов подключения.

> [!NOTE]
> Драйвер ODBC в Linux и macOS поддерживает только проверку подлинности Azure Active Directory непосредственно в Azure Active Directory. Если вы используете проверку подлинности Azure Active Directory по имени пользователя или паролю из клиента Linux или macOS и для конфигурации Active Directory требуется проверка подлинности клиента в конечной точке служб федерации Active Directory, проверка может завершиться ошибкой.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Новые или измененные ключевые слова строки подключения и имени DSN

Ключевое слово `Authentication` можно использовать при установке подключения через имя DSN или строку подключения для управления режимом проверки подлинности. Значение, заданное в строке подключения, переопределяет значение в имени DSN, если оно указано. _Значение предварительного атрибута_ параметра `Authentication` вычисляется на основе значений строки подключения и имени DSN.

|Имя|Значения|По умолчанию|Описание|
|-|-|-|-|
|`Authentication`|(не задано), (пустая строка), `SqlPassword`, `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`, `ActiveDirectoryMsi` |(не задано)|Управляет режимом проверки подлинности.<table><tr><th>Значение<th>Описание<tr><td>(не задано)<td>Режим проверки подлинности определяется другими ключевыми словами (существующие параметры устаревшего подключения).<tr><td>(пустая строка)<td>(Только строка подключения.) Переопределение и отмена значения `Authentication`, заданного в имени DSN.<tr><td>`SqlPassword`<td>Прямая проверка подлинности в экземпляре SQL Server по имени пользователя и пароля.<tr><td>`ActiveDirectoryPassword`<td>Проверка подлинности по удостоверению Azure Active Directory с использованием имени пользователя и пароля.<tr><td>`ActiveDirectoryIntegrated`<td>_Только драйвер Windows_. Встроенная проверка подлинности с использованием удостоверения Azure Active Directory.<tr><td>`ActiveDirectoryInteractive`<td>_Только драйвер Windows_. Интерактивная проверка подлинности с использованием удостоверения Azure Active Directory.<tr><td>`ActiveDirectoryMsi`<td>Проверка подлинности с помощью управляемого удостоверения службы с использованием удостоверения Azure Active Directory. Для назначаемого пользователем удостоверения в качестве идентификатора пользователя указывается идентификатор объекта удостоверения пользователя.</table>|
|`Encrypt`|(не задано), `Yes`, `No`|(см. описание)|Управляет шифрованием соединения. Если предварительный атрибут параметра `Authentication` не имеет значение _none_ в DSN или строке подключения, по умолчанию используется `Yes`. В противном случае значение по умолчанию — `No`. Если атрибут `SQL_COPT_SS_AUTHENTICATION` переопределяет значение предварительного атрибута `Authentication`, явно задайте значение шифрования в имени DSN, строке подключения или атрибуте подключения. Значением предварительного атрибута шифрования является `Yes`, если значение равно `Yes` в имени DSN или в строке подключения.|

## <a name="new-andor-modified-connection-attributes"></a>Новые или измененные атрибуты подключения

Для поддержки проверки подлинности Azure Active Directory были введены или изменены следующие предварительные атрибуты подключения. Если атрибут подключения имеет соответствующее ключевое слово строки подключения или имени DSN и установлен, у этого атрибута будет более высокий приоритет.

|attribute|Тип|Значения|По умолчанию|Описание|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_AD_MSI`, `SQL_AU_RESET`|(не задано)|См. описание ключевого слова `Authentication` выше. `SQL_AU_NONE` предоставляется для явного переопределения заданного значения `Authentication` в имени DSN или строке подключения, в то время как `SQL_AU_RESET` отменяет атрибут, если он был установлен, и значение имени DSN или строки подключения получает более высокий приоритет.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Указатель на `ACCESSTOKEN` или значение NULL|NULL|Если значение не равно NULL, указывается используемый маркер доступа Azure AD. Указание маркера доступа, а также ключевых слов строки подключения `UID`, `PWD`, `Trusted_Connection`, `Authentication` или эквивалентных атрибутов является ошибкой. <br> **ПРИМЕЧАНИЕ.** Драйвер ODBC версии 13.1 поддерживает это только в _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(см. описание)|Управляет шифрованием соединения. `SQL_EN_OFF` отключает шифрование, а `SQL_EN_ON`— включает. Если предварительный атрибут параметра `Authentication` не имеет значение _none_ или если значение `SQL_COPT_SS_ACCESS_TOKEN` задано, а ключевое слово `Encrypt` не указано ни в имени DSN, ни в строке подключения, по умолчанию используется значение `SQL_EN_ON`. В противном случае значение по умолчанию — `SQL_EN_OFF`. Если для атрибута подключения `SQL_COPT_SS_AUTHENTICATION` не задано значение _none_, явно задайте для `SQL_COPT_SS_ENCRYPT` нужное значение, если ключевое слово `Encrypt` не указано в имени DSN или в строке подключения. Действительное значение этого атрибута определяет, [будет ли использоваться шифрование для подключения](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation).|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Не поддерживается в Azure Active Directory, так как изменения паролей в субъектах AAD невозможно выполнить через подключение ODBC. <br><br>Истечение срока действия пароля для проверки подлинности SQL Server было введено в SQL Server 2005. Добавлен атрибут `SQL_COPT_SS_OLDPWD`, чтобы клиент мог предоставлять как старый, так и новый пароль для подключения. Если задано это свойство, поставщик не будет использовать пул соединений для первого и последующих соединений, поскольку строка подключения будет содержать «старый пароль», который уже изменен.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Нерекомендуемый_. Вместо этого для параметра `SQL_COPT_SS_AUTHENTICATION` укажите значение `SQL_AU_AD_INTEGRATED`. <br><br>Задает принудительное использование проверки подлинности Windows (Kerberos в Linux и macOS) для проверки доступа по имени входа для сервера. Если используется проверка подлинности Windows, драйвер пропускает значения идентификатора пользователя и пароля, предоставленные в процессе обработки `SQLConnect`, `SQLDriverConnect` или `SQLBrowseConnect`.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Дополнения пользовательского интерфейса для Azure Active Directory (только для драйверов Windows)

Для настройки имени DSN с помощью пользовательских интерфейсов подключения драйвера добавлены дополнительные параметры, необходимые для использования проверки подлинности в Azure AD.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Создание и изменение имен DSN в пользовательском интерфейсе

При создании или изменении существующего имени DSN с помощью пользовательского интерфейса установки драйвера можно использовать новые параметры проверки подлинности Azure AD:

`Authentication=ActiveDirectoryIntegrated` для интегрированной аутентификации в SQL Azure с использованием Azure Active Directory

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword` для проверки подлинности Azure Active Directory на основе имени пользователя и пароля в SQL Azure.

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` для интерактивной проверки подлинности Azure Active Directory в SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword` для проверки подлинности на основе пользователя и пароля в SQL Server (Azure или иным способом).

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes` для устаревшей встроенной проверки подлинности SSPI Windows.

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

Пять параметров соответствуют `Trusted_Connection=Yes` (устаревшая встроенная проверка подлинности только с использованием Windows SSPI), `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryPassword` и `ActiveDirectoryInteractive` соответственно.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>Диалоговое окно SQLDriverConnect (только драйвер Windows)

Диалоговое окно, отображаемое SQLDriverConnect при запросе сведений, необходимых для завершения подключения, содержит три новых параметра для проверки подлинности Azure AD:

![ServerLogin.png](windows/ServerLogin.png)

Эти параметры соответствуют пяти доступным установкам в пользовательском интерфейсе настройки имени DSN.

### <a name="example-connection-strings"></a>Примеры строк подключения
1. Устаревший синтаксис проверки подлинности SQL Server. Сертификат сервера не проверяется, и шифрование используется только в том случае, если сервер применяет его принудительно. Имя пользователя и пароль передаются в строку подключения.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. Новый синтаксис проверки подлинности SQL. Клиент запрашивает шифрование (значение параметра `Encrypt` по умолчанию — `true`), а сертификат сервера проверяется независимо от параметра шифрования (если только для параметра `TrustServerCertificate` не задано значение `true`). Имя пользователя и пароль передаются в строку подключения.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Встроенная проверка подлинности Windows (Kerberos в Linux и macOS) с использованием SSPI (для SQL Server или IaaS SQL) — текущий синтаксис. Сертификат сервера не проверяется, если шифрование не используется. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Только драйвер Windows_.) Встроенная проверка подлинности Windows с использованием SSPI (если целевая база данных находится в SQL Server или IaaS SQL) — новый синтаксис. Клиент запрашивает шифрование (значение параметра `Encrypt` по умолчанию — `true`), а сертификат сервера проверяется независимо от параметра шифрования (если только для параметра `TrustServerCertificate` не задано значение `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Проверка подлинности по имени пользователя и пароля AAD (если целевая база данных находится в Базе данных SQL Azure). Сертификат сервера проверяется независимо от параметра шифрования (если только параметр `TrustServerCertificate` не имеет значение `true`). Имя пользователя и пароль передаются в строку подключения. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Только драйвер Windows_.) Встроенная проверка подлинности Windows с помощью ADAL, которая активирует учетные данные учетной записи Windows для маркера доступа, выданного AAD, при условии, что целевая база данных находится в Базе данных SQL Azure. Сертификат сервера проверяется независимо от параметра шифрования (если только параметр `TrustServerCertificate` не имеет значение `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Только драйвер Windows_.) При интерактивной проверке подлинности AAD для настройки подключения используется технология многофакторной идентификации Azure. В этом режиме после указания имени для входа активируется диалоговое окно проверки подлинности Azure, которое позволяет пользователю ввести пароль для завершения установки подключения. Имя пользователя передается в строку подключения.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

8. При проверке подлинности по управляемому удостоверению службы AAD, осуществляемой для настройки подключения, используется назначенное системой или пользователем удостоверение. Для назначенного пользователем удостоверения в качестве идентификатора пользователя задается идентификатор объекта удостоверения пользователя.<br>
Для назначенного системой удостоверения:<br>
`server=Server;database=Database;Authentication=ActiveDirectoryMsi;`<br>
Для назначенного пользователем удостоверения с идентификатором объекта равным myObjectId:<br>
`server=Server;database=Database;UID=myObjectId;Authentication=ActiveDirectoryMsi;`

> [!NOTE] 
>- При использовании новых параметров Active Directory с драйвером ODBC Windows должна быть установлена [Библиотека проверки подлинности Active Directory для SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072). При использовании драйверов Linux и macOS убедитесь, что `libcurl` установлена. Для драйвера версии 17.2 и более поздних эта зависимость не является явной, так как она не обязательна для других методов проверки подлинности или операций ODBC.
>- Чтобы подключиться с помощью имени пользователя и пароля учетной записи SQL Server, теперь можно использовать новый параметр `SqlPassword` (рекомендуется для SQL Azure, так как этот параметр обеспечивает более безопасные значения по умолчанию для подключений).
>- Чтобы подключиться с помощью имени пользователя и пароля учетной записи Azure Active Directory, укажите `Authentication=ActiveDirectoryPassword` в строке подключения, а также ключевые слова `UID` и `PWD` с именем пользователя и паролем соответственно.
>- Чтобы подключиться с помощью встроенной проверки подлинности Windows или встроенной проверки подлинности Active Directory (только драйвер Windows), укажите `Authentication=ActiveDirectoryIntegrated` в строке подключения. Драйвер автоматически выбирает правильный режим проверки подлинности. Не следует указывать `UID` и `PWD`.
>- Для подключения с использованием интерактивной проверки подлинности Active Directory (только для драйвера Windows) необходимо указать `UID`.

## <a name="authenticating-with-an-access-token"></a>Проверка подлинности с помощью маркера доступа

Настраиваемый перед подключением атрибут `SQL_COPT_SS_ACCESS_TOKEN` позволяет использовать маркер доступа, полученный из Azure AD, для проверки подлинности вместо имени пользователя и пароля, а также обходит согласование и получение маркера доступа драйвером. Чтобы использовать маркер доступа, задайте для указателя на структуру `ACCESSTOKEN` атрибут подключения `SQL_COPT_SS_ACCESS_TOKEN`:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

`ACCESSTOKEN` представляет собой структуру переменной длины, состоящую из _4-байт_, за которой следует значение _длины_ байт непрозрачных данных, образующих маркер доступа. Из-за того, как SQL Server обрабатывает маркеры доступа, один из них, полученный с помощью ответа JSON [OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios), должен быть расширен таким образом, чтобы за каждым байтом был байт нулевого отступа, аналогично строке UCS-2, содержащей только символы ASCII. Маркер является непрозрачным значением, а длина, указанная в байтах, не должна содержать символ завершения NULL. По причине существенных ограничений длины и формата этот метод проверки подлинности доступен только программно с помощью атрибута подключения `SQL_COPT_SS_ACCESS_TOKEN`. Соответствующее ключевое слово DSN или строки подключения отсутствуют. Строка подключения не должна содержать ключевые слова `UID`, `PWD`, `Authentication` или `Trusted_Connection`.

> [!NOTE]
> Драйвер ODBC версии 13.1 поддерживает такую проверку подлинности только в _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Образец кода проверки подлинности Azure Active Directory

В следующем примере показан код, необходимый для подключения к SQL Server с помощью Azure Active Directory с помощью ключевых слов подключения. Обратите внимание, что код приложения менять не нужно. Для проверки подлинности AAD следует изменить только строку подключения или имя DSN, если оно используется.
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
В следующем примере показан код, необходимый для подключения к SQL Server с помощью Azure Active Directory с использованием проверки подлинности на основе маркеров доступа. В этом случае необходимо изменить код приложения для обработки маркера доступа и настроить связанный атрибут подключения.
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
Ниже приведен пример строки подключения для использования с интерактивной проверкой подлинности Azure Active Directory. Обратите внимание, что он не содержит поле PWD, так как пароль будет вводиться на экране проверки подлинности Azure.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~
Ниже приведен пример строки подключения для использования с проверкой подлинности Azure Active Directory на основе управляемого удостоверения службы. Учтите, что идентификатор пользователя указывается идентификатору объекта удостоверения пользователя для назначаемого пользователем удостоверения.
~~~
// For system-assigned identity,
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};Authentication=ActiveDirectoryMsi"
...
// For user-assigned identity with object ID equals to myObjectId
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myObjectId;Authentication=ActiveDirectoryMsi"
~~~

## <a name="see-also"></a>См. также:
[Token-based authentication support for Azure SQL DB using Azure AD auth](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth) (Поддержка аутентификации на основе маркера для Базы данных SQL Azure с использованием аутентификации Azure AD)

