---
title: "Проверка подлинности Active Directory с SQL Server для Linux | Документы Microsoft"
description: "Действия по настройке для проверки подлинности AAD для SQL Server в Linux"
author: tmullaney
ms.date: 07/17/2017
ms.author: thmullan;rickbyh
manager: jhubbard
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
helpviewer_keywords:
- Linux, AAD authentication
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9e6d1afdfa7b7d4ef1bfec4461badca746651c44
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="active-directory-authentication-with-sql-server-on-linux"></a>Проверка подлинности Active Directory с SQL Server в Linux  
[!INCLUDE[tsql-appliesto-sslinx-only_md](../../docs/includes/tsql-appliesto-sslinx-only_md.md)]


В этом документе описывается настройка [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] в Linux для поддержки проверки подлинности Active Directory (AD), также известный как встроенную проверку подлинности. Проверка подлинности AD позволяет присоединенных к домену клиенты под управлением Windows или Linux, для проверки подлинности [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] с помощью учетных данных домена, а протокол Kerberos. Проверки подлинности AD имеет следующие преимущества по [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] проверки подлинности:  
• Пользователи проходят проверку подлинности через единый вход, не вводя пароль.   
• Путем создания имен входа для групп AD, можно управлять доступа и разрешений в [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] с помощью членства в группах AD.  
• Каждый пользователь получает одно удостоверение во всей организации, поэтому не нужно для отслеживания которой [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] круг пользователей, которым соответствуют имена входа.   
• AD позволяет принудительно применять политику централизованного пароль во всей организации.   

## <a name="prerequisites"></a>Предварительные требования
Перед настройкой проверки подлинности AD, необходимо:
- Настроить контроллер домена AD (Windows), в сети  
- Установка[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]
  - [Red Hat Enterprise Linux](quickstart-install-connect-red-hat.md)
  - [SUSE Linux Enterprise Server](quickstart-install-connect-suse.md)
  - [Ubuntu](quickstart-install-connect-ubuntu.md)

>  [!IMPORTANT]  
>   В настоящее время единственного способа проверки подлинности поддерживается для конечной точки зеркального отображения базы данных является СЕРТИФИКАТ. Метод проверки подлинности WINDOWS, которые будут включены в будущих версиях

## <a name="step-1-join-includessnoversiondocsincludesssnoversion-mdmd-host-to-ad-domain"></a>Шаг 1: Присоединить [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] узла к домену AD
Существует множество средств для присоединения [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] хост-компьютера к домену AD. В этом пошаговом руководстве используется  **[realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join.html)**, пакет с открытым исходным кодом. Если это еще не сделано, установите на клиентские пакеты Kerberos и realmd [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] хост-компьютера с помощью диспетчера пакетов дистрибутив Linux:  
```bash  
# RHEL
sudo yum install realmd krb5-workstation

# SUSE
sudo zypper install realmd krb5-client

# Ubuntu
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```  

Если пакет установки клиента Kerberos запросит имя области, введите имя домена прописными буквами.  

>  [!NOTE]  
>  В этом пошаговом руководстве используется «contoso.com» и «CONTOSO.COM» как примеры домен и область имен, соответственно. Следует заменить их собственными значениями. Эти команды чувствительны к регистру, поэтому убедитесь, что вы используете прописные везде, где он используется в этом пошаговом руководстве.  

Выполните следующую команду, чтобы убедиться, что [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] хост-компьютере настроен для использования в качестве имен DNS контроллера домена AD для:
```bash  
sudo realm discover contoso.com -v
```  
Если домен не найден, необходимо настроить на [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] хост-компьютера для использования IP-адрес контроллера домена AD в качестве имен DNS. Конкретная последовательность действий для этого зависят от вашей конфигурации устройства в сети, конфигурации домена и дистрибутив Linux. Ниже приведены некоторые подходы пример.

### <a name="example-dns-configuration-ubuntu"></a>Пример конфигурации DNS: Ubuntu
Изменить `/etc/network/interfaces` так, чтобы контроллер домена AD IP-адрес указан в качестве dns имен. Например: 
 
```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
iface eth0 inet dhcp
dns-nameservers **<AD domain controller IP address>**
dns-search **<AD domain name>**
```  
>  [!NOTE]  
>  Сетевой интерфейс (eth0) могут отличаться для differnet машин. Чтобы узнать, какой из них используется, запустите ifconfig и скопируйте интерфейс, который имеет IP-адрес и отправленных и полученных байт.

