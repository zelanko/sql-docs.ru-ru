---
title: "С помощью Azure Active Directory с помощью драйвера ODBC | Документы Microsoft"
ms.custom: 
ms.date: 04/18/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: afdd399a8efcbb67915eab1978796b812e8a6558
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>С помощью Azure Active Directory с помощью драйвера ODBC
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>Назначение

ODBC Driver 13.1 for SQL Server позволяет приложениям ODBC для подключения к экземпляру SQL Azure, с помощью федеративного удостоверения в Azure Active Directory с имени пользователя и пароля, маркер доступа Azure Active Directory (только для Windows драйвер) или интеграции с Windows Проверка подлинности (только для Windows драйвер). Это достигается за счет применения нового источника данных и ключевых слов строки подключения и атрибуты соединения.

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>Нового или измененного DSN и ключевых слов строки подключения

`Authentication` Ключевое слово может использоваться при соединении с DSN или строка соединения для управления режимом проверки подлинности. Значение, заданное в строке подключения, переопределения, в имени DSN, если указано. _Предварительно значение атрибута_ из `Authentication` задано значение вычисляется из значений источника данных и строку соединения.

|Имя|Значения|По умолчанию|Description|
|-|-|-|-|
|`Authentication`|(не задано), (пустая строка), `SqlPassword`, `ActiveDirectoryPassword`,`ActiveDirectoryIntegrated`|(не задано)|Определяет режим проверки подлинности.<table><tr><th>Значение<th>Description<tr><td>(не задано)<td>Режим проверки подлинности определяется другие ключевые слова (существующие параметры соединения прежних версий).<tr><td>пустая строка)<td>(Строка подключения только.) Переопределите и не задано `Authentication` заданное в имени DSN.<tr><td>`SqlPassword`<td>Проверка подлинности непосредственно к экземпляру SQL Server, с использованием имени пользователя и пароля.<tr><td>`ActiveDirectoryPassword`<td>Проверка подлинности с помощью удостоверения Azure Active Directory, используя имя пользователя и пароль.<tr><td>`ActiveDirectoryIntegrated`<td>_Только драйвер Windows_. Проверка подлинности с помощью удостоверения Azure Active Directory, используя встроенную проверку подлинности.</table>|
|`Encrypt`|(не задано), `Yes`,`No`|(см. описание)|Управляет шифрованием соединения. Если значение атрибута перед `Authentication` не является параметром _нет_, значение по умолчанию — `Yes`. В противном случае — значение по умолчанию — `No`. Значение атрибута перед шифрования `Yes` Если имеет значение `Yes` в строке соединения или имя источника данных.|

## <a name="new-andor-modified-connection-attributes"></a>Атрибуты соединения новый или измененный

Следующие предварительно подключением атрибуты либо были появился или изменены для поддержки проверки подлинности Azure Active Directory. Если атрибут соединения имеет соответствующие строки подключения или ключевое слово DSN и установлено, атрибут соединения имеет приоритет.

