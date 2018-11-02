---
title: Использование сторонних поставщиков Active Directory с SQL Server в Linux | Документация Майкрософт
description: Этот учебник содержит действия по настройке проверки подлинности Active Directory с помощью сторонних поставщиков
author: dylan-MSFT
ms.date: 07/25/2018
ms.author: dygray
manager: mikehab
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AD authentication
ms.openlocfilehash: 0ffe146de3a842f9c273b4dbba2a9fe4d9ff7ff5
ms.sourcegitcommit: 41979c9d511b3eeb45134d30ccb0dbc6bba70f1a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/01/2018
ms.locfileid: "50757999"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>Использование сторонних поставщиков Active Directory с SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на хост-компьютере Linux с помощью проверки подлинности Active Directory при использовании сторонних поставщиков Active Directory. Примерами являются [PowerBroker удостоверения службы (PBI)](https://www.beyondtrust.com/), [одно удостоверение](https://www.oneidentity.com/products/authentication-services/), и [Centrify](https://www.centrify.com/). Это руководство содержит инструкции по проверке конфигурации Active Directory. Она не предназначена для указания о том, как присоединить машину к домену. Подробные инструкции по присоединению к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] узла к домену с помощью realmd и SSSD, см. в разделе [проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).

## <a name="prerequisites"></a>предварительные требования

Прежде чем настраивать проверку подлинности Active Directory, необходимо настроить контроллер домена Active Directory, Windows, в сети. Затем присоединиться к вашей [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на узле Linux к домену Active Directory. Можно использовать [элементы PBI](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), или [Centrify](https://www.centrify.com/).

> [!NOTE]
>
>В этом руководстве используется **`contoso.com`** и **`CONTOSO.COM`** как примеры доменом и областью имен, соответственно. Он также использует **`DC1.CONTOSO.COM`** как примере полное доменное имя контроллера домена. Эти имена следует заменить собственными значениями.

## <a name="check-the-connection-to-a-domain-controller"></a>Проверьте подключение к контроллеру домена

Проверьте, что могут обращаться к контроллеру домена с краткое и полное именами домена:

```bash
ping contoso

ping contoso.com
```

Если любой из этих проверок имя, нужно обновите список поиска домена:

- **Ubuntu**

  Изменить `/etc/network/interfaces` файл таким образом, доменом Active Directory в списке доменов поиска: 

  ```/etc/network/interfaces
  <...>
  # The primary network interface
  auto eth0
  iface eth0 inet dhcp
  dns-nameservers **<AD domain controller IP address>**
  dns-search **<AD domain name>**
  ```

  > [!NOTE]  
  > Сетевой интерфейс, **eth0**, могут отличаться для разных компьютерах. Чтобы узнать, какой из них, вы используете, выполните **ifconfig**. Затем скопируйте интерфейсе с IP-адресом и отправленных и полученных байтов.

  Изменив этот файл, перезапустите сетевую службу:

  ```bash
  sudo ifdown eth0 && sudo ifup eth0
  ```

  Теперь убедитесь, что ваш `/etc/resolv.conf` файл содержит строку, как в следующем примере:  

  ```/etc/resolv.conf
  search contoso.com com  
  nameserver **<AD domain controller IP address>**
  ```

- **RHEL**

  Изменить `/etc/sysconfig/network-scripts/ifcfg-eth0` файл таким образом, доменом Active Directory в списке доменов поиска. Или измените другой файл конфигурации интерфейса соответствующим образом:

  ```/etc/sysconfig/network-scripts/ifcfg-eth0
  <...>
  PEERDNS=no
  DNS1=**<AD domain controller IP address>**
  DOMAIN="contoso.com com"
  ```

  Изменив этот файл, перезапустите сетевую службу:

  ```bash
  sudo systemctl restart network
  ```

  Теперь убедитесь, что ваш `/etc/resolv.conf` файл содержит строку, как в следующем примере:  

  ```/etc/resolv.conf
  search contoso.com com  
  nameserver **<AD domain controller IP address>**
  ```

  Если вы по-прежнему не удается проверить связь с контроллера домена, найти полное доменное имя и IP-адрес контроллера домена. С именем домена в примере является `DC1.CONTOSO.COM`. Добавьте следующую запись `/etc/hosts`:

  ```/etc/hosts
  **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
  ```

- **SLES**

  Изменить `/etc/sysconfig/network/config` файл, чтобы ваш IP-адрес контроллера домена для Active Directory используется для запросов DNS, и доменом Active Directory находится в списке доменов поиска:

  ```/etc/sysconfig/network/config
  <...>
  NETCONFIG_DNS_STATIC_SEARCHLIST=""
  NETCONFIG_DNS_STATIC_SERVERS="**<AD domain controller IP address>**"
  ```

  Изменив этот файл, перезапустите сетевую службу:

  ```bash
  sudo systemctl restart network
  ```

  Теперь убедитесь, что ваш `/etc/resolv.conf` файл содержит строку, как в следующем примере:

  ```/etc/resolv.conf
  search contoso.com com
  nameserver **<AD domain controller IP address>**
  ```

## <a name="check-that-the-reverse-dns-is-properly-configured"></a>Убедитесь, что правильно настроен обратной зоны DNS

Следующая команда вернет полное доменное имя узла, на котором выполняется SQL Server. Например, **`SqlHost.contoso.com`**.

```bash
host **<IP address of SQL Server host>**
# **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
```

Если эта команда не возвращает полное доменное имя вашего узла или полное доменное имя неверное, добавить обратный DNS-запись для вас: [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на узле Linux на DNS-сервер.

## <a name="check-that-your-krb5-configuration-is-correct"></a>Проверьте правильность конфигурации KRB5

Убедитесь, что ваш `/etc/krb5.conf` настроен правильно. Для большинства поставщиков сторонних Active Directory эта настройка выполняется автоматически. Тем не менее, проверьте `/etc/krb5.conf` следующие значения для предотвращения проблем в будущем:

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

## <a name="next-steps"></a>Следующие шаги

В этой статье описывается, как настроить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на хост-компьютере Linux с помощью проверки подлинности Active Directory при использовании сторонних поставщиков Active Directory. Чтобы завершить настройку [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux для поддержки учетных записей Active Directory, следуйте инструкциям в [проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).

> [!div class="nextstepaction"]
> [Использование проверки подлинности Active Directory с SQL Server в Linux](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> Вы можете пропустить **узла присоединиться к SQL Server к домену Active Directory** статьи [проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md) как вы только что выполнили, в этом руководстве.