После изменения этого файла, перезапустите сетевую службу:
```bash
sudo ifdown eth0 && sudo ifup eth0
```
Убедитесь, что теперь ваш `/etc/resolv.conf` файл содержит строку следующего вида:  
```Code  
nameserver **<AD domain controller IP address>**
```  

### <a name="example-dns-configuration-rhel"></a>Пример конфигурации DNS: RHEL
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
Убедитесь, что теперь ваш `/etc/resolv.conf` файл содержит строку следующего вида:  
```Code  
nameserver **<AD domain controller IP address>**
```  

### <a name="join-the-domain"></a>Присоединение к домену.
После подтверждения что ваша служба DNS настроена правильно, присоединиться к домену, выполнив следующую команду. Необходимо выполнить проверку подлинности с помощью учетной записи AD, которая имеет достаточные права в AD, чтобы присоединить новую машину к домену. В частности, эта команда будет создавать новую учетную запись компьютера в AD, `/etc/krb5.keytab` размещения файла keytab и Настройка домена в `/etc/sssd/sssd.conf`:
```bash                                     
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
 * Successfully enrolled machine in realm
```    

>  [!NOTE]  
>   Если появится сообщение об ошибке, «не установлены необходимые пакеты», то следует установить эти пакеты с помощью диспетчера пакетов дистрибутив Linux, перед запуском `realm join` еще раз. 
>  
>  Если появляется сообщение об ошибке «Недостаточно разрешений на присоединение к домену» будет необходимо проконсультироваться с администратором домена, что разрешения достаточны для присоединения к домену компьютеры Linux.

 
Убедитесь, что теперь можно собрать сведения о пользователе из домена и что можно получить билет Kerberos, что и пользователь. 

We will use **id**, **[kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html)** and **[klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html)** commands for this.

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

>  [!NOTE]  
>   Если `id user@contoso.com` возвращает «Нет такой пользователь,» убедитесь в том, успешно запущена служба SSSD, выполнив команду `sudo systemctl status sssd`. Если служба запущена, и по-прежнему отображается сообщение «Пользователь», попробуйте включить подробное ведение журнала для SSSD. Дополнительные сведения см. в документации Red Hat для [Устранение неполадок SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).  
>  
>  Если `kinit user@CONTOSO.COM` возвращает, «ответ контроллера Kerberos-домена не соответствует ожиданиям при получении начального учетных данных,» убедитесь в том, указанный область в верхнем регистре.

Дополнительные сведения см. в документации Red Hat для [Discovering и присоединение домены удостоверений](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html). 

## <a name="step-2-create-ad-user-for-includessnoversiondocsincludesssnoversion-mdmd-and-set-spn"></a>Шаг 2: Создание пользователя AD для [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] и задать имя участника-службы  

>  [!NOTE]  
>  В следующих шагах мы будем использовать ваш [полного доменного имени](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Если вы работаете с **Azure**, необходимо будет  **[создать](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/portal-create-fqdn)**  перед продолжением. 

На контроллере домена запустите [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) команду PowerShell, чтобы создать нового пользователя AD с помощью пароля, срок действия не ограничен. В этом примере имена учетной записи «mssql», но имя учетной записи может быть любое. Вам будет предложено ввести новый пароль для учетной записи:  
```PowerShell   
Import-Module ActiveDirectory

New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
```   

>  [!NOTE]  
>  Это соображениям безопасности рекомендуется иметь выделенной учетной записи AD для SQL Server, чтобы учетные данные SQL Server не совместно с другими службами, используя ту же учетную запись. Тем не менее можно повторно использовать существующую учетную запись AD при желании, если вы знаете пароль (требуется для создания файла keytab на следующем шаге).

Теперь значение ServicePrincipalName (SPN) для этой учетной записи с помощью `setspn.exe` средства. Имя участника-службы должен быть отформатирован только как указано в следующем примере: полное доменное имя можно найти [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] хост-компьютера, запустив `hostname --all-fqdns` на [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] узла и TCP-порт должен быть 1433, если не настроены [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] использовать другой номер порта.  
```PowerShell   
setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
```   

>  [!NOTE]  
>  Если появляется сообщение об ошибке «Недостаточно прав,» затем необходимо проконсультироваться с администратором домена, что разрешения достаточны для задания имени участника-службы для этой учетной записи.
>  
>  Если в дальнейшем изменить TCP-порт, будет необходимо снова запустить команду setspn с новым номером порта. Также необходимо будет добавить новое имя участника-службы keytab службы SQL Server, приведенные в следующем разделе.

Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](/sql/database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).  

