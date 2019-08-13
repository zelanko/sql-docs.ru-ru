---
title: Руководство. Использование проверки подлинности Active Directory для SQL Server на Linux
titleSuffix: SQL Server
description: В этом руководстве приводятся инструкции по настройке проверки подлинности Active Directory для SQL Server на Linux.
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.date: 04/01/2019
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 69bbeb31f8da4023bd0630ae0d944165407e2dec
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68027332"
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
* установить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:
  * [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server (SLES)](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Присоединение узла [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] к домену Active Directory

Узел SQL Server на Linux необходимо присоединить к контроллеру домена Active Directory. Сведения о присоединении к домену Active Directory см. в статье [Присоединение узла SQL Server на Linux к домену Active Directory](sql-server-linux-active-directory-join-domain.md).

## <a id="createuser"></a> Создание пользователя Active Directory (или управляемой учетной записи службы) для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задание имени субъекта-службы

> [!NOTE]
> В следующих инструкциях применяется [полное доменное имя](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Если вы используете **Azure**, необходимо **[создать это имя](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** , прежде чем продолжить.

1. В контроллере домена выполните команду PowerShell [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx), чтобы создать пользователя Active Directory с бессрочным паролем. В приведенном ниже примере используется имя учетной записи `mssql`, однако оно может быть любым. Вы получите запрос на ввод нового пароля для учетной записи.

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > В целях безопасности рекомендуется использовать для SQL Server выделенную учетную запись Active Directory, чтобы учетные данные SQL Server не использовались другими службами. Однако при необходимости можно выбрать существующую учетную запись Active Directory, если вы знаете ее пароль (он потребуется для создания файла KEYTAB в следующем шаге).

2. Укажите значение ServicePrincipalName (имя субъекта-службы) для этой учетной записи с помощью средства **setspn.exe**. Формат имени субъекта-службы должен быть в точности таким же, как в приведенном ниже примере. Чтобы определить полное доменное имя хост-компьютера [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], выполните команду `hostname --all-fqdns` в узле [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. TCP-портом должен быть порт 1433, если вы не настроили для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] другой номер порта.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   setspn -A MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Если возникнет ошибка `Insufficient access rights`, узнайте у администратора вашего домена, достаточно ли у вас разрешений для задания имени субъекта-службы для этой учетной записи.
   >
   > Если в будущем вы измените TCP-порт, необходимо будет еще раз выполнить команду **setspn** с новым номером порта. Кроме того, необходимо будет добавить новое имя субъекта-службы в файл KEYTAB службы SQL Server, выполнив инструкции в следующем разделе.

Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Настройка KEYTAB-файла службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]

Настраивать KEYTAB-файлы службы SQL Server можно двумя способами. Первый способ предполагает использование учетной записи компьютера (имени участника-пользователя), а второй — управляемой учетной записи службы (MSA) в конфигурации KEYTAB. Оба механизма в равной степени функциональны, поэтому вы можете выбрать тот из них, который лучше подходит для вашей среды.

В обоих случаях требуется имя субъекта-службы, созданное ранее, и его необходимо зарегистрировать в файле KEYTAB.

Чтобы настроить KEYTAB-файла службы SQL Server, выполните указанные ниже действия.

1. Настройте [записи имени субъекта-службы в файле KEYTAB](#spn), как описано в следующем разделе.

1. Затем добавьте в KEYTAB-файл [имя участника-пользователя](#upn) (вариант 1) или [управляемую учетную запись службы](#msa) (вариант 2), выполнив инструкции в соответствующих разделах.

> [!IMPORTANT]
> При изменении пароля для имени участника-пользователя, управляемой учетной записи службы или учетной записи, которой назначены имена субъектов-служб, необходимо обновить файл KEYTAB, указав новый пароль и номер версии ключа (KVNO). В некоторых службах смена паролей может происходить автоматически. Проверьте политики смены паролей для нужных учетных записей и приведите их в соответствие с запланированными действиями по обслуживанию, чтобы избежать непредвиденных простоев.

### <a id="spn"></a> Записи имени субъекта-службы в файле KEYTAB

1. Определите номер версии ключа (KVNO) для учетной записи Active Directory, созданной в предыдущем шаге. Обычно он имеет значение 2, но может быть другим целым числом, если пароль учетной записи менялся несколько раз. На хост-компьютере SQL Server выполните следующие команды:

   ```bash
   kinit user@CONTOSO.COM
   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM
   ```

   > [!NOTE]
   > Распространение имен субъектов-служб в домене может занять несколько минут, особенно если домен большой. Если возникнет ошибка `kvno: Server not found in Kerberos database while getting credentials for MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM`, подождите несколько минут и повторите попытку.  

1. Запустите **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Добавьте в KEYTAB записи для каждого имени субъекта-службы с помощью следующих команд:

   ```bash
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   ```

1. Запишите содержимое KEYTAB в файл и выйдите из программы ktutil:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

   > [!NOTE]
   > Программа **ktutil** не проверяет пароль, поэтому при появлении запроса его нужно ввести правильно.

### <a id="upn"></a> Вариант 1. Настройка KEYTAB с использованием имени участника-пользователя

Добавьте в KEYTAB учетную запись компьютера с помощью **ktutil**. Учетная запись компьютера (также называемая именем участника-пользователя) содержится в файле **/etc/krb5.keytab** в формате `<hostname>$@<realm.com>` (например, `sqlhost$@CONTOSO.COM`). Скопируйте эти записи из файла **/etc/krb5.keytab** в файл **mssql.keytab**.

1. Запустите **ktuil** с помощью следующей команды:

   ```bash
   sudo ktutil
   ```

1. Используйте команду **rkt** для считывания всех записей из файла **/etc/krb5.keytab**.

   ```bash
   rkt /etc/krb5.keytab
   ```

1. Затем выведите список записей.

   ```bash
   list
   ```

1. Удалите записи, не являющиеся именами участников-пользователей, по номеру слота. Удаляйте записи по одной за раз, выполняя следующую команду:

   ```bash
   delent <slot num>
   ```

   > [!IMPORTANT]
   > При удалении записи, например слота 1, оставшиеся значения смещаются вверх на одну позицию. Это означает, что при удалении записи в слоте 1 запись из слота 2 перемещается в слот 1.

1. Еще раз выведите список записей, пока не останутся только записи имен участников-пользователей.

   ```bash
   list
   ```

1. Когда останутся только записи имен участников-пользователей, добавьте эти значения в файл **mssql.keytab**:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   ```

1. Выйдите из **ktutil**.

   ```bash
   quit
   ```

### <a id="msa"></a> Вариант 2.  Настройка KEYTAB с использованием управляемой учетной записи службы

Для использования управляемой учетной записи службы необходимо создать KEYTAB-файл Kerberos SQL Server. Он должен содержать все [имена субъектов-служб, зарегистрированные в первом шаге](#spn), и учетные данные управляемой учетной записи службы, в которой зарегистрированы имена субъектов-служб. 

1. После создания записей имен субъектов-служб в KEYTAB выполните следующие команды на компьютере Linux, присоединенном к домену:

   ```bash
   kinit <AD user>
   kvno <any SPN registered in step 1>
      <spn>@CONTOSO.COM: kvno = <KVNO>
   ```

   Будет выведен номер KVNO для учетной записи пользователя, назначенной владельцем имени субъекта-службы. Для выполнения этого шага имя субъекта-службы должно было быть назначено управляемой учетной записи службы во время ее создания. Если имя субъекта-службы не было назначено управляемой учетной записи службы, отображаемый номер KVNO будет относиться к текущему владельцу имени субъекта-службы и будет неправильным для данной конфигурации.  

1. Запустите **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Добавьте управляемую учетную запись службы с помощью следующих двух команд:

   ```bash
   addent -password -p <MSA> -k <kvno from command above> -e aes256-cts-hmac-sha1-96
   addent -password -p <MSA> -k <kvno from command above> -e rc4-hmac
   ```

1. Запишите содержимое KEYTAB в файл и выйдите из программы ktutil:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

1. При использовании управляемой учетной записи службы для доступа к KEYTAB-файлу необходимо задать соответствующий параметр конфигурации с помощью средства **mssql-conf**. Приведенные ниже значения должны содержаться в файле **/var/opt/mssql/mssql.conf**.

   ```bash
   sudo mssql-conf set network.privilegedadaccount <MSA_Name>
   ```

   > [!NOTE]
   > Включите только имя управляемой учетной записи службы, но не имя домена и учетной записи.

## <a id="securekeytab"></a> Защита KEYTAB-файла

Любой пользователь, имеющий доступ к KEYTAB-файлу, может олицетворять SQL Server в домене, поэтому необходимо ограничить доступ к файлу так, чтобы только учетная запись mssql имела доступ для чтения:

```bash
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```

## <a id="keytabkerberos"></a> Настройка SQL Server для использования KEYTAB-файла для проверки подлинности Kerberos

Чтобы настроить использование KEYTAB-файла для проверки подлинности Kerberos при запуске SQL Server, выполните указанные ниже действия.

```bash
sudo mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```

Чтобы повысить производительность, можно отключить подключения UDP к контроллеру домена. При подключении к контроллеру домена UDP-подключения часто завершаются сбоем, поэтому в файле **/etc/krb5.conf** можно задать параметры конфигурации для пропуска вызовов UDP. Измените файл **/etc/krb5.conf**, задав следующие параметры:

```/etc/krb5.conf
[libdefaults]
udp_preference_limit=0
```

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

### <a name="ssms-on-a-domain-joined-windows-client"></a>SSMS в клиенте Windows, присоединенном к домену

Выполните вход в присоединенный к домену клиент Windows с помощью учетных данных домена. Убедитесь в том, что установлена среда SQL Server Management Studio, а затем подключитесь к экземпляру SQL Server (например, `mssql-host.contoso.com`), выбрав **проверку подлинности Windows** в диалоговом окне **Подключение к серверу**.

### <a name="ad-authentication-using-other-client-drivers"></a>Проверка подлинности Active Directory с использованием других клиентских драйверов

В приведенной ниже таблице представлены рекомендации для других клиентских драйверов.

| Клиентский драйвер | Рекомендация |
|---|---|
| **JDBC** | Используйте встроенную проверку подлинности Kerberos для подключения к SQL Server. |
| **интерфейс ODBC** | Используйте встроенную проверку подлинности. |
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

Сначала установите параметры **disablessd** и **enablekdcfromkrb5conf** в значение true, а затем перезапустите SQL Server:

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

## <a name="next-steps"></a>Следующие шаги

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
