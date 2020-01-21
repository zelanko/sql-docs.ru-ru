---
title: Руководство. Использование проверки подлинности Active Directory для SQL Server на Linux
titleSuffix: SQL Server
description: В этом руководстве приводятся инструкции по настройке проверки подлинности Active Directory (AD) для SQL Server на Linux.
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.date: 12/18/2019
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 90c0023c0de69c03f64d33ff64866b0e5ff4f5ba
ms.sourcegitcommit: 909b69dd1f918f00b9013bb43ea66e76a690400a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75924954"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>Руководство. Использование проверки подлинности Active Directory с SQL Server на Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этом руководстве описывается, как настроить в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на Linux поддержку проверки подлинности Active Directory, также известную как встроенная проверка подлинности. Общие сведения см. в статье [Проверка подлинности Active Directory для SQL Server на Linux](sql-server-linux-active-directory-auth-overview.md).

В этом руководстве рассматриваются следующие задачи:

> [!div class="checklist"]
> * присоединение узла [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] к домену Active Directory;
> * создание пользователя Active Directory для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и указание имени субъекта-службы;
> * настройка KEYTAB-файла службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)];
> * защита KEYTAB-файла;
> * настройка SQL Server для использования KEYTAB-файла для проверки подлинности Kerberos;
> * создание имен входа на основе Active Directory в Transact-SQL;
> * подключение к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью проверки подлинности Active Directory.

## <a name="prerequisites"></a>предварительные требования

Прежде чем настраивать проверку подлинности Active Directory, необходимо сделать следующее:

* настроить контроллер домена Active Directory (Windows) в сети;  
* установить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)];
  * [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server (SLES)](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Присоединение узла [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] к домену Active Directory

Присоедините узел SQL Server на Linux к контроллеру домена Active Directory. Сведения о присоединении к домену Active Directory см. в статье [Присоединение узла SQL Server на Linux к домену Active Directory](sql-server-linux-active-directory-join-domain.md).

## <a id="createuser"></a> Создание пользователя Active Directory (или управляемой учетной записи службы) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задание имени субъекта-службы

> [!NOTE]
> В следующих инструкциях применяется [полное доменное имя](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Если вы используете **Azure**, необходимо **[создать это имя](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** , прежде чем продолжить.

1. В контроллере домена выполните команду PowerShell [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx), чтобы создать пользователя Active Directory с бессрочным паролем. В приведенном ниже примере используется имя учетной записи `mssql`, однако оно может быть любым. Вы получите запрос на ввод нового пароля для учетной записи.

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > В целях безопасности рекомендуется использовать для SQL Server выделенную учетную запись Active Directory, чтобы учетные данные SQL Server не использовались другими службами. Однако при необходимости можно выбрать существующую учетную запись Active Directory, если вы знаете ее пароль (он потребуется для создания файла KEYTAB в следующем шаге). Кроме того, учетная запись должна быть включена для поддержки 128-разрядного и 256-разрядного шифрования Kerberos (атрибут **msDS-SupportedEncryptionTypes**) в учетной записи пользователя.

2. Укажите значение ServicePrincipalName (имя субъекта-службы) для этой учетной записи с помощью средства **setspn.exe**. Формат имени субъекта-службы должен быть в точности таким же, как в приведенном ниже примере. Чтобы определить полное доменное имя хост-компьютера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], выполните команду `hostname --all-fqdns` в узле [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. TCP-портом должен быть порт 1433, если вы не настроили для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] другой номер порта.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   setspn -A MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Если возникнет ошибка `Insufficient access rights`, узнайте у администратора вашего домена, достаточно ли у вас разрешений для задания имени субъекта-службы для этой учетной записи. Учетная запись, используемая для регистрации имени субъекта-службы, потребует разрешений **Запись servicePrincipalName**. Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).
   >
   > Если в будущем вы измените TCP-порт, необходимо будет еще раз выполнить команду **setspn** с новым номером порта. Кроме того, необходимо будет добавить новое имя субъекта-службы в файл KEYTAB службы SQL Server, выполнив инструкции в следующем разделе.

Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Настройка KEYTAB-файла службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]

Для настройки проверки подлинности AD для SQL Server на Linux требуется учетная запись AD (учетная запись пользователя MSA или AD) и имя субъекта-службы, созданное в предыдущем разделе.