|Attribute|Тип|Значения|По умолчанию|Description|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`, `SQL_AU_PASSWORD`, `SQL_AU_AD_INTEGRATED`, `SQL_AU_AD_PASSWORD`, `SQL_AU_RESET`|(не задано)|См. описание `Authentication` выше ключевое слово. `SQL_AU_NONE`предоставляется для явного переопределения набор `Authentication` значение в строке соединения источника данных и/или пока `SQL_AU_RESET` отменяет атрибут, если он был задан, позволяя DSN или подключения строковое значение, которое имеет приоритет.|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|Указатель на `ACCESSTOKEN` или иметь значение NULL|NULL|_Только драйвер Windows_. Если значение null, указывает AzureAD токена доступа для использования. Это ошибка, чтобы указать маркер доступа, а также `UID`, `PWD`, `Trusted_Connection`, или `Authentication` ключевых слов строки подключения или их эквивалентные атрибутов.|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(см. описание)|Управляет шифрованием соединения. `SQL_EN_OFF`и `SQL_EN_ON` отключения и включения шифрования, соответственно. Если значение атрибута перед `Authentication` не является параметром _нет_ или `SQL_COPT_SS_ACCESS_TOKEN` имеет значение, и `Encrypt` не указан в строке соединения или имя источника данных, значение по умолчанию — `SQL_EN_ON`. В противном случае — значение по умолчанию — `SQL_EN_OFF`. Действительное значение этого атрибута элементы управления [шифрование будет использоваться для подключения.](https://docs.microsoft.com/en-us/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|Не поддерживается в Azure Active Directory, поскольку изменения паролей AAD участникам не могут быть реализованы через соединение ODBC. <br><br>Истечение срока действия пароля для проверки подлинности SQL Server появился в SQL Server 2005. `SQL_COPT_SS_OLDPWD` Был добавлен атрибут, чтобы разрешить клиенту предоставлять старый и новый пароль для соединения. Если задано это свойство, поставщик не будет использовать пул соединений для первого и последующих соединений, поскольку строка подключения будет содержать «старый пароль», который уже изменен.|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_Рекомендуется использовать_; используйте `SQL_COPT_SS_AUTHENTICATION` значение `SQL_AU_AD_INTEGRATED` вместо него. <br><br>Принудительно использовать проверку подлинности Windows (Kerberos в Linux и macOS) для проверки доступа по имени входа сервера. Если используется проверка подлинности Windows, драйвер пропускает идентификатор значения пользователя и пароля предоставляется как часть `SQLConnect`, `SQLDriverConnect`, или `SQLBrowseConnect` обработки.|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Добавление пользовательского интерфейса для Azure Active Directory (только для драйверов Windows)

Настройка источника данных и подключение пользовательских интерфейсов драйвера дополненные Дополнительные параметры, необходимые для использования проверки подлинности в Azure AD.

### <a name="creating-and-editing-dsns-in-the-ui"></a>Создание и изменение источников данных в пользовательском Интерфейсе

Существует возможность использовать новый Azure AD параметры проверки подлинности при создании или изменении существующего источника данных с помощью программы установки драйвера пользовательского интерфейса:

`Authentication=ActiveDirectoryIntegrated`для проверки подлинности в Azure Active Directory Integrated SQL Azure

![CreateNewDSN3.png](windows/CreateNewDSN3.png)

`Authentication=ActiveDirectoryPassword`для проверки подлинности имя пользователя и пароль Azure Active Directory для SQL Azure

![CreateNewDSN4.png](windows/CreateNewDSN4.png)

`Authentication=SqlPassword`для проверки подлинности имя пользователя и пароль SQL Server (Azure или иным образом)

![CreateNewDSN.png](windows/CreateNewDSN.png)

`Trusted_Connection=Yes`для Windows SSPI устаревших встроенная проверка подлинности

![CreateNewDSN2.png](windows/CreateNewDSN2.png)

Четыре варианта соответствуют `Trusted_Connection=Yes` (существующие предыдущих версий Windows SSPI-только для проверки подлинности) и `Authentication=` `ActiveDirectoryIntegrated`, `SqlPassword`, и `ActiveDirectoryPassword`соответственно.

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect строки (только для драйверов Windows)

Диалоговое окно запроса, отображаться SQLDriverConnect, когда он запрашивает сведения, необходимые для завершения подключения содержит два новых параметра для проверки подлинности Azure AD:

![SQLServerLogin.png](windows/SQLServerLogin.png)

Эти параметры соответствуют же четыре, доступных в программе установки DSN выше пользовательского интерфейса.

### <a name="example-connection-strings"></a>Примеры строк подключения
1. Проверка подлинности SQL Server — устаревший синтаксис. Сертификат сервера не проверяется, и используется только в том случае, если сервер инициирует его шифрование. Имя пользователя и пароль передаются в строке подключения.
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. Проверка подлинности SQL — новый синтаксис. Клиент запрашивает шифрование (значение по умолчанию `Encrypt` — `true`) и получает сертификат сервера проверяется, независимо от того, параметры шифрования (если не `TrustServerCertificate` равно `true`). Имя пользователя и пароль передаются в строке подключения.
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. Встроенная проверка подлинности Windows (Kerberos в Linux и macOS) с помощью интерфейса SSPI (SQL Server или SQL IaaS) — текущего синтаксиса. Сертификат сервера не проверяется, если шифрование не используется. 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Только драйвер Windows_.) Встроенная проверка подлинности Windows с помощью SSPI (если в целевую базу данных в SQL Server или SQL IaaS) — новый синтаксис. Клиент запрашивает шифрование (значение по умолчанию `Encrypt` — `true`) и получает сертификат сервера проверяется, независимо от того, параметры шифрования (если не `TrustServerCertificate` равно `true`). 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. Имя пользователя и пароль проверки подлинности AAD (если целевая база данных находится в базе данных SQL Azure). Получает проверку сертификата сервера, независимо от того, параметры шифрования (если не `TrustServerCertificate` равно `true`). Имя пользователя и пароль передаются в строке подключения. 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Только драйвер Windows_.) Встроенная проверка подлинности Windows, с помощью ADAL, которая включает в себя активирует учетные данные Windows для маркер доступа выдан AAD, при условии, что целевая база данных находится в базе данных SQL Azure. Получает проверку сертификата сервера, независимо от того, параметры шифрования (если не `TrustServerCertificate` равно `true`). 
`server=Server;database=Database; Authentication=ActiveDirectoryIntegrated;`

> [!NOTE] 
>- При использовании новых параметров Active Directory с драйвером Windows ODBC, убедитесь, что [библиотеку аутентификации Active Directory для SQL Server](http://go.microsoft.com/fwlink/?LinkID=513072) установлен. Драйверы Linux и macOS все дополнительные зависимости, для проверки подлинности в Azure Active Directory не требуется.
>- Чтобы подключиться с помощью SQL Server учетная запись пользователя и паролем, теперь можно использовать новый `SqlPassword` параметр, который рекомендуется специально для SQL Azure, так как этот параметр позволяет выполнять более безопасные соединения по умолчанию.
>- Чтобы подключиться с помощью Azure Active Directory учетной записи пользователя и пароль, укажите `Authentication=ActiveDirectoryPassword` в строке подключения и `UID` и `PWD` ключевые слова, имя пользователя и пароль, соответственно.
>- Чтобы подключиться с помощью интеграции с Windows или проверки подлинности Active Directory Integrated (только для Windows драйвер), укажите `Authentication=ActiveDirectoryIntegrated` в строке подключения. Драйвер автоматически выберет режим проверку подлинности пользователя. `UID`и `PWD` не должен быть указан.

## <a name="authenticating-with-an-access-token-windows-driver-only"></a>Проверка подлинности с помощью токена доступа (только для Windows драйвер)

`SQL_COPT_SS_ACCESS_TOKEN` Атрибута предварительного соединения позволяет использовать маркер доступа, полученный из Azure AD для проверки подлинности, а не имя пользователя и пароль, а также осуществляется обход согласования и получение токена доступа с помощью драйвера. Чтобы использовать маркер доступа, задайте `SQL_COPT_SS_ACCESS_TOKEN` атрибут соединения к указателю на `ACCESSTOKEN` структуры:

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

`ACCESSTOKEN` — Это структура переменной длины, состоящий из 4-байтовый _длина_ следуют _длина_ байт непрозрачные данные, которые образуют маркер доступа. Из-за как SQL Server обрабатывает маркеры доступа, один, полученных через [OAuth 2.0](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-scenarios) ответа JSON необходимо развернуть, чтобы каждый байт следуют 0, заполнение байт, аналогично UCS-2 Строка, содержащая только символы ASCII, однако маркер Непрозрачное значение и длины, указанной в байтах, не должны содержать символ завершения null. Из-за их существенное ограничений, длина и формат, этот метод проверки подлинности, доступен только программно через `SQL_COPT_SS_ACCESS_TOKEN` атрибута coonnection; нет соответствующего источника данных или ключевое слово строки подключения. Строка подключения не должна содержать `UID`, `PWD`, `Authentication`, или `Trusted_Connection` ключевые слова.

## <a name="azure-active-directory-authentication-sample-code"></a>Пример кода проверки подлинности Azure Active Directory

Ниже приведен пример кода, необходимого для подключения к SQL Server с помощью Azure Active Directory с помощью ключевых слов соединения. Обратите внимание, что нет необходимости менять код приложения. Строка подключения или DSN, если он используется, имеет только изменения, необходимые для использования AAD для проверки подлинности:
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
Ниже приведен пример кода, необходимого для подключения к SQL Server с помощью Azure Active Directory с помощью проверки подлинности маркера доступа. В этом случае необходимо изменить код приложения для обработки токена доступа и установить атрибут связанного соединения.
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

## <a name="see-also"></a>См. также:
[Поддержка проверки подлинности на основе маркеров для базы данных SQL Azure с помощью проверки подлинности Azure AD](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

