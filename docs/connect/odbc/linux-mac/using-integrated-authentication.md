---
title: Использование встроенной проверки подлинности | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- integrated authentication
ms.assetid: 9499ffdf-e0ee-4d3c-8bca-605371eb52d9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0edf87997b8b53266e7597b392bb217288590636
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810152"
---
# <a name="using-integrated-authentication"></a>Использование встроенной проверки подлинности
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

[!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в Linux и macOS поддерживает соединения, использующие встроенную проверку подлинности Kerberos. Он поддерживает центр распространения ключей (KDC) Kerberos MIT и работает с общим API служб безопасности (GSSAPI) и библиотеками Kerberos версии 5.
  
## <a name="using-integrated-authentication-to-connect-to-includessnoversionincludesssnoversion-mdmd-from-an-odbc-application"></a>Использование встроенной проверки подлинности для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] из приложения ODBC  

Вы можете включить встроенную проверку подлинности Kerberos, указав **Trusted_Connection=yes** в строке подключения для **SQLDriverConnect** или **SQLConnect**. Пример:  

```
Driver='ODBC Driver 13 for SQL Server';Server=your_server;Trusted_Connection=yes  
```
  
При подключении с DSN, можно также добавить **Trusted_Connection = yes** в запись имени DSN в `odbc.ini`.
  
`-E` Параметр `sqlcmd` и `-T` параметр `bcp` также может использоваться для указания встроенной проверки подлинности; см. в разделе [соединение с помощью **sqlcmd** ](../../../connect/odbc/linux-mac/connecting-with-sqlcmd.md) и [ Соединение с помощью **bcp** ](../../../connect/odbc/linux-mac/connecting-with-bcp.md) Дополнительные сведения.

Убедитесь в том, что субъект клиента, который будет соединяться с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], уже прошел проверку подлинности с помощью Kerberos KDC.
  
**ServerSPN** и **FailoverPartnerSPN** не поддерживаются.  
  
## <a name="deploying-a-linux-or-macos-odbc-driver-application-designed-to-run-as-a-service"></a>Развертывание Linux или macOS, драйвер ODBC приложение разработано для выполнения в качестве службы

Системный администратор может развернуть приложение для запуска в качестве службы, которое использует проверку подлинности Kerberos для подключения к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
Сначала необходимо настроить Kerberos в клиенте, а затем убедиться в том, что приложение может использовать учетные данные Kerberos субъекта по умолчанию.

Убедитесь в том, что вы используете `kinit` или PAM (подключаемый модуль проверки подлинности) для получения и кэширования TGT для субъекта, используемого соединением, одним из следующих способов:  
  
-   Запустите `kinit`, передав имя и пароль субъекта.  
  
-   Запустите `kinit`, передав имя субъекта и расположение файла keytab, который содержит ключ субъекта, созданный `ktutil`.  
  
-   Убедитесь в том, что вход в систему был выполнен с помощью PAM Kerberos (подключаемый модуль проверки подлинности).

Когда приложение запускается в виде службы, обновляйте учетные данные Kerberos, чтобы обеспечить постоянную доступность службы, так как учетные данные намеренно имеют срок действия. Драйвер ODBC не обновляйте учетные данные. Убедитесь в наличии `cron` заданий или скрипт, который периодически выполняют обновление учетных данных до их истечения срока действия. Чтобы избежать запроса пароля для каждого обновления, можно использовать файла keytab.  
  
