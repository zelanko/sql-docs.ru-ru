---
title: "С помощью встроенной проверки подлинности | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: integrated authentication
ms.assetid: 9499ffdf-e0ee-4d3c-8bca-605371eb52d9
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 162b94d551ea8625b6b22fafec61e19038dc2051
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="using-integrated-authentication"></a>Использование встроенной проверки подлинности
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

[!INCLUDE[msCoName](../../../includes/msconame_md.md)] Драйвер ODBC для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] в Linux и macOS поддерживает соединения, использующие Kerberos встроенной проверки подлинности. Он поддерживает MIT Kerberos распространения ключей центра (KDC) и работает с универсальной безопасности служб приложения программы интерфейса (GSSAPI) и Kerberos v5 библиотеки.
  
## <a name="using-integrated-authentication-to-connect-to-includessnoversionincludesssnoversionmdmd-from-an-odbc-application"></a>С помощью встроенной проверки подлинности для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] из приложения ODBC  

Можно включить встроенную проверку подлинности Kerberos, указав **Trusted_Connection = yes** в строке подключения для **SQLDriverConnect** или **SQLConnect**. Например:  

```
Driver='ODBC Driver 13 for SQL Server';Server=your_server;Trusted_Connection=yes  
```
  
При соединении с DSN, можно также добавить **Trusted_Connection = yes** в запись имени DSN в `odbc.ini`.
  
`-E` Параметр `sqlcmd` и `-T` параметр `bcp` ; см. также можно использовать встроенную проверку подлинности [соединение с помощью **sqlcmd** ](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md) и [ Соединение с помощью **bcp** ](../../../connect/odbc/linux-mac/connecting-with-bcp.md) для получения дополнительной информации.

Убедитесь, что субъект клиента, который собирается подключиться к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] уже прошел проверку подлинности с помощью Kerberos KDC.
  
**ServerSPN** и **FailoverPartnerSPN** не поддерживаются.  
  
## <a name="deploying-a-linux-or-macos-odbc-driver-application-designed-to-run-as-a-service"></a>Развертывание Linux или macOS приложения драйвера ODBC, разработанные для запуска в качестве службы

Системный администратор может развернуть приложение для запуска в качестве службы, использующей проверку подлинности Kerberos для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
Сначала необходимо настроить Kerberos на клиентском компьютере и убедитесь, что приложение может использовать учетные данные Kerberos субъекта по умолчанию.

Убедитесь, что при использовании `kinit` или PAM (подключаемый модуль проверки подлинности) для получения и кэширования TGT для субъекта, использует соединение через одну из следующих методов:  
  
-   Запустите `kinit`, передав имя и пароль.  
  
-   Запустите `kinit`, передав имя и расположение файла keytab, который содержит ключ субъекта, созданных `ktutil`.  
  
-   Убедитесь, что имя входа в систему выполнялась с использованием Kerberos PAM (подключаемый модуль проверки подлинности).

Если приложение выполняется как служба, так как срок действия учетных данных Kerberos намеренно, обновляйте учетные данные, чтобы обеспечить постоянную доступность службы. Драйвер ODBC не обновить учетные данные Убедитесь, что `cron` заданий или скрипт, который периодически выполняют обновление учетных данных до истечения срока их действия. Чтобы избежать запроса пароля для каждого обновления, можно использовать файл keytab.  
  
Статья[Конфигурация и использование Kerberos](http://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Centralized_Authentication_Tools/Kerberos_Configuration_and_Use) содержит сведения о способах применения Kerberos для служб в Linux.
  
## <a name="tracking-access-to-a-database"></a>Отслеживание доступа к базе данных

Администратор базы данных может создать журнал аудита доступа к базе данных при использовании системных учетных записей для доступа к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] встроенную проверку подлинности.  
  
Вход в систему [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] использует системную учетную запись и функции отсутствуют в Linux для олицетворения контекста безопасности. Таким образом, для определения пользователя требуется нечто большее.
  
Для аудита действий в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] от имени пользователей, отличной от учетной записи system, приложение должно использовать [!INCLUDE[tsql](../../../includes/tsql_md.md)] **EXECUTE AS**.  
  
