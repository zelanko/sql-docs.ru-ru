---
title: С помощью Azure Active Directory с помощью драйвера ODBC | Документация по Microsoft для SQL Server
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
manager: craigg
ms.openlocfilehash: 98f7e0ac3667bc8546a7bf7ce2d8036341bb2650
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 12/11/2018
ms.locfileid: "53206603"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>Использование Azure Active Directory с драйвером ODBC
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Назначение

Драйвер Microsoft ODBC для SQL Server с версии 13.1 или более поздней позволяет приложениям ODBC для подключения к экземпляру SQL Azure, федеративного удостоверения в Azure Active Directory с помощью имени пользователя и пароля, маркер доступа Azure Active Directory или Windows Встроенная проверка подлинности (_только драйвер Windows_). Для драйвера ODBC версии 13.1, доступа Azure Active Directory, маркер проверки подлинности является _Windows только_. Драйвер ODBC версии 17 и выше поддерживает этой проверки подлинности на всех платформах (Windows, Linux и Mac). Новый интерактивный аутентификации Azure Active Directory с Идентификатором входа впервые появился в версии 17.1 драйвера ODBC для Windows. Все они выполняются при помощи нового источника данных и ключевых слов строки подключения и атрибуты соединения.

> [!NOTE]
> Драйвер ODBC для Linux и macOS не поддерживает службы федерации Active Directory. Если используется проверка подлинности имени пользователя и пароля Azure Active Directory из Linux или macOS клиента и конфигурации Active Directory включает службы федерации, возможен сбой проверки подлинности.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Новых или измененных DSN и ключевых слов строки подключения

`Authentication` Ключевое слово может использоваться при соединении с использованием имени DSN или строки подключения для управления режимом проверки подлинности. В строке подключения задано значение переопределяет значение этого источника данных, если указано. _Предварительно значение атрибута_ из `Authentication` параметр является значением, вычисляемым на основе строки подключения и значения имени DSN.

|Имя|Значения|По умолчанию|Описание|
|-|-|-|-|
|`Authentication`|(не задано), (пустая строка), `SqlPassword`, `ActiveDirectoryPassword`, `ActiveDirectoryIntegrated`, `ActiveDirectoryInteractive`|(не задано)|Контролирует режим проверки подлинности.<table><tr><th>Значение<th>Описание<tr><td>(не задано)<td>Режим проверки подлинности определяется другими ключевыми словами (существующие параметры подключения прежних версий).<tr><td>(пустая строка)<td>Строкой подключения является: "{0}" Переопределение и удаление `Authentication` заданное в имени DSN.<tr><td>`SqlPassword`<td>Проверку подлинности непосредственно в экземпляр SQL Server, используя имя пользователя и пароль.<tr><td>`ActiveDirectoryPassword`<td>Проверка подлинности с помощью удостоверения Azure Active Directory, используя имя пользователя и пароль.<tr><td>`ActiveDirectoryIntegrated`<td>_Только драйвер Windows_. Проверка подлинности с помощью удостоверения Azure Active Directory, используя встроенную проверку подлинности.<tr><td>`ActiveDirectoryInteractive`<td>_Только драйвер Windows_. Проверка подлинности с помощью удостоверения Azure Active Directory с помощью интерактивной проверки подлинности.</table>|
|`Encrypt`|(не задано), `Yes`, `No`|(см. описание)|Управляет шифрованием соединения. Если значение атрибута предварительного `Authentication` параметр не _none_ DSN или строки подключения, по умолчанию используется `Yes`. В противном случае значение по умолчанию — `No`. Если атрибут `SQL_COPT_SS_AUTHENTICATION` переопределяет значение атрибута предварительного `Authentication`, явным образом задать значение шифрования в DSN или строки подключения или атрибут соединения. Значение атрибута предварительного шифрования `Yes` Если присвоено значение `Yes` в строке подключения или имя DSN.|

## <a name="new-andor-modified-connection-attributes"></a>Атрибуты соединения новых или измененных

Следующие предварительно подключением атрибуты либо были представлены или изменены для поддержки проверки подлинности Azure Active Directory. Если атрибут соединения имеет соответствующую строку подключения или ключевое слово DSN и имеет значение, атрибут соединения имеет приоритет.