## <a name="step-3-configure-includessnoversiondocsincludesssnoversion-mdmd-service-keytab"></a>Шаг 3: Настройка [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] keytab службы  
Во-первых Проверьте номер версии ключа (kvno) для учетной записи AD, созданной на предыдущем шаге. Обычно будет равен 2, но это может быть другое целое число, при изменении пароля для учетной записи несколько раз. На [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] хост-компьютера, выполните следующую команду:

```bash
kinit user@CONTOSO.COM

kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
```

Теперь создайте файл keytab для пользователя AD, созданный на предыдущем шаге. В этом случае мы будем использовать  **[ktutil](https://web.mit.edu/kerberos/krb5-1.12/doc/admin/admin_commands/ktutil.html)**. При появлении запроса введите пароль для этой учетной записи AD. 
```bash  
sudo ktutil

ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96

ktutil: addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac

ktutil: wkt /var/opt/mssql/secrets/mssql.keytab

quit
```  

>  [!NOTE]  
>  Средство ktutil не проверки пароля, поэтому убедитесь, что введен правильно.

Все, кто имеет доступ к этой `keytab` файл может олицетворять [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] в домене, поэтому убедитесь, что ограничить доступ к файлу такие только `mssql` учетная запись имеет доступ для чтения:  
```bash  
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```  
Настройте [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] для использования этой `keytab` файла для проверки подлинности Kerberos:  
```bash  
sudo /opt/mssql/bin/mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```  

## <a name="step-4-create-ad-based-logins-in-transact-sql"></a>Шаг 4: Создание имен входа на основе AD в Transact-SQL  
Подключиться к [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] и создать новое, основанное на AD входа:  
```Transact-SQL  
CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
```   

Убедитесь, что имя входа теперь содержатся в [sys.server_principals](/sql/relational-databases/system-catalog-views/sys-server-principals-transact-sql.mc) представления системного каталога:  
```Transact-SQL  
SELECT name FROM sys.server_principals;
```  

## <a name="step-5-connect-to-includessnoversiondocsincludesssnoversion-mdmd-using-ad-authentication"></a>Шаг 5: Подключение к [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] с использованием проверки подлинности AD  
Войдите на клиентский компьютер, используя свои учетные данные домена. Теперь вы можете подключиться к [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] избежать повторного ввода пароля, с помощью проверки подлинности AD. При создании имени входа для присоединения к группе AD, таким же образом можно подключиться любой пользователь AD, являющийся членом этой группы.  
Параметр строки подключения для клиентов на использование проверки подлинности AD, зависит от того, на драйвер, который вы используете. Ниже приведено несколько примеров.  

## <a name="examples"></a>Примеры  
### <a name="example-1-sqlcmd-on-a-domain-joined-linux-client"></a>Пример 1: `sqlcmd` на присоединенных к домену клиента Linux  
Войдите на присоединенных к домену клиента Linux с помощью `ssh` и учетные данные домена:  
```bash  
ssh -l user@contoso.com client.contoso.com
```  

Убедитесь, что вы установили [mssql средства](sql-server-linux-setup-tools.md) пакета, а затем подключиться с помощью `sqlcmd` без указания любые учетные данные:  
```bash  
sqlcmd -S mssql.contoso.com
```  

### <a name="example-2-ssms-on-a-domain-joined-windows-client"></a>Пример 2: SSMS на присоединенных к домену клиента Windows  
Войдите на присоединенных к домену клиента Windows, используя свои учетные данные домена. Убедитесь, что [!INCLUDE[ssmanstudiofull-md](../../docs/includes/ssmanstudiofull-md.md)] установлен, а затем подключиться к вашей [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] экземпляром, с указанием **проверки подлинности Windows** в **соединение с сервером** диалогового окна.  

### <a name="ad-authentication-using-other-client-drivers"></a>Другие клиентские драйверы с помощью проверки подлинности AD  
• JDBC: [Kerberos с использованием встроенной проверки подлинности для подключения SQL Server](https://docs.microsoft.com/sql/connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server])  
• ODBC: [встроенную проверку подлинности](https://docs.microsoft.com/sql/connect/odbc/linux/using-integrated-authentication)  
• ADO.NET: [синтаксис строки соединения](https://msdn.microsoft.com/library/ms254500.aspx)   