Статья[Конфигурация и использование Kerberos](http://commons.oreilly.com/wiki/index.php/Linux_in_a_Windows_World/Centralized_Authentication_Tools/Kerberos_Configuration_and_Use) содержит сведения о способах применения Kerberos для служб в Linux.
  
## <a name="tracking-access-to-a-database"></a>Отслеживание доступа к базе данных

Администратор базы данных может создать журнал аудита доступа к базе данных при использовании системных учетных записей для доступа к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью встроенной проверки подлинности.  
  
Для входа в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используется системная учетная запись, а в Linux нет никаких функций для олицетворения контекста безопасности. Таким образом, для определения пользователя требуется нечто большее.
  
Для аудита действий в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] от имени пользователей, отличных от системной учетной записи, приложение должно использовать [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE AS**.  
  
Для повышения производительности приложение может использовать организацию пулов соединений со встроенной проверкой подлинности и аудитом. Однако совмещение организации пулов соединений, встроенной проверки подлинности и аудита создает угрозу безопасности, так как диспетчер драйверов unixODBC позволяет различным пользователям повторно использовать подключения из пула. Дополнительные сведения см. в статье [Организация пулов соединений ODBC](http://www.unixodbc.org/doc/conn_pool.html).  

Перед повторным использованием приложение должно сбросить соединения в пуле, выполнив `sp_reset_connection`.  

## <a name="using-active-directory-to-manage-user-identities"></a>Использование Active Directory для управления удостоверениями пользователей

Администратору системы приложений не требуется управлять отдельными наборами учетных данных входа для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Можно настроить Active Directory в качестве центра распространения ключей (KDC) для встроенной проверки подлинности. См. в разделе [Microsoft Kerberos](/windows/desktop/SecAuthN/microsoft-kerberos) Дополнительные сведения.

## <a name="using-linked-server-and-distributed-queries"></a>Использование связанного сервера и распределенных запросов

Разработчики могут развернуть приложение, которое использует связанный сервер или распределенные запросы, без администратора базы данных, обслуживающего отдельные наборы учетных данных SQL. В этом случае разработчику необходимо настроить в приложении использование встроенной проверки подлинности:  
  
-   Пользователь входит на клиентский компьютер и выполняет проверку подлинности для сервера приложений.  
  
-   Сервер приложений осуществляет проверку подлинности в качестве другой базы данных и подключается к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] проходит проверку подлинности как пользователь базы данных в другой базе данных ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
После настройки встроенной проверки подлинности учетные данные передаются связанному серверу.  
  
## <a name="integrated-authentication-and-sqlcmd"></a>Встроенная проверка подлинности и sqlcmd
Чтобы получить доступ к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью встроенной проверки подлинности, используйте параметр `-E` программы `sqlcmd`. Убедитесь, что учетная запись, которая выполняет `sqlcmd` связан с участником клиента Kerberos по умолчанию.

## <a name="integrated-authentication-and-bcp"></a>Встроенная проверка подлинности и bcp
Чтобы получить доступ к [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью встроенной проверки подлинности, используйте параметр `-T` программы `bcp`. Убедитесь, что учетная запись, которая выполняет `bcp` связан с участником клиента Kerberos по умолчанию. 
  
Это ошибка для использования `-T` с `-U` или `-P` параметр.
  
## <a name="supported-syntax-for-an-spn-registered-by-includessnoversionincludesssnoversion-mdmd"></a>Поддерживаемый синтаксис для имени субъекта-службы, зарегистрированного [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]

В именах субъектов-служб в атрибутах или строке подключения применяется следующий синтаксис:  

|Синтаксис|Описание|  
|----------|---------------|  
|MSSQLSvc/*fqdn*:*port*|Сформированное поставщиком имя участника-службы для экземпляра по умолчанию, когда используется протокол TCP. *port* — номер TCP-порта. *fqdn* — полное доменное имя.|  
  
## <a name="authenticating-a-linux-or-macos-computer-with-active-directory"></a>Проверка подлинности компьютера Linux или macOS с помощью Active Directory

Чтобы настроить протокол Kerberos, введите данные в `krb5.conf` файл. `krb5.conf` в `/etc/` , но можно сослаться на другой файл, например с помощью синтаксиса `export KRB5_CONFIG=/home/dbapp/etc/krb5.conf`. Ниже представлен пример файла `krb5.conf`.  
  
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
  
Если компьютер Linux или macOS настроен для использования конфигурации протокола DHCP (Dynamic Host) с Windows DHCP-сервера на DNS-серверы для использования, можно использовать **dns_lookup_kdc = true**. Теперь можно использовать Kerberos для входа в вашем домене, выполнив команду `kinit alias@YYYY.CORP.CONTOSO.COM`. Параметры, передаваемые `kinit` чувствительны к регистру и [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] компьютер, настроенный для нахождения в домене должен иметь этот пользователь `alias@YYYY.CORP.CONTOSO.COM` добавлены для имени входа. Теперь вы можете использовать доверительные соединения (**Trusted_Connection=YES** в строке подключения, **bcp -T** или **sqlcmd -E**).  
  
Время на компьютере Linux или macOS и время на Центр распространения ключей Kerberos (KDC), необходимо закрыть. Убедитесь в том, что системное время задано правильно, например с помощью протокола NTP.  

При сбое проверки подлинности Kerberos драйвер ODBC в Linux или macOS не использует проверку подлинности NTLM.  

Дополнительные сведения о проверке подлинности компьютеров Linux или macOS с помощью Active Directory, см. в разделе [проверки подлинности клиентов Linux с помощью Active Directory](http://technet.microsoft.com/magazine/2008.12.linux.aspx#id0060048) и [советы и рекомендации по интеграции OS X с Active Directory](http://training.apple.com/pdf/Best_Practices_for_Integrating_OS_X_with_Active_Directory.pdf). Дополнительные сведения о настройке Kerberos см. в разделе [MIT Kerberos документации](https://web.mit.edu/kerberos/krb5-1.12/doc/index.html).

## <a name="see-also"></a>См. также:  
[Указания по программированию](../../../connect/odbc/linux-mac/programming-guidelines.md)

[Заметки о выпуске](../../../connect/odbc/linux-mac/release-notes.md)

[Использование Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md)
