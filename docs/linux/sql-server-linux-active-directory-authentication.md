---
title: Active учебника каталога проверки подлинности для SQL Server для Linux | Документы Microsoft
description: Этот учебник шаги конфигурации используется для проверки подлинности AAD для SQL Server в Linux.
author: meet-bhagdev
ms.date: 02/23/2018
ms.author: meetb
manager: craigg
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: df3cea6d47d50464fe0b8a7f2573c230585b9cb1
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>Учебник: Проверка подлинности Active Directory используйте с помощью SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Этот учебник описывается настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux для поддержки проверки подлинности Active Directory (AD), также известный как встроенную проверку подлинности. Общие сведения см. в разделе [проверки подлинности Active Directory для SQL Server в Linux](sql-server-linux-active-directory-auth-overview.md).

Этот учебник состоит из следующих задач:

> [!div class="checklist"]
> * Присоединение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену AD
> * Создайте пользователя AD для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задать имя участника-службы
> * Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab службы
> * Создать имена входа на основе AD в Transact-SQL
> * Подключиться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с использованием проверки подлинности AD

## <a name="prerequisites"></a>предварительные требования

Перед настройкой проверки подлинности AD, необходимо:

* Настроить контроллер домена AD (Windows), в сети  
* Установка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
  * [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Присоединение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену AD

Выполните следующие действия, чтобы присоединить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену Active Directory:

1. Используйте **[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)** для присоединения к домену AD хост-компьютере. Если это еще не сделано, установите на клиентские пакеты Kerberos и realmd [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютера с помощью диспетчера пакетов дистрибутив Linux:

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
   > В этом пошаговом руководстве используется «contoso.com» и «CONTOSO.COM» как примеры домен и область имен, соответственно. Следует заменить их собственными значениями. Эти команды чувствительны к регистру, поэтому убедитесь, что вы используете прописные везде, где он используется в этом пошаговом руководстве.

1. Настройка вашего [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютера для использования IP-адрес контроллера домена AD в качестве имен DNS. 

   - **Ubuntu**:

      Изменить `/etc/network/interfaces` так, чтобы контроллер домена AD IP-адрес указан в качестве dns имен. Например: 

      ```/etc/network/interfaces
      <...>
      # The primary network interface
      auth eth0
      iface eth0 inet dhcp
      dns-nameservers **<AD domain controller IP address>**
      dns-search **<AD domain name>**
      ```

      > [!NOTE]
      > Сетевой интерфейс (eth0) может отличаться для разных компьютерах. Чтобы узнать, какой из них используется, запустите ifconfig и скопируйте интерфейс, который имеет IP-адрес и отправленных и полученных байт.

      После изменения этого файла, перезапустите сетевую службу:

      ```bash
      sudo ifdown eth0 && sudo ifup eth0
      ```

      Убедитесь, что теперь ваш `/etc/resolv.conf` файл содержит строку, как в следующем примере:  

      ```Code
      nameserver **<AD domain controller IP address>**
      ```

   - **RHEL**:

     Изменить `/etc/sysconfig/network-scripts/ifcfg-eth0` файла (или другие конфигурации интерфейса соответствующим образом файла), чтобы контроллер домена AD IP-адрес указан в качестве DNS-сервера:

     ```/etc/sysconfig/network-scripts/ifcfg-eth0
     <...>
     PEERDNS=no
     DNS1=**<AD domain controller IP address>**
     ```

     После изменения этого файла, перезапустите сетевую службу:

     ```bash
     sudo systemctl restart network
     ```

     Убедитесь, что теперь ваш `/etc/resolv.conf` файл содержит строку, как в следующем примере:  

     ```Code
     nameserver **<AD domain controller IP address>**
     ```

1. Присоединение к домену.

   После подтверждения что ваша служба DNS настроена правильно, присоединиться к домену, выполнив следующую команду. Необходимо проверить подлинность с помощью учетной записи AD, которая имеет достаточные права в AD, чтобы присоединить новую машину к домену.

   В частности, эта команда создает новую учетную запись компьютера в AD, создайте `/etc/krb5.keytab` размещения файла keytab и Настройка домена в `/etc/sssd/sssd.conf`:

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   <...>
   * Successfully enrolled machine in realm
   ```

   > [!NOTE]
   > Если появится сообщение об ошибке, «не установлены необходимые пакеты», то следует установить эти пакеты с помощью диспетчера пакетов дистрибутив Linux, перед запуском `realm join` еще раз.
   >
   > Если появляется сообщение об ошибке «Недостаточно разрешений на присоединение к домену» затем необходимо проконсультироваться с администратором домена, что разрешения достаточны для присоединения к домену компьютеры Linux.
   >
   > Если появляется сообщение об ошибке, «ответ контроллера Kerberos-домена не соответствует ожиданиям,» затем может не были выбраны правильные имя пользователя. Имена областей чувствительны к регистру, обычно прописные буквы и могут идентифицироваться с помощью команды `realm discover contoso.com`.
   
   > SQL Server использует SSSD и NSS для сопоставления идентификаторов безопасности (SID) учетных записей пользователей и групп. SSSD должна быть настроена и запущена в порядке для SQL Server для создания имен входа AD успешно. Realmd обычно выполняется автоматически в процессе присоединения к домену, но в некоторых случаях это необходимо сделать отдельно.
   >
   > См. ниже, чтобы настроить [SSSD вручную](https://access.redhat.com/articles/3023951), и [Настройка NSS для работы с SSSD](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options)

  
5. Убедитесь, что теперь можно собрать сведения о пользователе из домена и что можно получить билет Kerberos, что и пользователь.

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
   > Если `id user@contoso.com` возвращает «Нет такой пользователь,» убедитесь в том, успешно запущена служба SSSD, выполнив команду `sudo systemctl status sssd`. Если служба запущена, и по-прежнему отображается сообщение «Пользователь», попробуйте включить подробное ведение журнала для SSSD. Дополнительные сведения см. в документации Red Hat для [Устранение неполадок SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).
   >
   > Если `kinit user@CONTOSO.COM` возвращает, «ответ контроллера Kerberos-домена не соответствует ожиданиям при получении начального учетных данных,» убедитесь в том, указанный область в верхнем регистре.

Дополнительные сведения см. в документации Red Hat для [Discovering и присоединение домены удостоверений](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html). 

## <a id="createuser"></a> Создайте пользователя AD для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задать имя участника-службы

  > [!NOTE]
  > Далее шаги использования вашей [полного доменного имени](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Если вы работаете с **Azure**, необходимо **[создать](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/portal-create-fqdn)** перед продолжением работы.

1. На контроллере домена запустите [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) команду PowerShell, чтобы создать нового пользователя AD с помощью пароля, срок действия не ограничен. В этом примере имена учетной записи «mssql», но имя учетной записи может быть любое. Вам будет предложено ввести новый пароль для учетной записи:

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > Это соображениям безопасности рекомендуется иметь выделенной учетной записи AD для SQL Server, чтобы учетные данные SQL Server не совместно с другими службами, используя ту же учетную запись. Тем не менее можно повторно использовать существующую учетную запись AD при желании, если вы знаете пароль (требуется для создания файла keytab на следующем шаге).

2. Задать ServicePrincipalName (SPN) для этой учетной записи с помощью `setspn.exe` средства. Имя участника-службы должен быть отформатирован в точности совпадают с указанными в следующем примере. Полное доменное имя можно найти [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютера, запустив `hostname --all-fqdns` на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла и TCP-порт должен быть 1433, если не настроены [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использовать другой номер порта.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Если появляется сообщение об ошибке «Недостаточно прав,» затем необходимо проконсультироваться с администратором домена, что разрешения достаточны для задания имени участника-службы для этой учетной записи.
   >
   > Если в дальнейшем изменить TCP-порт, необходимо снова запустить команду setspn с новым номером порта. Необходимо также добавить новое имя участника-службы keytab службы SQL Server, приведенные в следующем разделе.

3. Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab службы

1. Проверьте номер версии ключа (kvno) для учетной записи AD, созданной на предыдущем шаге. Обычно он равен 2, но это может быть другое целое число, при изменении пароля для учетной записи несколько раз. На [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютера, выполните следующую команду:

   ```bash
   kinit user@CONTOSO.COM

   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

2. Создание файла keytab с **[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)** для пользователя AD, созданный на предыдущем шаге. При появлении запроса введите пароль для этой учетной записи AD.

   ```bash
   sudo ktutil

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

   ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

   ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

   quit
   ```

   > [!NOTE]
   > Средство ktutil не проверки пароля, поэтому убедитесь, что введен правильно.

3. Все, кто имеет доступ к этой `keytab` файл может олицетворять [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в домене, поэтому убедитесь, что ограничить доступ к файлу такие только `mssql` учетная запись имеет доступ для чтения:

   ```bash
   sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
   sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
   ```

4. Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для использования этой `keytab` файла для проверки подлинности Kerberos:

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
   sudo systemctl restart mssql-server
   ```

## <a id="createsqllogins"></a> Создать имена входа на основе AD в Transact-SQL

1. Подключиться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и создать новое, основанное на AD входа:

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

2. Убедитесь, что имя входа теперь содержатся в [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления системного каталога:

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> Подключиться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с использованием проверки подлинности AD

Войдите на клиентский компьютер, используя свои учетные данные домена. Теперь вы можете подключиться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] избежать повторного ввода пароля, с помощью проверки подлинности AD. При создании имени входа для присоединения к группе AD, таким же образом можно подключиться любой пользователь AD, являющийся членом этой группы.

Параметр строки подключения для клиентов на использование проверки подлинности AD, зависит от того, на драйвер, который вы используете. Рассмотрим следующие примеры:

* `sqlcmd` на клиентском компьютере Linux присоединенных к домену

   Войдите на присоединенных к домену клиента Linux с помощью `ssh` и учетные данные домена:

   ```bash
   ssh -l user@contoso.com client.contoso.com
   ```

   Убедитесь, что вы установили [mssql средства](sql-server-linux-setup-tools.md) пакета, а затем подключиться с помощью `sqlcmd` без указания любые учетные данные:

   ```bash
   sqlcmd -S mssql.contoso.com
   ```

* Среда SSMS на присоединенных к домену клиента Windows

   Войдите на присоединенных к домену клиента Windows, используя свои учетные данные домена. Убедитесь, что [!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] установлен, а затем подключиться к вашей [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] экземпляром, с указанием **проверки подлинности Windows** в **соединение с сервером** диалогового окна.

* Другие клиентские драйверы с помощью проверки подлинности AD

  * JDBC: [Kerberos с использованием встроенной проверки подлинности для подключения SQL Server](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server)
  * ODBC: [встроенную проверку подлинности](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)
  * ADO.NET: [синтаксис строки соединения](https://msdn.microsoft.com/library/system.data.sqlclient.sqlauthenticationmethod(v=vs.110).aspx)
  
## <a name="next-steps"></a>Следующие шаги

В этом учебнике мы прошли по настройке проверки подлинности Active Directory с SQL Server в Linux. Узнать, как для:
> [!div class="checklist"]
> * Присоединение [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену AD
> * Создайте пользователя AD для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задать имя участника-службы
> * Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab службы
> * Создать имена входа на основе AD в Transact-SQL
> * Подключиться к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с использованием проверки подлинности AD

Затем изучите другие сценарии безопасности для SQL Server в Linux.

> [!div class="nextstepaction"]
>[Шифрование соединений с SQL Server в Linux](sql-server-linux-encrypted-connections.md)