|attribute|Тип|Значения|По умолчанию|Описание|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_AD_INTERACTIVE`, `SQL_AU_RESET`|(не задано)|См. описание `Authentication` выше ключевое слово. `SQL_AU_NONE` предоставляется для явного переопределения набора `Authentication` значение в строке подключения DSN и/или пока `SQL_AU_RESET` отменяет атрибут, если он был задан, позволяя DSN или подключения строковое значение, более высокий приоритет.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Указатель на `ACCESSTOKEN` или значение NULL|NULL|Если не null, указывает AzureAD токена доступа для использования. Это ошибка для указания маркера доступа, а также `UID`, `PWD`, `Trusted_Connection`, или `Authentication` ключевых слов строки подключения или их эквивалент атрибутов. <br> **Примечание.** Драйвер ODBC версии 13.1 поддерживает только это на _Windows_.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(см. описание)|Управляет шифрованием соединения. `SQL_EN_OFF` и `SQL_EN_ON` отключить и включить шифрование, соответственно. Если значение атрибута предварительного `Authentication` параметр не _none_ или `SQL_COPT_SS_ACCESS_TOKEN` имеет значение, и `Encrypt` не был указан в строке подключения или имя DSN, по умолчанию используется `SQL_EN_ON`. В противном случае значение по умолчанию — `SQL_EN_OFF`. Если атрибут соединения `SQL_COPT_SS_AUTHENTICATION` присваивается не _none_, явно задайте `SQL_COPT_SS_ENCRYPT` нужное значение Если `Encrypt` в DSN или строки подключения не указан. Действительное значение этого атрибута элементы управления [шифрование будет использоваться для подключения.](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Не поддерживается с Azure Active Directory, так как изменения паролей участникам AAD не могут быть реализованы через соединение ODBC. <br><br>Истечение срока действия пароля для проверки подлинности SQL Server было введено в SQL Server 2005. `SQL_COPT_SS_OLDPWD` Был добавлен атрибут, чтобы разрешить клиенту предоставлять старый и новый пароль для подключения. Если задано это свойство, поставщик не будет использовать пул соединений для первого и последующих соединений, поскольку строка подключения будет содержать «старый пароль», который уже изменен.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Рекомендуется использовать_; используйте `SQL_COPT_SS_AUTHENTICATION` присвоено `SQL_AU_AD_INTEGRATED` вместо этого. <br><br>Принудительное использование проверки подлинности Windows (Kerberos в Linux и macOS) для проверки доступа имени входа на сервер. Если используется проверка подлинности Windows, драйвер пропускает идентификатор значения пользователя и пароля предоставляется как часть `SQLConnect`, `SQLDriverConnect`, или `SQLBrowseConnect` обработки.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Добавление пользовательского интерфейса для Azure Active Directory (только драйвер Windows)

Настройки имени источника данных и подключения пользовательских интерфейсов драйвера были улучшены Дополнительные параметры, необходимые для использования проверки подлинности с помощью Azure AD.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Создание и изменение источников данных в пользовательском Интерфейсе

Существует возможность использовать новый Azure AD параметры проверки подлинности при создании или редактировании существующего источника данных с помощью программы установки драйвера пользовательского интерфейса:

`Authentication=ActiveDirectoryIntegrated` для интегрированной аутентификации в SQL Azure с использованием Azure Active Directory

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword` для проверки подлинности имя пользователя и пароль Azure Active Directory для SQL Azure

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` для интерактивной проверки подлинности Azure Active Directory в SQL Azure

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword` для проверки подлинности имя пользователя и пароль для SQL Server (Azure или других)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes` для Windows SSPI устаревших встроенная проверка подлинности

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

Пять параметры соответствуют свойствам `Trusted_Connection=Yes` (существующие прежних версий Windows SSPI-только для встроенной проверки подлинности) и `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, `ActiveDirectoryPassword`, и `ActiveDirectoryInteractive`, соответственно.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect строки (только драйвер Windows)

Диалогового окна запроса, отображаемого элементом SQLDriverConnect, когда он запрашивает сведения, необходимые для завершения подключения содержит три новых параметра для проверки подлинности Azure AD:

![ServerLogin.png](windows/ServerLogin.png)

Эти параметры соответствуют свойствам же пять в настройки имени источника данных выше пользовательского интерфейса.

### <a name="example-connection-strings"></a>Примеры строк подключения
1. Проверка подлинности SQL Server - синтаксис в предыдущих версиях. Сертификат сервера не проверяется, а шифрование применяется только в том случае, если сервер инициирует его. Имя пользователя и пароль передаются в строке подключения.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. Проверка подлинности SQL - новый синтаксис. Клиент запрашивает шифрование (значение по умолчанию `Encrypt` — `true`) и сертификат сервера получает проверенный, независимо от того, параметр шифрования (если не `TrustServerCertificate` присваивается `true`). Имя пользователя и пароль передаются в строке подключения.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Встроенная проверка подлинности Windows (Kerberos в Linux и macOS) с помощью интерфейса SSPI (SQL Server или SQL IaaS) — текущего синтаксиса. Сертификат сервера не проверяется, если не используется шифрование. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Только драйвер Windows_.) Встроенная проверка подлинности Windows с помощью SSPI (если целевая база данных находится в SQL Server или SQL IaaS) — новый синтаксис. Клиент запрашивает шифрование (значение по умолчанию `Encrypt` — `true`) и сертификат сервера получает проверенный, независимо от того, параметр шифрования (если не `TrustServerCertificate` присваивается `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Имя пользователя и пароль проверки подлинности AAD (если целевая база данных находится в базе данных SQL Azure). Получает проверить сертификат сервера, независимо от того, параметр шифрования (если только не `TrustServerCertificate` присваивается `true`). Имя пользователя и пароль передаются в строке подключения. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Только драйвер Windows_.) Встроенная проверка подлинности Windows, с помощью ADAL, которая включает в себя использование учетных данных учетной записи Windows на маркер доступа, выданных AAD, при условии, что целевая база данных находится в базе данных SQL Azure. Получает проверить сертификат сервера, независимо от того, параметр шифрования (если только не `TrustServerCertificate` присваивается `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Только драйвер Windows_.) Интерактивная проверка подлинности AAD используется технология многофакторной идентификации Azure для настройки подключения. В этом режиме, предоставляя идентификатор входа диалоговое окно проверки подлинности Windows Azure запускается и позволяет пользователю на ввод пароля для завершения подключения. Имя пользователя передается в строке подключения.
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