> [!IMPORTANT]
> При изменении пароля для учетной записи AD или учетной записи, которой назначены имена субъектов-служб, необходимо обновить файл KEYTAB, указав новый пароль и номер версии ключа (KVNO). В некоторых службах смена паролей может происходить автоматически. Проверьте политики смены паролей для нужных учетных записей и приведите их в соответствие с запланированными действиями по обслуживанию, чтобы избежать непредвиденных простоев.

### <a id="spn"></a> Записи имени субъекта-службы в файле KEYTAB

1. Определите номер версии ключа (KVNO) для учетной записи Active Directory, созданной в предыдущем шаге. Обычно он имеет значение 2, но может быть другим целым числом, если пароль учетной записи менялся несколько раз. На хост-компьютере SQL Server выполните следующие команды:

    - В приведенных ниже примерах предполагается, что `user` находится в домене `@CONTOSO.COM`. Измените имя пользователя и домена на свои значения.

   ```bash
   kinit user@CONTOSO.COM
   kvno user@CONTOSO.COM
   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM
   ```

   > [!NOTE]
   > Распространение имен субъектов-служб в домене может занять несколько минут, особенно если домен большой. Если возникнет ошибка `kvno: Server not found in Kerberos database while getting credentials for MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM`, подождите несколько минут и повторите попытку.</br></br> Приведенные выше команды будут работать только в том случае, если сервер присоединен к домену AD, который был рассмотрен в предыдущем разделе.

1. С помощью [**ktpass**](/windows-server/administration/windows-commands/ktpass)добавьте записи KEYTAB для каждого имени субъекта-службы с помощью следующих команд в командной строке компьютера Windows:

    - `<DomainName>\<UserName>` — может быть учетной записью пользователя MSA или AD
    - `@CONTOSO.COM` — используйте свое имя домена
    - `/kvno <#>` — замените `<#>` номером KVNO, полученным на предыдущем шаге
    - `<StrongPassword>` — используйте надежный пароль

   ```bash
   ktpass /princ MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM /ptype KRB5_NT_PRINCIPAL /crypto aes256-sha1 /mapuser <DomainName>\<UserName> /out mssql.keytab -setpass -setupn /kvno <#> /pass <StrongPassword>

   ktpass /princ MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM /ptype KRB5_NT_PRINCIPAL /crypto rc4-hmac-nt /mapuser <DomainName>\<UserName> /in mssql.keytab /out mssql.keytab -setpass -setupn /kvno <#> /pass <StrongPassword>

   ktpass /princ MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM /ptype KRB5_NT_PRINCIPAL /crypto aes256-sha1 /mapuser <DomainName>\<UserName> /in mssql.keytab /out mssql.keytab -setpass -setupn /kvno <#> /pass <StrongPassword>

   ktpass /princ MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM /ptype KRB5_NT_PRINCIPAL /crypto rc4-hmac-nt /mapuser <DomainName>\<UserName> /in mssql.keytab /out mssql.keytab -setpass -setupn /kvno <#> /pass <StrongPassword>

   ktpass /princ <UserName>@CONTOSO.COM /ptype KRB5_NT_PRINCIPAL /crypto aes256-sha1 /mapuser <DomainName>\<UserName> /in mssql.keytab /out mssql.keytab -setpass -setupn /kvno <#> /pass <StrongPassword>

   ktpass /princ <UserName>@CONTOSO.COM /ptype KRB5_NT_PRINCIPAL /crypto rc4-hmac-nt /mapuser <DomainName>\<UserName> /in mssql.keytab /out mssql.keytab -setpass -setupn /kvno <#> /pass <StrongPassword>
   ```

   > [!NOTE]
   > Приведенные выше команды позволяют использовать методы шифрования AES и RC4 для проверки подлинности AD. RC4 — это старый метод шифрования, и если требуется более высокая степень безопасности, то можно создать записи KEYTAB только с методом шифрования AES.

1. После выполнения приведенной выше команды у вас должен быть файл KEYTAB с именем mssql.keytab. Скопируйте файл на компьютер с SQL Server в папке `/var/opt/mssql/secrets`.

