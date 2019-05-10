---
title: Учебник. Использовать проверку подлинности AD для SQL Server в Linux
titleSuffix: SQL Server
description: Этот учебник действия по настройке проверки подлинности AD для SQL Server в Linux.
author: Dylan-MSFT
ms.author: Dylan.Gray
ms.reviewer: rothja
ms.date: 04/01/2019
manager: craigg
ms.topic: tutorial
ms.prod: sql
ms.custom: seodec18
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 3ab6fd05b0cf9486ded5b0e550101a374669be11
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65097237"
---
# <a name="tutorial-use-active-directory-authentication-with-sql-server-on-linux"></a>Учебник. Использование проверки подлинности Active Directory с SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Это руководство содержит сведения о настройке [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux для поддержки проверки подлинности Active Directory (AD), также известный как встроенная проверка подлинности. Дополнительные сведения см. в разделе [проверки подлинности Active Directory для SQL Server в Linux](sql-server-linux-active-directory-auth-overview.md).

Этот учебник состоит из следующих задач:

> [!div class="checklist"]
> * Присоединяйтесь к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену AD
> * Создание пользователя AD для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задать имя участника-службы
> * Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab службы
> * Защита файла keytab
> * Настройка SQL Server для использования файла keytab для проверки подлинности Kerberos
> * Создание имен входа на основе AD в Transact-SQL
> * Подключение к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] с использованием проверки подлинности AD

## <a name="prerequisites"></a>предварительные требования

Перед настройкой проверки подлинности AD, вам потребуется:

* Настройка контроллера домена AD (Windows) в сети  
* Установка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]
  * [Red Hat Enterprise Linux (RHEL)](quickstart-install-connect-red-hat.md)
  * [SUSE Linux Enterprise Server (SLES)](quickstart-install-connect-suse.md)
  * [Ubuntu](quickstart-install-connect-ubuntu.md)

## <a id="join"></a> Присоединяйтесь к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену AD

Необходимо присоединить узла SQL Server Linux с контроллером домена Active Directory. Сведения о том, как присоединиться к домену active directory, см. в разделе [соединения SQL Server на узле Linux к домену Active Directory](sql-server-linux-active-directory-join-domain.md).

## <a id="createuser"></a> Создает для пользователя AD (или MSA) [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и задать имя участника-службы

