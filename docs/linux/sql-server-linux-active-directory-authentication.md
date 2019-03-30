---
title: Учебник. Проверка подлинности Active Directory для SQL Server в Linux
titleSuffix: SQL Server
description: Этот учебник шаги конфигурации используется для проверки подлинности AAD для SQL Server в Linux.
author: meet-bhagdev
ms.date: 02/23/2018
ms.author: meetb
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 82f4df8607af55a4b50f0ecfaf7b66a8c088c43a
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2019
ms.locfileid: "58657938"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>Учебник. Использование проверки подлинности Active Directory с SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Это руководство содержит сведения о настройке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux для поддержки проверки подлинности Active Directory (AD), также известный как встроенная проверка подлинности. Дополнительные сведения см. в разделе [проверки подлинности Active Directory для SQL Server в Linux](sql-server-linux-active-directory-auth-overview.md).

Этот учебник состоит из следующих задач:

> [!div class="checklist"]
> * Присоединяйтесь к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену AD
> * Создание пользователя AD для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задать имя участника-службы
> * Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab службы
> * Создание имен входа на основе AD в Transact-SQL
> * Подключение к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с использованием проверки подлинности AD

> [!NOTE]
>
> Если вы хотите настроить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux для использования стороннего поставщика AD, см. в разделе [использование сторонних поставщиков Active Directory с SQL Server в Linux](./sql-server-linux-active-directory-third-party-providers.md).

## <a name="prerequisites"></a>предварительные требования

Перед настройкой проверки подлинности AD, вам потребуется:

* Настройка контроллера домена AD (Windows) в сети  
* Установка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
  * [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Присоединяйтесь к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену AD

Следуйте инструкциям ниже, чтобы присоединить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену Active Directory:

1. Используйте **[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)** для присоединения к домену AD хост-компьютере. Если это еще не сделано, установите realmd и пакеты клиента Kerberos на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютере, с помощью диспетчера пакетов дистрибутива Linux:

   ```bash
   # RHEL
   sudo yum install realmd krb5-workstation

   # SUSE
   sudo zypper install realmd krb5-client

   # Ubuntu
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Если пакет установки клиента Kerberos запросит имя области, введите имя домена прописными буквами.

   > [!NOTE]
   > В этом пошаговом руководстве используется «contoso.com» и «CONTOSO.COM» как примеры доменом и областью имен, соответственно. Следует заменить их своими собственными значениями. Эти команды чувствительны к регистру, поэтому убедитесь, что использовать прописные везде, где он используется в этом пошаговом руководстве.

1. Настройка вашей [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютер для использования IP-адрес контроллера домена AD в качестве имен DNS. 

   - **Ubuntu**:

      Изменить `/etc/network/interfaces` файл таким образом, чтобы контроллер домена AD IP-адрес указан в качестве dns-имени сервера. Например: 

      ```/etc/network/interfaces
      <...>
      # The primary network interface
      auto eth0
      iface eth0 inet dhcp
      dns-nameservers **<AD domain controller IP address>**
      dns-search **<AD domain name>**
      ```

      > [!NOTE]
      > Сетевой интерфейс (eth0) могут отличаться для разных компьютерах. Чтобы узнать, какой из них, вы используете, выполнения ifconfig и скопировать интерфейсе с IP-адресом и отправленных и полученных байтов.

      Изменив этот файл, перезапустите сетевую службу:

      ```bash
      sudo ifdown eth0 && sudo ifup eth0
      ```

      Теперь убедитесь, что ваш `/etc/resolv.conf` файл содержит строку, как в следующем примере:  

      ```/etc/resolv.conf
      nameserver **<AD domain controller IP address>**
      ```

   - **RHEL**:

     Изменить `/etc/sysconfig/network-scripts/ifcfg-eth0` файл (или другой интерфейс конфигурации, в файл соответствующим образом), чтобы контроллер домена AD IP-адрес указан в качестве DNS-сервера:

     ```/etc/sysconfig/network-scripts/ifcfg-eth0
     <...>
     PEERDNS=no
     DNS1=**<AD domain controller IP address>**
     ```

     Изменив этот файл, перезапустите сетевую службу:

     ```bash
     sudo systemctl restart network
     ```

     Теперь убедитесь, что ваш `/etc/resolv.conf` файл содержит строку, как в следующем примере:  

     ```/etc/resolv.conf
     nameserver **<AD domain controller IP address>**
     ```

   - **SLES**:

     Изменить `/etc/sysconfig/network/config` файл, чтобы IP-адрес контроллера домена AD, которые будут использоваться для запросов DNS и доменом AD находится в списке доменов поиска:

     ```/etc/sysconfig/network/config
     <...>
     NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
     ```

     Изменив этот файл, перезапустите сетевую службу:

     ```bash
     sudo systemctl restart network
     ```

     Теперь убедитесь, что ваш `/etc/resolv.conf` файл содержит строку, как в следующем примере:

     ```/etc/resolv.conf
     nameserver **<AD domain controller IP address>**
     ```

1. Присоединение к домену

   Когда вы подтвердите, что ваша служба DNS настроена правильно, присоединение к домену, выполнив следующую команду. Вы должны пройти аутентификацию с помощью учетной записи AD, имеет достаточные права в AD, чтобы присоединить машину к домену.

   В частности, эта команда создает новую учетную запись компьютера в AD, создайте `/etc/krb5.keytab` размещения файла keytab и Настройка домена в `/etc/sssd/sssd.conf`:

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   <...>
   * Successfully enrolled machine in realm
   ```

   > [!NOTE]
   > Если появится сообщение об ошибке, «не установлены необходимые пакеты», то необходимо установить эти пакеты с помощью диспетчера пакетов дистрибутив Linux, перед запуском `realm join` еще раз выполните команду.
   >
   > Если появляется ошибка «Недостаточные разрешения для присоединения к домену,» необходимо проконсультироваться с администратором домена, что вас недостаточно разрешений на присоединение компьютеров Linux к домену.
   >
   > Если появится сообщение об ошибке, «ответ контроллера Kerberos-домена не соответствует ожиданиям,» затем может не введен правильное имя пользователя. Имена областей чувствительны к регистру, обычно верхний регистр и могут быть идентифицированы с помощью команды `realm discover contoso.com`.
   
   > SQL Server использует SSSD и NSS для сопоставления учетных записей пользователей и групп идентификаторы безопасности (SID). SSSD должна быть настроена и запущена в порядке для SQL Server для создания имен входа AD успешно. Realmd обычно делает это автоматически в процессе присоединения к домену, но в некоторых случаях это необходимо сделать отдельно.
   >
   > См. ниже, чтобы настроить [SSSD вручную](https://access.redhat.com/articles/3023951), и [Настройка NSS для работы с SSSD](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/Configuring_Services#Configuration_Options-NSS_Configuration_Options)

5. Убедитесь, что домен настроен в `/etc/krb5.conf`
    ```/etc/krb5.conf
    [libdefaults]
    default_realm = CONTOSO.COM

    [realms]
    CONTOSO.COM = {
    }

    [domain_realm]
    contoso.com = CONTOSO.COM
    .contoso.com = CONTOSO.COM
    ```

  
6. Убедитесь, что теперь можно собрать сведения о пользователе из домена и что вы можете получить билет Kerberos от имени этого пользователя.

   В следующем примере используется **идентификатор**,  **[kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)**, и **[klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)** команд для этого.

   ```bash
   id user@contoso.com
   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM
   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   <...>
   ```

   > [!NOTE]
   > Если `id user@contoso.com` возвращает «Такой пользователь,» убедитесь, что успешно запустить службу SSSD, выполнив команду `sudo systemctl status sssd`. Если служба запущена, и по-прежнему отображается ошибка «Пользователь», попробуйте включить подробное ведение журнала для SSSD. Дополнительные сведения см. в документации Red Hat для [Устранение неполадок SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).
   >
   > Если `kinit user@CONTOSO.COM` возвращает, «ответ контроллера Kerberos-домена не соответствует ожиданиям при получении начальной учетные данные,» убедитесь, вы указали область в верхнем регистре.

Дополнительные сведения см. в документации Red Hat для [Discovering и присоединение доменов удостоверений](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html). 

## <a id="createuser"></a> Создание пользователя AD для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задать имя участника-службы

  > [!NOTE]
  > Далее шагах используется вашей [полное доменное имя](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Если вы используете **Azure**, вы должны **[создать](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** перед началом работы.

1. На контроллере домена запустите [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) команду PowerShell, чтобы создать нового пользователя AD с помощью пароля, срок действия не ограничен. В этом примере имена учетной записи «mssql», но имя учетной записи может быть любым. Вам будет предложено ввести новый пароль для учетной записи:

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > Это соображениям безопасности рекомендуется использовать выделенную учетную запись AD для SQL Server так, чтобы учетные данные SQL Server не совместно с другими службами, с помощью той же учетной записи. Тем не менее можно повторно использовать существующую учетную запись AD при желании, если вы знаете пароль учетной записи (требуется для создания файла keytab на следующем шаге).

2. Задайте ServicePrincipalName (SPN) для этой учетной записи с помощью `setspn.exe` средство. Имя участника-службы должен быть отформатирован в точности так, как указано в следующем примере. Полное доменное имя можно найти [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютере, выполнив `hostname --all-fqdns` на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла и TCP-порт должен быть 1433, если вы не настроили [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использовать другой номер порта.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Если возникает ошибка «не хватает прав,» необходимо убедитесь с администратором домена, что имеются достаточные разрешения для задания имени SPN в этой учетной записи.
   >
   > Если вы измените порт TCP в будущем, необходимо повторно запустить команду setspn с новый номер порта. Необходимо также добавить нового имени участника-службы keytab службы SQL Server, выполнив действия, описанные в следующем разделе.

3. Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab службы

1. Проверьте номер версии ключа (kvno) для учетной записи AD, созданной на предыдущем шаге. Обычно это 2, но это может быть другое целое число, если вы изменили пароль для учетной записи несколько раз. На [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютере, выполните следующую команду:

   ```bash
   kinit user@CONTOSO.COM

   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

   > [!NOTE]
   > Имена участников-служб может занять несколько минут для распространения через домен, особенно в том случае, если домен велико. Если появляется ошибка «kvno: Сервер не найден в базе данных Kerberos при получении учетных данных для MSSQLSvc /\*\*\<полное доменное имя компьютера-узла\>\*\*:\* \* \< TCP-порт\>\*\*\@CONTOSO.COM», подождите несколько минут и повторите попытку.

2. Создание файла keytab с **[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)** для пользователя AD, созданный на предыдущем шаге. При запросе введите пароль для этой учетной записи AD.

   ```bash
   sudo ktutil

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

   > [!NOTE]
   > Средство ktutil не проверки пароля, поэтому убедитесь, что введен правильно.

3. Добавьте учетную запись компьютера для вашего keytab с  **[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)**. (Также называемый UPN) учетной записи компьютера присутствует в `/etc/krb5.keytab` в форме "\<hostname\>$\@\<realm.com\>" (например sqlhost$\@CONTOSO.COM). Мы будет копировать эти записи из `/etc/krb5.keytab` для `mssql.keytab`.

   ```bash
   sudo ktutil

   # Read all entries from /etc/krb5.keytab
   ktutil: rkt /etc/krb5.keytab

   # List all entries
   ktutil: list

   # Delete all entries by their slot number which are not the UPN one at a
   # time.
   # Warning: when an entry is deleted (e.g. slot 1), all values slide up by
   # one to take its place (e.g. the entry in slot 2 moves to slot 1 when slot
   # 1's entry is deleted)
   ktutil: delent <slot num>
   ktutil: delent <slot num>
   ...

   # List all entries to ensure only UPN entries are left
   ktutil: list

   # When only UPN entries are left, append these values to mssql.keytab
   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

4. Все, кто имеет доступ к этому `keytab` файл может олицетворять [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в домене, поэтому убедитесь, что ограничение доступа к файлу таких только `mssql` учетная запись имеет доступ на чтение:

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
   sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
   ```

5. Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использовать этот `keytab` файл для проверки подлинности Kerberos:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
   sudo systemctl restart mssql-server
   ```

6. Необязательно. Отключите UDP-подключений к контроллеру домена для повышения производительности. Во многих случаях подключения по протоколу UDP всегда завершится ошибкой, при подключении к контроллеру домена, можно задать параметры конфигурации `/etc/krb5.conf` пропустить вызовы UDP. Изменить `/etc/krb5.conf` и задать следующие параметры:

   ```/etc/krb5.conf
   [libdefaults]
   udp_preference_limit=0
   ```

## <a id="createsqllogins"></a> Создание имен входа на основе AD в Transact-SQL

1. Подключение к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и создать новый, основанный на AD входа:

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

2. Убедитесь, что имя входа является теперь [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления системного каталога:

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> Подключение к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с использованием проверки подлинности AD

Войдите на клиентский компьютер, используя свои учетные данные домена. Теперь вы можете подключиться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] избежать повторного ввода пароля, с использованием проверки подлинности AD. При создании имени входа группы AD, таким же образом можно подключиться любой пользователь AD, являющийся членом этой группы.

Параметр строки подключения для клиентов на использование проверки подлинности AD зависит от того, какой драйвер используется. Рассмотрим следующие примеры:

* `sqlcmd` на присоединенных к домену клиента Linux

   Войдите на присоединенных к домену клиента Linux с помощью `ssh` и учетные данные домена:

   ```bash
   ssh -l user@contoso.com client.contoso.com
   ```

   Убедитесь, что вы установили [mssql-tools](sql-server-linux-setup-tools.md) пакета, затем через `sqlcmd` без указания учетных данных:

   ```bash
   sqlcmd -S mssql-host.contoso.com
   ```

* SSMS на клиенте Windows, присоединенных к домену

   Войдите на присоединенных к домену клиента Windows, используя свои учетные данные домена. Убедитесь, что [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] установлен, а затем подключиться к вашей [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] экземпляра (например «mssql-host.contoso.com»), указав **проверки подлинности Windows** в **соединение с сервером** диалоговое окно.

* С помощью других драйверов клиента проверки подлинности AD

  * JDBC: [С помощью встроенной проверки подлинности Kerberos для подключения к серверу SQL](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server)
  * ODBC. [Использование встроенной проверки подлинности](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)
  * ADO.NET: [Синтаксис строки соединения](https://msdn.microsoft.com/library/system.data.sqlclient.sqlauthenticationmethod(v=vs.110).aspx)

## <a name="performance-improvements"></a>Повышение производительности
Если вы Обратите внимание, что поиск учетной записи AD занимает некоторое время вы проверили AD конфигурация является допустимой с действия, описанные в [использование аутентификации Active Directory с помощью SQL Server в Linux с помощью сторонних поставщиков AD](sql-server-linux-active-directory-third-party-providers.md), вы можете добавить строки ниже, чтобы `/var/opt/mssql/mssql.conf` пропустить вызовы SSSD и непосредственно использовать вызовы LDAP.

```/var/opt/mssql/mssql.conf
[network]
disablesssd = true
```

## <a name="next-steps"></a>Следующие шаги

В этом учебнике мы рассмотрели способы настройки проверки подлинности Active Directory с SQL Server в Linux. Вы узнали, как для:
> [!div class="checklist"]
> * Присоединяйтесь к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену AD
> * Создание пользователя AD для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задать имя участника-службы
> * Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab службы
> * Создание имен входа на основе AD в Transact-SQL
> * Подключение к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с использованием проверки подлинности AD

Затем изучите другие сценарии безопасности для SQL Server в Linux.

> [!div class="nextstepaction"]
>[Шифрование подключений к SQL Server в Linux](sql-server-linux-encrypted-connections.md)