1. Защитите KEYTAB-файл.

    Любой пользователь, имеющий доступ к KEYTAB-файлу, может олицетворять SQL Server в домене, поэтому необходимо ограничить доступ к файлу так, чтобы только учетная запись mssql имела доступ для чтения:

    ```bash
    sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
    sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
    ```

1. Для указания учетной записи для доступа к KEYTAB-файлу необходимо задать соответствующий параметр конфигурации с помощью средства **mssql-conf**.

   ```bash
   sudo mssql-conf set network.privilegedadaccount <username>
   ```

   > [!NOTE]
   > Включайте только имя пользователя, а не имя_домена\имя_пользователя или username@domain. SQL Server сам добавляет имя домена вместе с этим именем пользователя при использовании.

1. Чтобы настроить использование KEYTAB-файла для проверки подлинности Kerberos при запуске SQL Server, выполните указанные ниже действия.

    ```bash
    sudo mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
    sudo systemctl restart mssql-server
    ```

    > [!TIP]
    > Чтобы повысить производительность, можно отключить подключения UDP к контроллеру домена. При подключении к контроллеру домена UDP-подключения часто завершаются сбоем, поэтому в файле **/etc/krb5.conf** можно задать параметры конфигурации для пропуска вызовов UDP. Измените файл **/etc/krb5.conf**, задав следующие параметры:
    > ```bash
    > /etc/krb5.conf
    > [libdefaults]
    > udp_preference_limit=0
    > ```

Теперь все готово для использования имен входа на основе Active Directory в SQL Server.

## <a id="createsqllogins"></a> Создание имен входа на основе Active Directory в Transact-SQL

1. Подключитесь к SQL Server и создайте имя входа на основе Active Directory:

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

1. Убедитесь в том, что имя входа теперь приводится в представлении системного каталога [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md):

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> Подключение к SQL Server с помощью проверки подлинности Active Directory

Выполните вход на клиентский компьютер, используя учетные данные домена. Теперь можно подключаться к SQL Server с помощью проверки подлинности Active Directory, не вводя пароль повторно. Если создать имя входа для группы Active Directory, все пользователи Active Directory, входящие в эту группу, смогут подключаться одинаковым образом.

Параметр строки подключения, предписывающий использование проверки подлинности Active Directory для клиентов, зависит от драйвера. Рассмотрим примеры в следующих разделах.

### <a name="sqlcmd-on-a-domain-joined-linux-client"></a>sqlcmd в клиенте Linux, присоединенном к домену

Выполните вход в присоединенный к домену клиент Linux с помощью **ssh** и учетных данных домена:

```bash
ssh -l user@contoso.com client.contoso.com
```

Убедитесь в том, что установлен пакет [mssql-tools](sql-server-linux-setup-tools.md), а затем подключитесь с помощью **sqlcmd**, не указывая учетные данные:

```bash
sqlcmd -S mssql-host.contoso.com
```
В отличие от SQL Windows проверка подлинности Kerberos работает для локального подключения в SQL Linux. Однако вам по-прежнему необходимо предоставить полное доменное имя узла SQL Linux, а проверка подлинности AD не будет работать при попытке подключения к ".", "localhost", "127.0.0.1" и т. д.

### <a name="ssms-on-a-domain-joined-windows-client"></a>SSMS в клиенте Windows, присоединенном к домену

Выполните вход в присоединенный к домену клиент Windows с помощью учетных данных домена. Убедитесь в том, что установлена среда SQL Server Management Studio, а затем подключитесь к экземпляру SQL Server (например, `mssql-host.contoso.com`), выбрав **проверку подлинности Windows** в диалоговом окне **Подключение к серверу**.

### <a name="ad-authentication-using-other-client-drivers"></a>Проверка подлинности Active Directory с использованием других клиентских драйверов

В приведенной ниже таблице представлены рекомендации для других клиентских драйверов.

| Клиентский драйвер | Рекомендация |
|---|---|
| **JDBC** | Используйте встроенную проверку подлинности Kerberos для подключения к SQL Server. |
| **ODBC** | Используйте встроенную проверку подлинности. |
| **ADO.NET** | Синтаксис строки подключения. |

## <a id="additionalconfig"></a> Дополнительные параметры конфигурации