> [!NOTE]
> В следующих действиях используется вашей [полное доменное имя](https://en.wikipedia.org/wiki/Fully_qualified_domain_name). Если вы используете **Azure**, вы должны **[создать](https://docs.microsoft.com/azure/virtual-machines/linux/portal-create-fqdn)** перед началом работы.

1. На контроллере домена запустите [New-ADUser](https://technet.microsoft.com/library/ee617253.aspx) команду PowerShell, чтобы создать нового пользователя AD с помощью пароля, срок действия не ограничен. Следующий пример имена учетной записи `mssql`, но имя учетной записи может быть любой вам нравится. Вам будет предложено ввести новый пароль для учетной записи.

   ```PowerShell
   Import-Module ActiveDirectory

   New-ADUser mssql -AccountPassword (Read-Host -AsSecureString "Enter Password") -PasswordNeverExpires $true -Enabled $true
   ```

   > [!NOTE]
   > Это соображениям безопасности рекомендуется использовать выделенную учетную запись AD для SQL Server так, чтобы учетные данные SQL Server не совместно с другими службами, с помощью той же учетной записи. Тем не менее можно при необходимости повторно использовать существующую учетную запись AD, если вы знаете пароль учетной записи (необходимый для создания файла keytab на следующем шаге).

2. Задайте ServicePrincipalName (SPN) для этой учетной записи с помощью **setspn.exe** средство. Имя участника-службы должен быть отформатирован в точности так, как указано в следующем примере. Полное доменное имя можно найти [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] хост-компьютере, выполнив `hostname --all-fqdns` на [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла. TCP-порт должен быть 1433, если вы не настроили [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] использовать другой номер порта.

   ```PowerShell
   setspn -A MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>** mssql
   setspn -A MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>** mssql
   ```

   > [!NOTE]
   > Если появится сообщение об ошибке, `Insufficient access rights`, обратитесь к администратору домена, что имеется достаточно разрешений на установку SPN для этой учетной записи.
   >
   > Если вы измените порт TCP в будущем, необходимо запустить **setspn** команду еще раз с новым номером порта. Необходимо также добавить нового имени участника-службы keytab службы SQL Server, выполнив действия, описанные в следующем разделе.

Дополнительные сведения см. в разделе [Регистрация имени участника-службы для соединений Kerberos](../database-engine/configure-windows/register-a-service-principal-name-for-kerberos-connections.md).

## <a id="configurekeytab"></a> Настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] keytab службы

Существует два различных способа настройки файлов keytab для службы SQL Server. Первый вариант — использовать учетную запись компьютера (UPN), в то время как второй параметр использует учетную запись управляемые службы (MSA) в конфигурации keytab. Оба механизма одинаково работают, и можно выбрать метод, который лучше всего подходит для вашей среды.

В обоих случаях требуется имя участника-службы, созданные на предыдущем шаге, и оно должно быть зарегистрировано в keytab.

Настройка файла keytab службы SQL Server:

1. Настройка [записи keytab](#spn) в следующем разделе.

1. Затем либо [добавить имя участника-пользователя](#upn) (вариант 1) или [MSA](#msa) (вариант 2) записи в файле keytab, выполнив действия, описанные в соответствующих подразделах.

> [!IMPORTANT]
> Если изменяется пароль для имени участника-пользователя или учетная запись MSA или изменении пароля для учетной записи, которые назначаются имена SPN, необходимо обновить keytab, указав новый пароль и номер версии ключа (KVNO). Некоторые службы также может автоматически изменить пароли. Просмотрите все политики смены пароля для учетных записей в вопросе и выровняйте их действия запланированного обслуживания, уберечься от незапланированных простоев.

### <a id="spn"></a> Имя участника-службы keytab записей

1. Проверьте номер версии ключа (KVNO) для учетной записи AD, созданной на предыдущем шаге. Обычно это 2, но это может быть другое целое число, если вы изменили пароль для учетной записи несколько раз. На хост-компьютере SQL Server выполните следующие команды:

   ```bash
   kinit user@CONTOSO.COM
   kvno MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**
   ```

   > [!NOTE]
   > Имена участников-служб может занять несколько минут для распространения через домен, особенно в том случае, если домен велико. Если сообщение об ошибке, `kvno: Server not found in Kerberos database while getting credentials for MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM`, подождите несколько минут и повторите попытку.  

1. Запуск **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Добавьте записи keytab для каждого имени участника-службы, используя следующие команды:

   ```bash
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<fully qualified domain name of host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e aes256-cts-hmac-sha1-96
   addent -password -p MSSQLSvc/**<netbios name of the host machine>**:**<tcp port>**@CONTOSO.COM -k **<kvno from above>** -e rc4-hmac
   ```

1. Запись в файл keytab и закройте ktutil:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

   > [!NOTE]
   > **Ktutil** инструмент не проверяет пароль, поэтому убедитесь, что он правильно при появлении запроса.

### <a id="upn"></a> Вариант 1. С помощью имени участника-пользователя для настройки keytab

Добавьте учетную запись компьютера для вашего keytab с **ktutil**. (Также называемый UPN) учетной записи компьютера присутствует в **/etc/krb5.keytab** в форме `<hostname>$@<realm.com>` (например, `sqlhost$@CONTOSO.COM`). Скопируйте эти записи из **/etc/krb5.keytab** для **mssql.keytab**.

1. Запуск **ktuil** , выполнив следующую команду:

   ```bash
   sudo ktutil
   ```

1. Используйте **rkt** команду, чтобы прочитать все записи из **/etc/krb5.keytab**.

   ```bash
   rkt /etc/krb5.keytab
   ```

1. Затем получите список записей.

   ```bash
   list
   ```

1. Удалите все записи путем их номер ячейки, которые не являются имя участника-пользователя. Сделайте этот один за другим, повторив следующую команду:

   ```bash
   delent <slot num>
   ```

   > [!IMPORTANT]
   > Когда запись удаляется, например области 1, все значения слайд вверх на единицу, чтобы занять его место. Это означает, что перемещает элемент в слоте 2 слота 1, при удалении записи в слот 1.

1. Записи еще раз список пока остаются только записи, имя участника-пользователя.

   ```bash
   list
   ```

1. Когда остаются только записи, имя участника-пользователя, добавить эти значения **mssql.keytab**:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   ```

1. Выйти из программы **ktutil**.

   ```bash
   quit
   ```

### <a id="msa"></a> Вариант 2.  С помощью MSA для настройки keytab

Для параметра MSA необходимо создать keytab Kerberos в SQL Server. Он должен содержать все [имен SPN, зарегистрированных на первом шаге](#spn) и учетные данные для MSA, к которому имена SPN регистрируются. 

1. После keytab имени участника-службы создаются записи, выполните следующие команды с компьютера Linux, который присоединен к домену:

   ```bash
   kinit <AD user>
   kvno <any SPN registered in step 1>
      <spn>@CONTOSO.COM: kvno = <KVNO>
   ```

   Этот шаг выводит KVNO учетной записи пользователя, можно назначить владельцем имени участника-службы. Для этого шага для работы имя участника-службы должны были назначены учетная запись MSA во время его создания. Если имя участника-службы не был назначен MSA, KVNO отображается будет текущей учетной записи владельца имени участника-службы и быть неправильным, используемый для конфигурации.  

1. Запуск **ktutil**:

   ```bash
   sudo ktutil
   ```

1. Добавьте учетная запись MSA с помощью следующих двух команд:

   ```bash
   addent -password -p <MSA> -k <kvno from command above> -e aes256-cts-hmac-sha1-96
   addent -password -p <MSA> -k <kvno from command above> -e rc4-hmac
   ```

1. Запись в файл keytab и закройте ktutil:

   ```bash
   wkt /var/opt/mssql/secrets/mssql.keytab
   quit
   ```

1. При использовании подхода MSA, необходимо задать с помощью параметра конфигурации **mssql-conf** средства, чтобы задать управляемую учетную запись службы, которая будет использоваться при доступе к файлу keytab. Убедитесь, приведенные ниже значения **/var/opt/mssql/mssql.conf**.

   ```bash
   sudo mssql-conf set network.privilegedadaccount <MSA_Name>
   ```

   > [!NOTE]
   > Включать только имя MSA, а не имя домен\u1091? четная запись.

## <a id="securekeytab"></a> Защита файла keytab

Все, кто имеет доступ к этому файлу keytab может олицетворять SQL Server в домене, поэтому убедитесь, что ограничение доступа к файлу, таким образом, чтобы только mssql учетная запись имеет доступ на чтение:

```bash
sudo chown mssql:mssql /var/opt/mssql/secrets/mssql.keytab
sudo chmod 400 /var/opt/mssql/secrets/mssql.keytab
```

## <a id="keytabkerberos"></a> Настройка SQL Server для использования файла keytab для проверки подлинности Kerberos

Используйте следующие действия для настройки SQL Server, чтобы приступить к использованию файла keytab для проверки подлинности Kerberos.

```bash
sudo mssql-conf set network.kerberoskeytabfile /var/opt/mssql/secrets/mssql.keytab
sudo systemctl restart mssql-server
```

При необходимости отключите UDP-подключений к контроллеру домена для повышения производительности. Во многих случаях подключения по протоколу UDP согласованно сбой при подключении к контроллеру домена, можно задать параметры конфигурации **/etc/krb5.conf** пропустить вызовы UDP. Изменить **/etc/krb5.conf** и задать следующие параметры:

```/etc/krb5.conf
[libdefaults]
udp_preference_limit=0
```

На этом этапе все готово для использования имен входа на основе AD в SQL Server следующим образом.

## <a id="createsqllogins"></a> Создание имен входа на основе AD в Transact-SQL

1. Подключитесь к SQL Server и создать новый, основанный на AD входа:

   ```sql
   CREATE LOGIN [CONTOSO\user] FROM WINDOWS;
   ```

1. Убедитесь, что имя входа является теперь [sys.server_principals](../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) представления системного каталога:

   ```sql
   SELECT name FROM sys.server_principals;
   ```

## <a id="connect"></a> Подключение к SQL Server с использованием проверки подлинности AD

Войдите на клиентский компьютер, используя свои учетные данные домена. Теперь можно подключиться к SQL Server без повторного ввода пароля с использованием проверки подлинности AD. При создании имени входа группы AD, таким же образом можно подключиться любой пользователь AD, являющийся членом этой группы.

Параметр строки подключения для клиентов на использование проверки подлинности AD зависит от того, какой драйвер используется. Обратите внимание на примеры в следующих разделах.

### <a name="sqlcmd-on-a-domain-joined-linux-client"></a>sqlcmd на присоединенных к домену клиента Linux

Войдите на присоединенных к домену клиента Linux с помощью **ssh** и учетные данные домена:

```bash
ssh -l user@contoso.com client.contoso.com
```

Убедитесь, что вы установили [mssql-tools](sql-server-linux-setup-tools.md) пакета, затем через **sqlcmd** без указания учетных данных:

```bash
sqlcmd -S mssql-host.contoso.com
```

### <a name="ssms-on-a-domain-joined-windows-client"></a>SSMS на клиенте Windows, присоединенных к домену

Войдите на присоединенных к домену клиента Windows, используя свои учетные данные домена. Убедитесь, что установлен SQL Server Management Studio, а затем подключитесь к экземпляру SQL Server (например, `mssql-host.contoso.com`), указав **проверки подлинности Windows** в **соединение с сервером** диалоговое окно.

### <a name="ad-authentication-using-other-client-drivers"></a>С помощью других драйверов клиента проверки подлинности AD

В следующей таблице описаны рекомендации для других драйверов клиента:

| Драйвер клиента | Рекомендация |
|---|---|
| **JDBC** | Используйте встроенную проверку подлинности Kerberos для подключения к серверу SQL. |
| **интерфейс ODBC** | Используйте встроенную проверку подлинности. |
| **ADO.NET** | Синтаксис строки соединения. |

## <a id="additionalconfig"></a> Дополнительные параметры конфигурации

При использовании служебных программ независимых производителей, таких как [элементы PBI](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), или [Centrify](https://www.centrify.com/) для присоединения узла Linux в AD домены и вы бы хотели вынудить SQL server с помощью openldap Библиотека напрямую, можно настроить **disablesssd** с параметром **mssql-conf** следующим образом:

```bash
sudo mssql-conf set network.disablesssd true
systemctl restart mssql-server
```

> [!NOTE]
> Существуют служебные программы, такие как **realmd** которой Настройка SSSD, при других средств, например PBI, виртуального адресного ПРОСТРАНСТВА и Centrify не настроили SSSD. Если используется для присоединения к домену AD не установки SSSD, рекомендуется настроить **disablesssd** равным `true`. Это не обязательно, так как SQL Server попытается использовать SSSD для AD до возврата к openldap механизм, было бы более высокую производительность, чтобы настроить его, чтобы SQL Server вызывает openldap непосредственно обход механизма SSSD.

Если контроллер домена поддерживает LDAPS, можно заставить все подключения из SQL Server на контроллерах домена, чтобы быть через LDAPS. Чтобы проверить, клиент может связаться с контроллером домена через ldaps, выполните следующую команду bash, `ldapsearch -H ldaps://contoso.com:3269`. Чтобы установить SQL Server на использование только LDAPS, используйте следующую команду:

```bash
sudo mssql-conf set network.forcesecureldap true
systemctl restart mssql-server
```

Это будут использовать LDAPS по SSSD, если присоединение к домену AD, на узел выполнено также с помощью пакета SSSD и **disablesssd** не задано значение true. Если **disablesssd** имеет значение true вместе с **forcesecureldap** , равным true, то он будет использовать протокол LDAPS через вызовы библиотеки openldap, выполняемые SQL Server.

### <a name="post-sql-server-2017-cu14"></a>Учет CU14 SQL Server 2017

Начиная с SQL Server 2017 CU14, если SQL Server был присоединен к контроллеру домена AD, с помощью сторонних поставщиков и настроен с помощью параметра openldap вызовов для поиска в общие AD **disablesssd** в значение true, можно также использовать **enablekdcfromkrb5** параметр, чтобы принудительно SQL Server для использования библиотеки krb5 при поиске контроллера Kerberos-домена вместо обратного просмотра DNS для сервера центра распространения КЛЮЧЕЙ.

Это может быть полезно для сценария, где вы хотите вручную настроить SQL Server пытается связаться с контроллеров домена. И использовать механизм библиотеки openldap с помощью списка KDC в **krb5.conf**.

Сначала задайте **disablessd** и **enablekdcfromkrb5conf** равным true и перезапустите SQL Server:

```bash
sudo mssql-conf set network.disablesssd true
sudo mssql-conf set network.enablekdcfromkrb5conf true
systemctl restart mssql-server
```

Затем настройте список KDC в **/etc/krb5.conf** следующим образом:

```/etc/krb5.conf
[realms]
CONTOSO.COM = {
  kdc = dcWithGC1.contoso.com
  kdc = dcWithGC2.contoso.com
}
```

> [!NOTE]
> Хотя не рекомендуется, можно использовать служебные программы, такие как **realmd**, который настроен SSSD присоединение узла Linux к домену, при настройке **disablesssd** значение true, чтобы SQL Server использует вызовы openldap вместо из SSSD для Active Directory, связанные с вызовы.

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
