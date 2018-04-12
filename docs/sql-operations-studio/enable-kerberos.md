---
title: Использование проверки подлинности Active Directory (Kerberos) при соединении с SQL Operations Studio (preview) | Документы Microsoft
description: Включение Kerberos для использования проверки подлинности Active Directory для SQL Operations Studio (preview)
ms.custom: tools|sos
ms.date: 11/17/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: ''
ms.topic: article
author: meet-bhagdev
ms.author: meetb
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbd229a0106506f744074df760ee10f871474ebb
ms.sourcegitcommit: 094c46e7fa6de44735ed0040c65a40ec3d951b75
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="connect-includename-sosincludesname-sos-shortmd-to-your-sql-server-using-windows-authentication---kerberos"></a>Подключение [!INCLUDE[name-sos](../includes/name-sos-short.md)] к экземпляру SQL Server с использованием проверки подлинности Windows — Kerberos 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] поддерживает подключение к SQL Server с помощью Kerberos.

Чтобы использовать встроенную проверку подлинности (проверка подлинности Windows) на macOS или Linux, необходимо настроить **билета Kerberos** связывание текущего пользователя с учетной записью домена Windows. 

## <a name="prerequisites"></a>предварительные требования

- Доступ к компьютером присоединенных к домену Windows, чтобы выполнять запросы к контроллеру домена Kerberos.
- Необходимо настроить SQL Server для проверки подлинности Kerberos. Для драйвера клиента под управлением Unix встроенная проверка подлинности поддерживается только с помощью Kerberos. Дополнительные сведения о настройке Sql Server для проверки подлинности с помощью Kerberos, можно найти [здесь](https://support.microsoft.com/en-us/help/319723/how-to-use-kerberos-authentication-in-sql-server). Должна существовать имен SPN, зарегистрированных для каждого экземпляра Sql Server, вы пытаетесь подключиться. Представлены сведения о формате имен участников-служб SQL Server [здесь](https://technet.microsoft.com/en-us/library/ms191153%28v=sql.105%29.aspx#SPN%20Formats)


## <a name="checking-if-sql-server-has-kerberos-setup"></a>Проверка наличия установки Kerberos в Sql Server

Имя входа на хост-компьютер Sql Server. Из командной строки в Windows, используйте `setspn -L %COMPUTERNAME%` для просмотра списка всех имен участника-службы для узла. Вы увидите записи, которые начинаются с MSSQLSvc/HostName.Domain.com это означает, что Sql Server зарегистрировал имени участника-службы и готов к приему проверки подлинности Kerberos. 
- Если нет доступа к узлу Sql Server, то из любой другой ОС Windows соединяется с одной службой Active Directory, можно использовать команду `setspn -L <SQLSERVER_NETBIOS>` где < SQLSERVER_NETBIOS > — имя компьютера узла Sql Server.


## <a name="get-the-kerberos-key-distribution-center"></a>Получить центра распространения ключей Kerberos

Найдите значение конфигурации центра распространения КЛЮЧЕЙ Kerberos (центр распространения ключей). На компьютере Windows, который присоединен к домену Active Directory, выполните следующую команду: 

Запуск `cmd.exe` и запустите `nltest`.

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where “DOMAIN.COMPANY.COM” maps to your domain’s name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
Скопируйте имя контроллера домена, необходимо указать значение конфигурации KDC в этом вариантов 33.domain.company.com контроллера домена

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>Присоедините ОС к контроллеру домена Active Directory

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

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

Убедитесь, что теперь ваш `/etc/resolv.conf` файл содержит строку следующего вида:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
```
   
### <a name="redhat-enterprise-linux"></a>RedHat Enterprise Linux
```bash
sudo yum install realmd krb5-workstation
```

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

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>MacOS

- Присоединение к macOS к контроллеру домена Active Directory [описанные ниже] (https://support.apple.com/kb/PH26282?viewlocale=en_US&locale=en_US).



## <a name="configure-kdc-in-krb5conf"></a>Если настроен центр KDC в krb5.conf

Изменить `/etc/krb5.conf` в редакторе по своему усмотрению. Настройте следующие ключи

```bash
sudo vi /etc/krb5.conf

[libdefaults]
  default_realm = DOMAIN.COMPANY.COM
 
[realms]
DOMAIN.COMPANY.COM = {
   kdc = dc-33.domain.company.com
}
```

Затем сохраните файл krb5.conf и выход

> [!NOTE]
> Домен должен быть в все прописные


## <a name="test-the-ticket-granting-ticket-retrieval"></a>Тестовые извлечение билет предоставления билета

Получите билет предоставления билета (TGT) из центра распространения КЛЮЧЕЙ.

```bash
kinit username@DOMAIN.COMPANY.COM
```

Просмотр доступных билеты, с помощью kinit. При успешном выполнении kinit, вы увидите, что билет. 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-includename-sosincludesname-sos-shortmd"></a>Подключение с использованием [!INCLUDE[name-sos](../includes/name-sos-short.md)]

* Создание нового профиля подключения

* Выберите **проверки подлинности Windows** как тип проверки подлинности

* Завершить профиля подключения, нажмите кнопку **Connect**

После успешного подключения сервера отображается в *серверы* боковой панели.
