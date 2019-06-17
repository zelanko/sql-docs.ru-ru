---
title: Присоединяйтесь к SQL Server в Linux в Active Directory
titleSuffix: SQL Server
description: ''
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: rothja
ms.date: 04/01/2019
manager: craigg
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: 50f2685b5b981cddfdba61f91b7ec04e9f6345d6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822524"
---
# <a name="join-sql-server-on-a-linux-host-to-an-active-directory-domain"></a>Присоединяйтесь к SQL Server на узле Linux к домену Active Directory

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье содержит общие рекомендации о том, как присоединить хост-компьютере SQL Server Linux к домену Active Directory (AD). Двумя способами: использовать встроенный пакет SSSD или использовать сторонние поставщики Active Directory. Примеры продуктов независимых производителей домена соединения [PowerBroker удостоверения службы (PBI)](https://www.beyondtrust.com/), [одно удостоверение](https://www.oneidentity.com/products/authentication-services/), и [Centrify](https://www.centrify.com/). Это руководство содержит инструкции по проверке конфигурации Active Directory. Тем не менее он не предназначен для предоставления инструкций о том, как присоединить машину к домену, при использовании сторонних программ.

## <a name="prerequisites"></a>предварительные требования

Прежде чем настраивать проверку подлинности Active Directory, необходимо настроить контроллер домена Active Directory, Windows, в сети. Затем Присоединяйтесь к серверу SQL Server на узле Linux к домену Active Directory.

> [!IMPORTANT]
> Пример действия, описанные в этой статье, только в качестве рекомендации. Фактические действия может немного отличаться в вашей среде, в зависимости от настройки всей среды. Обратитесь в службу системное и доменное администраторов для вашей среды для конкретной конфигурации, настройки, а также все необходимые устранения неполадок.

## <a name="check-the-connection-to-a-domain-controller"></a>Проверьте подключение к контроллеру домена

Проверьте, что могут обращаться к контроллеру домена с краткое и полное именами домена:

```bash
ping contoso
ping contoso.com
```

> [!TIP]
> В этом руководстве используется **contoso.com** и **CONTOSO.COM** как примеры доменом и областью имен, соответственно. Он также использует **DC1. CONTOSO.COM** как примере полное доменное имя контроллера домена. Необходимо заменить эти имена собственными значениями.

Если любой из этих проверок имя, нужно обновите список поиска домена. Следующие разделы содержат инструкции по Ubuntu, Red Hat Enterprise Linux (RHEL) и SUSE Linux Enterprise Server (SLES) соответственно.

### <a name="ubuntu"></a>Ubuntu

1. Изменить **/etc/network/interfaces** файл таким образом, доменом Active Directory в списке доменов поиска:

   ```/etc/network/interfaces
   # The primary network interface
   auto eth0
   iface eth0 inet dhcp
   dns-nameservers **<AD domain controller IP address>**
   dns-search **<AD domain name>**
   ```

   > [!NOTE]
   > Сетевой интерфейс, `eth0`, могут отличаться для разных компьютерах. Чтобы узнать, какой из них, вы используете, выполните **ifconfig**. Затем скопируйте интерфейсе с IP-адресом и отправленных и полученных байтов.

1. Изменив этот файл, перезапустите сетевую службу:

   ```bash
   sudo ifdown eth0 && sudo ifup eth0
   ```

1. Затем убедитесь, что ваш **/etc/resolv.conf** файл содержит строку, как в следующем примере:

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

### <a name="rhel"></a>RHEL

1. Изменить **/etc/sysconfig/network-scripts/ifcfg-eth0** файл таким образом, доменом Active Directory в списке доменов поиска. Или измените другой файл конфигурации интерфейса соответствующим образом:

   ```/etc/sysconfig/network-scripts/ifcfg-eth0
   PEERDNS=no
   DNS1=**<AD domain controller IP address>**
   DOMAIN="contoso.com com"
   ```

1. Изменив этот файл, перезапустите сетевую службу:

   ```bash
   sudo systemctl restart network
   ```

1. Теперь убедитесь, что ваш **/etc/resolv.conf** файл содержит строку, как в следующем примере:

   ```/etc/resolv.conf
   search contoso.com com  
   nameserver **<AD domain controller IP address>**
   ```

1. Если вы по-прежнему не удается проверить связь с контроллера домена, найти полное доменное имя и IP-адрес контроллера домена. С именем домена в примере является **DC1. CONTOSO.COM**. Добавьте следующую запись **/etc/hosts**:

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

### <a name="sles"></a>SLES

1. Изменить **/etc/sysconfig/network/config** файл, чтобы ваш IP-адрес контроллера домена для Active Directory используется для запросов DNS и доменом Active Directory находится в списке доменов поиска:

   ```/etc/sysconfig/network/config
   NETCONFIG_DNS_STATIC_SEARCHLIST=""
   NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
   ```

1. Изменив этот файл, перезапустите сетевую службу:

   ```bash
   sudo systemctl restart network
   ```

1. Затем убедитесь, что ваш **/etc/resolv.conf** файл содержит строку, как в следующем примере:

   ```/etc/resolv.conf
   search contoso.com com
   nameserver **<AD domain controller IP address>**
   ```

## <a name="join-to-the-ad-domain"></a>Присоединение к домену AD

После проверки базовой конфигурации и подключения с контроллером домена, существует два варианта для присоединения к SQL Server Linux хост-компьютере с контроллером домена Active Directory:

- [Вариант 1. Использовать пакет SSSD](#option1)
- [Вариант 2. Использовать служебные программы openldap стороннего поставщика](#option2)

### <a id="option1"></a> Вариант 1. Пакет sssd будет использовать для присоединения к домену AD

Этот метод объединяет узла SQL Server к домену AD с помощью **realmd** и **sssd** пакетов.

> [!NOTE]
> Это предпочтительный метод объединения на узле Linux к контроллеру домена AD.

Для присоединения узла SQL Server к домену Active Directory, следуйте инструкциям ниже:

1. Используйте [realmd](https://www.freedesktop.org/software/realmd/docs/guide-active-directory-join) для присоединения к домену AD хост-компьютере. Сначала необходимо установить оба **realmd** и пакеты клиента Kerberos на хост-компьютере SQL Server, с помощью диспетчера пакетов дистрибутива Linux:

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

1. Если пакет установки клиента Kerberos запросит имя области, введите имя домена прописными буквами.

1. Убедившись, что ваша служба DNS настроена правильно, присоединение к домену, выполнив следующую команду. Вы должны пройти аутентификацию с помощью учетной записи AD, имеет достаточные права в AD, чтобы присоединить машину к домену. Эта команда создает новую учетную запись компьютера в AD, создает **/etc/krb5.keytab** размещения файла keytab, настраивает домен в **/etc/sssd/sssd.conf**и обновления **/etc/krb5.conf**.

   ```bash
   sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
   ```

   Вы увидите сообщение, `Successfully enrolled machine in realm`.

   В следующей таблице перечислены некоторые сообщения об ошибках, которые могли получать и предложения по их устранению.

   | Сообщение об ошибке | Рекомендация |
   |---|---|
   | `Necessary packages are not installed` | Установите эти пакеты, с помощью диспетчера пакетов дистрибутива Linux перед повторным запуском команда присоединения сферы. |
   | `Insufficient permissions to join the domain` | Проверьте наличие достаточных разрешений на присоединение компьютеров Linux к домену с администратором домена. |
   | `KDC reply did not match expectations` | Возможно, не указали правильные имя пользователя. Имена областей чувствительны к регистру, обычно верхний регистр и можно идентифицировать с помощью команды область обнаружения contoso.com. |

   SQL Server использует SSSD и NSS для сопоставления учетных записей пользователей и групп идентификаторы безопасности (SID). SSSD должна быть настроена и запущена для SQL Server для создания имен входа AD успешно. **realmd** обычно делает это автоматически в процессе присоединения к домену, но в некоторых случаях, необходимо сделать это отдельно.

   Дополнительные сведения см. в разделе Практическое [вручную настроить SSSD](https://access.redhat.com/articles/3023951), и [Настройка NSS для работы с SSSD](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system-level_authentication_guide/configuring_services#Configuration_Options-NSS_Configuration_Options).

1. Убедитесь, что теперь можно собрать сведения о пользователе из домена и что вы можете получить билет Kerberos от имени этого пользователя. В следующем примере используется **идентификатор**, [kinit](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/kinit.html), и [klist](https://web.mit.edu/kerberos/krb5-1.12/doc/user/user_commands/klist.html) команд для этого.

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
   > - Если **идентификатор user@contoso.com**  возвращении `No such user`, убедитесь, что служба SSSD успешно запущена с помощью команды `sudo systemctl status sssd`. Если служба запущена, и по-прежнему отображается ошибка, попробуйте включить подробное ведение журнала для SSSD. Дополнительные сведения см. в документации Red Hat для [Устранение неполадок SSSD](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/System-Level_Authentication_Guide/trouble.html#SSSD-Troubleshooting).
   >
   > - Если **kinit user@CONTOSO.COM**  возвращении `KDC reply did not match expectations while getting initial credentials`, убедитесь, что вы указали область в верхнем регистре.

Дополнительные сведения см. в документации Red Hat для [Discovering и присоединение доменов удостоверений](https://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/Windows_Integration_Guide/realmd-domain.html).

### <a id="option2"></a> Вариант 2. Использовать служебные программы openldap стороннего поставщика

Можно использовать сторонние программы, такие как [элементы PBI](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), или [Centrify](https://www.centrify.com/). В этой статье рассматриваются шаги для каждого отдельного служебной программы. Сначала необходимо использовать один из этих служебных программ для присоединения узла Linux для SQL Server к домену перед продолжением вперед.  

SQL Server не использует интегратор стороннего кода или библиотеки для любых запросов, связанных с AD. SQL Server всегда запрашивает AD, используя вызовы openldap библиотеки непосредственно в этой программе установки. Интеграторы сторонних используются только для присоединения узла Linux к домену AD и SQL Server не поддерживает любой прямой обмен данными с помощью этих программ.

> [!IMPORTANT]
> См. рекомендации по использованию **mssql-conf** `network.disablesssd` параметр конфигурации в **Дополнительные параметры конфигурации** статьи [используйте Active Аутентификация с помощью SQL Server в Linux](sql-server-linux-active-directory-authentication.md#additionalconfig).

Убедитесь, что ваш **/etc/krb5.conf** настроен правильно. Для большинства поставщиков сторонних Active Directory эта настройка выполняется автоматически. Тем не менее, проверьте **/etc/krb5.conf** следующие значения для предотвращения проблем в будущем:

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

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>Убедитесь, что правильно настроен обратной зоны DNS

Следующая команда вернет полное доменное имя (FQDN) узла, на котором выполняется SQL Server. Например, **SqlHost.contoso.com**.

```bash
host **<IP address of SQL Server host>**
```

Выходные данные этой команды должен быть аналогичен `**<reversed IP address>**.in-addr.arpa domain name pointer SqlHost.contoso.com`. Если эта команда не возвращает полное доменное имя вашего узла или полное доменное имя неверное, добавьте обратный DNS-запись для SQL Server на узле Linux на DNS-сервер.

## <a name="next-steps"></a>Следующие шаги

В этой статье рассматриваются предварительные требования Настройка SQL Server на хост-компьютере Linux с помощью проверки подлинности Active Directory. Чтобы завершить настройку SQL Server в Linux для поддержки учетных записей Active Directory, следуйте инструкциям в [проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).