---
title: Использование сторонних поставщиков Active Directory с SQL Server в Linux | Документация Майкрософт
description: Этот учебник содержит действия по настройке проверки подлинности AD с помощью сторонних поставщиков
author: dylan-MSFT
ms.date: 07/25/2018
ms.author: dygray
manager: mikehab
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
helpviewer_keywords:
- Linux, AD authentication
ms.openlocfilehash: 288f46a2084166a1b7164ff8f0c0ef82b81fb16b
ms.sourcegitcommit: ca5430ff8e3f20b5571d092c81b1fb4c950ee285
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2018
ms.locfileid: "43381516"
---
# <a name="use-third-party-active-directory-providers-with-sql-server-on-linux"></a>Использование сторонних поставщиков Active Directory с SQL Server в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на хост-компьютере Linux, с проверкой подлинности AD при использовании сторонних поставщиков AD, таких как [PowerBroker удостоверения службы (PBI)](https://www.beyondtrust.com/), [Vintela проверки подлинности Services (VAS)](https://www.oneidentity.com/products/authentication-services/), и [Centrify](https://www.centrify.com/). Это руководство содержит действия, чтобы проверить конфигурацию AD, и он не предназначен для указания о том, как присоединить машину к домену. Подробные инструкции по присоединению к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] размещать домен с использованием области и SSSD, см. в разделе [проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).

## <a name="prerequisites"></a>предварительные требования

Прежде чем настроить проверку подлинности в AD, необходимо настроить контроллер домена AD (Windows) в сети и присоединения к вашей [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на узле Linux к домену AD. Можно использовать [элементы PBI](https://www.beyondtrust.com/), [VAS](https://www.oneidentity.com/products/authentication-services/), или [Centrify](https://www.centrify.com/).

> [!NOTE]
>
>В этом учебнике используется «contoso.com» и «CONTOSO.COM» как примеры имен доменом и соответственно. Он также использует «DC1. "CONTOSO.COM» в примере полное доменное имя контроллера домена. Следует заменить их своими собственными значениями.

## <a name="check-connection-to-domain-controller"></a>Проверьте подключение к контроллеру домена

Убедитесь, что вы можете связаться с контроллером домена с коротким, полное имя домена.

   ```bash
   ping contoso

   ping contoso.com
   ```

   Если откажет один из них обновите список поиска домена.

   - **Ubuntu**:

     Изменить `/etc/network/interfaces` файл таким образом, доменом AD в списке доменов поиска: 

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
     search contoso.com com  
     nameserver **<AD domain controller IP address>**
     ```

   - **RHEL**:

     Изменить `/etc/sysconfig/network-scripts/ifcfg-eth0` файл (или другой интерфейс конфигурации, в файл соответствующим образом), чтобы домен AD находится в списке доменов поиска:

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

   Если вы по-прежнему не удается проверить связь с контроллера домена, найти полное доменное имя (например DC1. CONTOSO.COM) и IP-адрес контроллера домена и добавьте следующую запись `/etc/hosts`

   ```/etc/hosts
   **<IP address>** DC1.CONTOSO.COM CONTOSO.COM CONTOSO
   ```

   - **SLES**:

     Изменить `/etc/sysconfig/network/config` файл, чтобы IP-адрес контроллера домена AD, которые будут использоваться для запросов DNS и доменом AD находится в списке доменов поиска:

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

## <a name="check-reverse-dns-is-properly-configured"></a>Проверьте, что обратного преобразования DNS настроен правильно

Следующая команда вернет полное доменное имя узла под управлением SQL Server (например) «SqlHost.contoso.com»).

   ```bash
   host **<IP address of SQL Server host>**
   # **<reversed IP address>**.in-addr.arpa domain name pointerSqlHost.contoso.com.
   ```

   Если это не возвращает полное доменное имя вашего узла или полное доменное имя неверное, добавить обратную запись DNS для вашего [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на узле Linux на DNS-сервер.

## <a name="check-your-krb5-configuration-is-correct"></a>Проверьте правильность конфигурации KRB5

Проверьте ваш `/etc/krb5.conf` настроен правильно. Для большинства поставщиков сторонних AD это выполняется автоматически. Тем не менее, проверьте `/etc/krb5.conf` следующие значения для предотвращения проблем в будущем:

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

В этой статье мы рассмотрели, как настроить [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на хост-компьютере Linux, с проверкой подлинности AD при использовании AD сторонних поставщиков. Чтобы завершить настройку [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] в Linux для поддержки учетных записей AD, следуйте инструкциям в [проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md).

> [!div class="nextstepaction"]
> [Использование проверки подлинности Active Directory с SQL Server в Linux](sql-server-linux-active-directory-authentication.md)

> [!NOTE]
>
> Вы можете пропустить раздел «Узел соединения SQL Server к домену AD» в [проверки подлинности Active Directory для использования с SQL Server в Linux](sql-server-linux-active-directory-authentication.md) как было сделано, в этом руководстве.