Для повышения производительности приложение может использовать организацию пулов соединений со встроенной проверкой подлинности и аудитом. Тем не менее объединяя подключения пулов встроенной проверки подлинности и аудита создает угрозу безопасности, поскольку диспетчер драйверов unixODBC позволяет различным пользователям повторно использовать подключения в пуле. Дополнительные сведения см. в статье [Организация пулов соединений ODBC](http://www.unixodbc.org/doc/conn_pool.html).  

Перед повторным использованием приложение должно сбросить соединения в пуле, выполнив `sp_reset_connection`.  

## <a name="using-active-directory-to-manage-user-identities"></a>Использование Active Directory для управления удостоверениями пользователей

Системный администратор приложения не требуется управлять отдельными наборами учетных данных входа для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Можно настроить Active Directory в качестве центра распространения ключей (KDC) для встроенной проверки подлинности. В разделе [Microsoft Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747(v=vs.85).aspx) для получения дополнительной информации.

## <a name="using-linked-server-and-distributed-queries"></a>Использование связанного сервера и распределенных запросов

Разработчики могут развернуть приложение, которое использует связанный сервер или распределенные запросы, без администратора базы данных, обслуживающего отдельные наборы учетных данных SQL. В этом случае разработчику необходимо настроить приложение для использования встроенной проверки подлинности:  
  
-   Пользователь входит на клиентский компьютер и выполняет проверку подлинности для сервера приложений.  
  
-   Сервер приложений выполняет аутентификацию в качестве другой базы данных и подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]выполняет проверку подлинности как пользователь базы данных в другую базу данных ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)].  
  
После настройки встроенной проверки подлинности учетные данные передаются связанному серверу.  
  
## <a name="integrated-authentication-and-sqlcmd"></a>Встроенная проверка подлинности и sqlcmd
Чтобы получить доступ к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] с использованием встроенной проверки подлинности, используйте `-E` параметр `sqlcmd`. Убедитесь, что учетная запись, которая выполняется `sqlcmd` связан с участником клиента Kerberos по умолчанию.

## <a name="integrated-authentication-and-bcp"></a>Встроенная проверка подлинности и bcp
Чтобы получить доступ к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] с использованием встроенной проверки подлинности, используйте `-T` параметр `bcp`. Убедитесь, что учетная запись, которая выполняется `bcp` связан с участником клиента Kerberos по умолчанию. 
  
Будет ошибкой использовать `-T` с `-U` или `-P` параметр.
  
## <a name="supported-syntax-for-an-spn-registered-by-includessnoversionincludesssnoversionmdmd"></a>Поддерживаемый синтаксис для имени участника-службы, зарегистрированные с[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]

Синтаксис имен участников-служб в строку подключения или атрибуты соединения выглядит следующим образом:  

|Синтаксис|Описание|  
|----------|---------------|  
|MSSQLSvc/*fqdn*:*port*|Сформированное поставщиком имя участника-службы для экземпляра по умолчанию, когда используется протокол TCP. *port* — номер порта TCP. *fqdn* — полное доменное имя.|  
  
## <a name="authenticating-a-linux-or-macos-computer-with-active-directory"></a>Проверка подлинности Linux или macOS компьютера в Active Directory

Чтобы настроить Kerberos, введите данные в `krb5.conf` файла. `krb5.conf`в `/etc/` , но может ссылаться на другой файл, например с помощью синтаксиса `export KRB5_CONFIG=/home/dbapp/etc/krb5.conf`. Ниже приведен пример `krb5.conf` файла:  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
```  
  
Если компьютер Linux или macOS настроен для использования протокол динамической настройки узла (DHCP) с Windows DHCP-сервера на DNS-серверы для использования, можно использовать **dns_lookup_kdc = true**. Теперь можно использовать Kerberos для входа в домен с помощью команды `kinit alias@YYYY.CORP.CONTOSO.COM`. Параметры, передаваемые в `kinit` чувствительны к регистру и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] компьютер, настроенный для нахождения в домене должен иметь этот пользователь `alias@YYYY.CORP.CONTOSO.COM` добавлен для имени входа. Теперь могут использовать доверенные соединения (**Trusted_Connection = YES** в строке подключения, **bcp -T**, или **sqlcmd -E**).  
  
Время на компьютере Linux или macOS и время на Центр распространения ключей Kerberos (KDC), необходимо закрыть. Убедитесь, что системное время задано правильно, например с помощью протокола сетевого времени (NTP).  

При сбое проверки подлинности Kerberos, драйвер ODBC для Linux или macOS не использует проверку подлинности NTLM.  

Дополнительные сведения о проверке подлинности Linux и macOS компьютеров с помощью Active Directory см. в разделе [проверки подлинности клиентов Linux с помощью Active Directory](http://technet.microsoft.com/magazine/2008.12.linux.aspx#id0060048) и [советы и рекомендации по интеграции OS X с помощью Active Directory](http://training.apple.com/pdf/Best_Practices_for_Integrating_OS_X_with_Active_Directory.pdf). Дополнительные сведения о настройке Kerberos см. в разделе [документация Kerberos MIT](https://web.mit.edu/kerberos/krb5-1.12/doc/index.html).

## <a name="see-also"></a>См. также:  
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)

[С помощью Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md)
