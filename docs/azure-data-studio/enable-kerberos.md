---
title: Использовать проверку подлинности Active Directory (Kerberos)
titleSuffix: Azure Data Studio
description: Узнайте, как включить Kerberos для использования проверки подлинности Active Directory для Azure Data Studio
ms.custom: seodec18
ms.date: 09/24/2018
ms.prod: sql
ms.technology: azure-data-studio
ms.reviewer: alayu; sstein
ms.topic: conceptual
author: meet-bhagdev
ms.author: meetb
ms.openlocfilehash: 5c8fae6bf1333742b40e9c8aae4ee575736058cd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67959668"
---
# <a name="connect-includename-sosincludesname-sos-shortmd-to-your-sql-server-using-windows-authentication---kerberos"></a>Подключение [!INCLUDE[name-sos](../includes/name-sos-short.md)] к серверу SQL Server, использование проверки подлинности Windows — Kerberos 

[!INCLUDE[name-sos](../includes/name-sos-short.md)] поддерживает подключение к SQL Server с помощью Kerberos.

Чтобы использовать встроенную проверку подлинности (проверка подлинности Windows) в macOS или Linux, необходимо настроить **билет Kerberos** связывание текущего пользователя для учетной записи домена Windows. 

## <a name="prerequisites"></a>предварительные требования

- Доступ к домену компьютере Windows для отправки запросов контроллера домена Kerberos.
- SQL Server должен позволять проводить проверку подлинности Kerberos. Для драйвера клиента под управлением Unix встроенная проверка подлинности поддерживается только с помощью Kerberos. Дополнительные сведения о настройке Sql Server для проверки подлинности с помощью Kerberos можно найти [здесь](https://support.microsoft.com/help/319723/how-to-use-kerberos-authentication-in-sql-server). Должно быть зарегистрированы для каждого экземпляра Sql Server, вы пытаетесь подключиться к SPN. Подробные сведения о формате имен участников-служб SQL Server указаны [здесь](https://technet.microsoft.com/library/ms191153%28v=sql.105%29.aspx#SPN%20Formats)


## <a name="checking-if-sql-server-has-kerberos-setup"></a>Проверка наличия установки Kerberos в Sql Server

Войдите в хост-компьютере Sql Server. Из командной строки в Windows, используйте `setspn -L %COMPUTERNAME%` Чтобы получить список всех имен субъекта-службы для узла. Вы увидите записи, которые начинаются с MSSQLSvc/HostName.Domain.com это означает, что Sql Server зарегистрировал SPN и готова к приему проверки подлинности Kerberos. 
- Если у вас нет доступа к узлу сервера Sql Server, а затем из любой другой Windows ОС, присоединены к одной Active Directory, можно использовать команду `setspn -L <SQLSERVER_NETBIOS>` где < SQLSERVER_NETBIOS > — имя компьютера узла сервера Sql Server.


## <a name="get-the-kerberos-key-distribution-center"></a>Получение центра распространения ключей Kerberos

Найдите значение конфигурации Kerberos KDC (центр распространения ключей). На компьютере Windows, которая соединяется с доменом Active Directory, выполните следующую команду: 

Запуск `cmd.exe` и запустите `nltest`.

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where "DOMAIN.COMPANY.COM" maps to your domain's name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
Скопируйте имя контроллера домена, требуется значение конфигурации KDC в этот вариантов 33.domain.company.com контроллера домена

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>Присоедините своей операционной системы к контроллеру домена Active Directory

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

Изменить `/etc/network/interfaces` файл таким образом, чтобы контроллер домена AD IP-адрес указан в качестве dns-имени сервера. Например: 

```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
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

Теперь убедитесь, что ваш `/etc/resolv.conf` файл содержит строку следующего вида:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
```
   
### <a name="redhat-enterprise-linux"></a>Red Hat Enterprise Linux
```bash
sudo yum install realmd krb5-workstation
```

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

Теперь убедитесь, что ваш `/etc/resolv.conf` файл содержит строку следующего вида:  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>macOS

- Присоедините macOS контроллера домена Active Directory, выполнив следующие действия:



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

Затем сохраните файл krb5.conf и выхода

> [!NOTE]
> Домен должен быть прописными буквами


## <a name="test-the-ticket-granting-ticket-retrieval"></a>Тестовые извлечение билет предоставления билета

Получите билет предоставления билета (TGT) из центра распространения КЛЮЧЕЙ.

```bash
kinit username@DOMAIN.COMPANY.COM
```

Просмотр доступных билеты, с помощью klist. При успешном выполнении kinit вы увидите, что запрос в службу. 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-includename-sosincludesname-sos-shortmd"></a>Подключение с использованием [!INCLUDE[name-sos](../includes/name-sos-short.md)]

* Создать новый профиль подключения

* Выберите **проверки подлинности Windows** как тип проверки подлинности

* Завершить профиль подключения, нажмите кнопку **Connect**

После успешного подключения сервер появится в *серверы* боковой панели.
