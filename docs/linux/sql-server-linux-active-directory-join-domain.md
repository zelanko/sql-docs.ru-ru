---
title: Присоединение SQL Server на базе Linux к Active Directory
titleSuffix: SQL Server
description: ''
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.date: 04/01/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 90a2bcdac4fd1870adc4eeaa888b906857ef9854
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305277"
---
# <a name="join-sql-server-on-a-linux-host-to-an-active-directory-domain"></a>Присоединение SQL Server на узле Linux к домену Active Directory

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье приводятся общие рекомендации по присоединению хост-компьютера SQL Server на базе Linux к домену Active Directory (AD). Доступно два метода: использование встроенного пакета SSSD или сторонних поставщиков Active Directory. Примерами сторонних продуктов для присоединения к домену являются [PowerBroker Identity Services (PBIS)](https://www.beyondtrust.com/), [One Identity](https://www.oneidentity.com/products/authentication-services/) и [Centrify](https://www.centrify.com/). Это руководство содержит инструкции по проверке конфигурации Active Directory. Однако оно не описывает, как присоединить компьютер к домену при использовании сторонних служебных программ.

## <a name="prerequisites"></a>предварительные требования

Перед настройкой проверки подлинности Active Directory необходимо настроить контроллер домена Active Directory в сети Windows. Затем присоедините SQL Server на узле Linux к домену Active Directory.

> [!IMPORTANT]
> Примеры шагов, приведенные в этой статье, предназначены только для справки. Фактические шаги могут немного отличаться в вашей среде в зависимости от ее общей настройки. Привлекайте своего системного администратора и администратора домена в своей среде к настройке и устранению неполадок.

## <a name="check-the-connection-to-a-domain-controller"></a>Проверка подключения к контроллеру домена

Убедитесь, что вы можете связаться с контроллером домена как по короткому, так и по полному имени домена.

```bash
ping contoso
ping contoso.com
```

> [!TIP]
> В этом руководстве в качестве примеров имен домена и области используются **contoso.com** и **CONTOSO.COM** соответственно. Также используется **DC1.CONTOSO.COM** в качестве примера полного доменного имени для контроллера домена. Эти имена нужно заменить собственными значениями.

Если любая из этих проверок имен завершается ошибкой, обновите список поиска доменов. В следующих разделах приведены инструкции для Ubuntu, Red Hat Enterprise Linux (RHEL) и SUSE Linux Enterprise Server (SLES) соответственно.

### <a name="ubuntu"></a>Ubuntu

1. Измените файл **/etc/network/interfaces**, чтобы ваш домен Active Directory находился в списке поиска доменов.

   ```/etc/network/interfaces
   # The primary network interface
   auto eth0
   iface eth0 inet dhcp
   dns-nameservers **<AD domain controller IP address>**
   dns-search **<AD domain name>**
   ```

   > [!NOTE]
   > Сетевой интерфейс (`eth0`) может отличаться для разных компьютеров. Чтобы узнать, какой из них вы используете, выполните команду **ifconfig**. Затем скопируйте интерфейс, имеющий IP-адрес и переданные и полученные байты.

1. После изменения этого файла перезапустите сетевую службу.

   ```bash
   sudo ifdown eth0 && sudo ifup eth0
   ```

1. Далее убедитесь, что файл **/etc/resolv.conf** содержит строку, аналогичную следующей.

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

### <a name="rhel"></a>RHEL

1. Измените файл **/etc/sysconfig/network-scripts/ifcfg-eth0**, чтобы ваш домен Active Directory находился в списке поиска доменов. Или измените другой файл конфигурации интерфейса соответствующим образом.

   ```/etc/sysconfig/network-scripts/ifcfg-eth0
   PEERDNS=no
   DNS1=**<AD domain controller IP address>**
   DOMAIN="contoso.com com"
   ```

1. После изменения этого файла перезапустите сетевую службу.

   ```bash
   sudo systemctl restart network
   ```

1. Теперь убедитесь, что файл **/etc/resolv.conf** содержит строку, аналогичную следующей.

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

1. Если проверить связь с контроллером домена по-прежнему не удается, найдите полное доменное имя и IP-адрес контроллера домена. Пример доменного имени: **DC1.CONTOSO.COM**. Добавьте следующую запись в **/etc/hosts**:

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

### <a name="sles"></a>SLES

1. Измените файл **/etc/sysconfig/network/config**, чтобы IP-адрес контроллера домена Active Directory использовался для запросов DNS, а домен Active Directory находился в списке поиска доменов.

   ```/etc/sysconfig/network/config
   NETCONFIG_DNS_STATIC_SEARCHLIST=""
   NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
   ```

1. После изменения этого файла перезапустите сетевую службу.

   ```bash
   sudo systemctl restart network
   ```

1. Далее убедитесь, что файл **/etc/resolv.conf** содержит строку, аналогичную следующей.

   ```/etc/resolv.conf
   search contoso.com com
   nameserver **<AD domain controller IP address>**
   ```

## <a name="join-to-the-ad-domain"></a>Присоединение к домену AD

После проверки базовой конфигурации и связи с контроллером домена хост-компьютер SQL Server на базе Linux можно присоединить к контроллеру домена Active Directory двумя способами.

- [Вариант 1. Использование пакета SSSD](#option1)
- [Вариант 2. Использование служебных программ сторонних поставщиков openldap](#option2)

### <a id="option1"></a> Вариант 1. Использование пакета SSSD для присоединения к домену AD

Этот метод присоединяет узел SQL Server к домену AD с помощью пакетов **realmd** и **sssd**.

> [!NOTE]
> Это предпочтительный способ присоединения узла Linux к контроллеру домена AD.

Для присоединение узла SQL Server к домену Active Directory сделайте следующее.

1. Используйте [realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join), чтобы присоединить хост-компьютер к домену AD. Сначала нужно установить пакеты **realmd** и клиента Kerberos на хост-компьютере SQL Server с помощью диспетчера пакетов дистрибутива Linux.

   **RHEL:**

   ```base
   sudo yum install realmd krb5-workstation
   ```

   **SUSE:**

   ```bash
   sudo zypper install realmd krb5-client
   ```

   **Ubuntu:**

   ```bash
   sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
   ```

1. Если при установке пакета клиента Kerberos запрашивается имя области, введите имя домена прописными буквами.

1. Убедившись, что DNS настроена правильно, присоединитесь к домену с помощью указанной ниже команды. Нужно выполнить проверку подлинности с помощью учетной записи AD, имеющей достаточные права в AD для присоединения нового компьютера к домену. Эта команда создает учетную запись компьютера в AD, создает KEYTAB-файл узла **/etc/krb5.keytab**, настраивает домен в **/etc/sssd/sssd.conf** и обновляет **/etc/krb5.conf**.

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   ```

   Должно появиться сообщение `Successfully enrolled machine in realm`.

   В следующей таблице перечислены некоторые сообщения об ошибках, которые вы можете получить, и рекомендации по их устранению.

   | Сообщение об ошибке | Рекомендация |
   |---|---|
   | `Necessary packages are not installed` | Установите эти пакеты с помощью диспетчера пакетов дистрибутива Linux, прежде чем снова выполнять команду realm join. |
   | `Insufficient permissions to join the domain` | Выясните у администратора домена, достаточно ли у вас разрешений для присоединения компьютеров Linux к домену. |
   | `KDC reply did not match expectations` | Возможно, вы не указали правильное имя области для пользователя. В именах областей учитывается регистр, обычно используются прописные буквы, и их можно определить с помощью команды realm discover contoso.com. |

   SQL Server использует SSSD и NSS для сопоставления учетных записей пользователей и групп с идентификаторами безопасности (SID). Для успешного создания имен входа в Active Directory нужно настроить и запустить SSSD для SQL Server. **realmd** обычно выполняет это автоматически при присоединении к домену, но в некоторых случаях это нужно делать отдельно.

   Дополнительные сведения см. в статьях о [настройке SSSD вручную](https://access.redhat.com/articles/3023951) и [настройке NSS для работы с SSSD](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options).

1. Убедитесь, что теперь вы можете собирать сведения о пользователе из домена и получить билет Kerberos от имени этого пользователя. В следующем примере для этого используются команды **id**, [kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html) и [klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html).

   ```bash
   id user@contoso.com

   uid=1348601103(user@contoso.com) gid=1348600513(domain group@contoso.com) groups=1348600513(domain group@contoso.com)

   kinit user@CONTOSO.COM

   Password for user@CONTOSO.COM:

   klist
   Ticket cache: FILE:/tmp/krb5cc_1000
   Default principal: user@CONTOSO.COM
   ```

   > [!NOTE]
   > - Если **id user\@contoso.com** возвращает `No such user`, убедитесь, что служба SSSD успешно запущена, выполнив команду `sudo systemctl status sssd`. Если служба запущена и вы по-прежнему видите ошибку, попробуйте включить подробное ведение журнала для SSSD. Дополнительные сведения см. в разделе об [устранении неполадок SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting) в документации по Red Hat.
   >
   > - Если **kinit user\@CONTOSO.COM** возвращает `KDC reply did not match expectations while getting initial credentials`, убедитесь, что вы указали область прописными буквами.

Дополнительные сведения см. в разделе об [обнаружении доменов удостоверений и присоединении к ним](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html) в документации по Red Hat.

### <a id="option2"></a> Вариант 2. Использование служебных программ сторонних поставщиков openldap

Вы можете использовать сторонние служебные программы, такие как [PBIS](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/) или [Centrify](https://www.centrify.com/). В этой статье не рассматриваются действия для каждой отдельной служебной программы. Прежде чем продолжить, нужно воспользоваться одной из этих служебных программ, чтобы присоединить узел Linux для SQL Server к домену.  

SQL Server не использует код или библиотеку стороннего интегратора для запросов, связанных с AD. SQL Server всегда запрашивает AD с помощью вызовов библиотеки openldap напрямую в этой установке. Сторонние интеграторы используются только для присоединения узла Linux к домену AD, при этом SQL Server не взаимодействует с такими служебными программами напрямую.

> [!IMPORTANT]
> См. рекомендации по использованию параметра конфигурации **mssql-conf** `network.disablesssd` в разделе **Дополнительные параметры конфигурации** статьи [Использование проверки подлинности Active Directory с помощью SQL Server на базе Linux](sql-server-linux-active-directory-authentication.md#additionalconfig).

Убедитесь, что **/etc/krb5.conf** настроен правильно. Для большинства сторонних поставщиков Active Directory эта конфигурация выполняется автоматически. Однако проверьте **/etc/krb5.conf** на наличие следующих значений, чтобы избежать появления проблем в будущем.

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

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>Проверка правильности настройки обратной DNS

Следующая команда должна возвращать полное доменное имя узла, на котором выполняется SQL Server. Пример: **SqlHost.contoso.com**.

```bash
host **<IP address of SQL Server host>**
```

Выходные данные этой команды должны быть похожи на `**<reversed IP address>**.in-addr.arpa domain name pointer SqlHost.contoso.com`. Если эта команда не возвращает полное доменное имя узла или это имя неправильное, добавьте запись обратной записи DNS для узла SQL Server на базе Linux на DNS-сервер.

## <a name="next-steps"></a>Следующие шаги

Эта статья описывает необходимые условия для настройки SQL Server на хост-компьютере Linux с проверкой подлинности Active Directory. Чтобы завершить настройку SQL Server на Linux для поддержки учетных записей Active Directory, следуйте инструкциям в статье [Использование проверки подлинности Active Directory с SQL Server на Linux](sql-server-linux-active-directory-authentication.md).