Если вы используете сторонние служебные программы, такие как [PBIS](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/) или [Centrify](https://www.centrify.com/), для присоединения узла Linux к домену Active Directory и хотите настроить принудительное использование библиотеки openldap сервером SQL Server, можно настроить параметр **disablesssd** с помощью **mssql-conf** следующим образом:

```bash
sudo mssql-conf set network.disablesssd true
systemctl restart mssql-server
```

> [!NOTE]
> Некоторые служебные программы, такие как **realmd**, настраивают SSSD, а другие, например PBIS, VAS и Centrify, не настраивают SSSD. Если программа, применяемая для присоединения к домену Active Directory, не настраивает SSSD, рекомендуется присвоить параметру **disablesssd** значение `true`. Хотя это не обязательно, так как SQL Server будет пытаться использовать SSSD для Active Directory, прежде чем переходить на openldap в качестве резервного механизма, такая настройка повышает производительность благодаря тому, что SQL Server выполняет вызовы openldap напрямую в обход механизма SSSD.

Если контроллер домена поддерживает протокол LDAPS, можно настроить принудительное использование LDAPS для всех подключений SQL Server к контроллеру домена. Чтобы проверить возможность связи клиента с контроллером домена по LDAPS, выполните следующую команду bash: `ldapsearch -H ldaps://contoso.com:3269`. Чтобы настроить в SQL Server использование только протокола LDAPS, выполните следующие команды:

```bash
sudo mssql-conf set network.forcesecureldap true
systemctl restart mssql-server
```

В результате LDAPS через SSSD будет использоваться, если присоединение узла к домену Active Directory было выполнено с помощью пакета SSSD и параметр **disablesssd** не установлен в значение true. Если параметр **disablesssd** установлен в значение true и параметр **forcesecureldap** также имеет значение true, протокол LDAPS будет использоваться для вызовов библиотеки openldap, совершаемых сервером SQL Server.

### <a name="post-sql-server-2017-cu14"></a>Версии начиная с SQL Server 2017 с накопительным пакетом обновления 14

Начиная с SQL Server 2017 с накопительным пакетом обновления 14, если сервер SQL Server был присоединен к контроллеру домена Active Directory с помощью сторонних поставщиков и для него настроено использование вызовов openldap для общих операций просмотра в Active Directory путем задания значения true для параметра **disablesssd**, можно также с помощью параметра **enablekdcfromkrb5** настроить принудительное использование сервером SQL Server библиотеки krb5 для просмотра KDC вместо обратного просмотра DNS для сервера KDC.

Это может быть полезно в ситуациях, когда нужно вручную настроить контроллеры домена, с которыми пытается связаться SQL Server. Механизм библиотеки openldap используется посредством списка KDC в **krb5.conf**.

Сначала установите параметры **disablesssd** и **enablekdcfromkrb5conf** в значение true, а затем перезапустите SQL Server:

```bash
sudo mssql-conf set network.disablesssd true
sudo mssql-conf set network.enablekdcfromkrb5conf true
systemctl restart mssql-server
```

Затем настройте список KDC в файле **/etc/krb5.conf** следующим образом:

```/etc/krb5.conf
[realms]
CONTOSO.COM = {
  kdc = dcWithGC1.contoso.com
  kdc = dcWithGC2.contoso.com
}
```

> [!NOTE]
> Хотя делать это не рекомендуется, вы можете использовать служебные программы, такие как **realmd**, для настройки SSSD при присоединении узла Linux к домену и присвоить параметру **disablesssd** значение true, чтобы SQL Server использовал вызовы openldap вместо SSSD для вызовов, связанных с Active Directory.

## <a name="next-steps"></a>Дальнейшие действия

В этом руководстве были представлены пошаговые инструкции по настройке проверки подлинности Active Directory для SQL Server на Linux. Вы ознакомились с выполнением следующих задач:
> [!div class="checklist"]
> * присоединение узла [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] к домену Active Directory;
> * создание пользователя Active Directory для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и указание имени субъекта-службы;
> * настройка KEYTAB-файла службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)];
> * создание имен входа на основе Active Directory в Transact-SQL;
> * подключение к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с помощью проверки подлинности Active Directory.

Далее вы можете ознакомиться с другими сценариями обеспечения безопасности для SQL Server на Linux.

> [!div class="nextstepaction"]
> [Шифрование соединений с SQL Server на Linux](sql-server-linux-encrypted-connections.md)