> [!NOTE] 
>- При использовании новых параметров Active Directory с драйвером Windows ODBC, убедитесь, что [Active Directory Authentication Library для SQL Server](https://go.microsoft.com/fwlink/?LinkID=513072) установки. При использовании драйверов Linux и macOS, убедитесь, что `libcurl` установлен. Версия драйвера, начиная с 17.2, это не для явных зависимостей, так как он не является обязательным для методов проверки подлинности или операций ODBC.
>- Чтобы подключиться, используя имя пользователя учетной записи SQL Server и пароль, теперь можно использовать новый `SqlPassword` параметр, который рекомендуется специально для SQL Azure, так как этот параметр включает более безопасные соединения по умолчанию.
>- Чтобы подключиться с помощью имени пользователя учетной записи Azure Active Directory и пароль учетной записи, укажите `Authentication=ActiveDirectoryPassword` в строке подключения и `UID` и `PWD` ключевые слова, имя пользователя и пароль, соответственно.
>- Чтобы подключиться с помощью интеграции Windows или Active Directory (только для Windows драйвер) проверки подлинности, укажите `Authentication=ActiveDirectoryIntegrated` в строке подключения. Драйвер автоматически выберет режиме прошла проверку подлинности. `UID` и `PWD` не должно быть указано.
>- Для подключения с использованием аутентификации Active Directory Interactive (только для Windows драйвер), `UID` должен быть указан.

## <a name="authenticating-with-an-access-token"></a>Проверка подлинности с помощью маркера доступа

`SQL_COPT_SS_ACCESS_TOKEN` Атрибута предварительного соединения позволяет использовать маркер доступа, полученного из Azure AD для проверки подлинности, а не имя пользователя и пароль и также обходила согласования и получение маркера доступа с помощью драйвера. Чтобы использовать маркер доступа, задайте `SQL_COPT_SS_ACCESS_TOKEN` атрибут соединения к указателю на `ACCESSTOKEN` структуры:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

`ACCESSTOKEN` Является структурой переменной длины, состоящий из 4-байтовый _длина_ следуют _длина_ байт непрозрачных данных, которые образуют маркер доступа. Из-за как SQL Server обрабатывает маркеры доступа, один, полученных через [OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) ответа JSON необходимо развернуть, чтобы каждый байт сопровождается padding byte, аналогичную UCS-2. Строка, содержащая только символы ASCII 0; тем не менее, маркер является Непрозрачное значение и длину, заданную в байтах, не должны включать символ завершения null. Из-за их значительные ограничения, длина и формат, этот метод проверки подлинности доступен только программным способом с помощью `SQL_COPT_SS_ACCESS_TOKEN` атрибут соединения; нет соответствующего имени DSN или ключевое слово строки подключения. Строка подключения не должна содержать `UID`, `PWD`, `Authentication`, или `Trusted_Connection` ключевые слова.

> [!NOTE]
> Драйвер ODBC версии 13.1 поддерживает только этой проверки подлинности на _Windows_.

## <a name="azure-active-directory-authentication-sample-code"></a>Образец кода проверки подлинности Azure Active Directory

Ниже приведен пример кода, необходимые для подключения к SQL Server с помощью Azure Active Directory с помощью ключевых слов подключения. Обратите внимание, что не нужно изменять код приложения. Строка подключения, то есть имя источника данных, если он используется, является единственным изменением, необходимые для использования AAD для проверки подлинности:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
Ниже приведен пример кода, необходимые для подключения к SQL Server с помощью Azure Active Directory с помощью проверки подлинности маркера доступа. В этом случае необходимо изменить код приложения для обработки маркера доступа и задать атрибут связанного соединения.
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
Ниже приведен пример строки подключения для использования с Azure Active Directory интерактивной проверки подлинности. Обратите внимание на то, что он не содержит поле PWD как бы ввода пароля с помощью экрана идентификацию Windows Azure.
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~

## <a name="see-also"></a>См. также:
[Поддержка проверки подлинности на основе маркеров для базы данных SQL Azure с помощью проверки подлинности Azure AD](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

