---
title: Подключение к SQL Server с использованием проверки подлинности Windows (Kerberos)
description: Узнайте, как подключить Azure Data Studio к SQL Server с помощью встроенной проверки подлинности Microsoft Kerberos.
ms.prod: azure-data-studio
ms.technology: azure-data-studio
author: markingmyname
ms.author: maghan
ms.reviewer: alayu, maghan, sstein
ms.topic: conceptual
ms.custom: seodec18
ms.date: 09/24/2018
ms.openlocfilehash: bb9735ec85ba8b6481156fb55e662bc55363dc7a
ms.sourcegitcommit: 5da46e16b2c9710414fe36af9670461fb07555dc
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2020
ms.locfileid: "89283736"
---
# <a name="connect-azure-data-studio-to-your-sql-server-using-windows-authentication---kerberos"></a>Подключение Azure Data Studio к своему SQL Server с использованием проверки подлинности Windows — Kerberos

Azure Data Studio поддерживает подключение к SQL Server с помощью Kerberos.

Чтобы использовать встроенную проверку подлинности (проверку подлинности Windows) в macOS или Linux, нужно настроить **билет Kerberos**, связывающий вашего текущего пользователя с учетной записью домена Windows.

## <a name="prerequisites"></a>Предварительные требования

- Доступ к компьютеру, присоединенному к домену Windows, для запроса контроллера домена Kerberos.
- SQL Server должен быть настроен для разрешения проверки подлинности Kerberos. Для драйвера клиента, работающего в Unix, встроенная проверка подлинности поддерживается только с помощью Kerberos. Дополнительные сведения см. в статье [Использовании встроенной проверки подлинности Kerberos для подключения к SQL Server](../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md). Для каждого экземпляра SQL Server, к которому вы пытаетесь подключиться, должны быть зарегистрированы имена субъектов-служб. Дополнительные сведения см. в разделе [Регистрация имени участника-службы](/previous-versions/sql/sql-server-2008-r2/ms191153(v=sql.105)#SPN%20Formats).


## <a name="checking-if-sql-server-has-kerberos-setup"></a>Проверка наличия настройки Kerberos в SQL Server

Войдите на хост-компьютер SQL Server. В командной строке Windows используйте `setspn -L %COMPUTERNAME%`, чтобы вывести список всех имен субъектов-служб для узла. Должны отобразиться записи, начинающиеся с MSSQLSvc/имя_узла.домен.com, что означает, что SQL Server зарегистрировал имя субъекта-службы и готов принять проверку подлинности Kerberos. 
- Если у вас нет доступа к узлу SQL Server, то из любой другой ОС Windows, присоединенной к тому же Active Directory, можно использовать команду `setspn -L <SQLSERVER_NETBIOS>`, где < SQLSERVER_NETBIOS > — имя компьютера узла SQL Server.


## <a name="get-the-kerberos-key-distribution-center"></a>Получение центра распространения ключей Kerberos

Найдите значение конфигурации для KDC (центр распространения ключей) Kerberos. Выполните следующую команду на компьютере Windows, присоединенном к домену Active Directory. 

Запустите `cmd.exe` и выполните `nltest`.

```
nltest /dsgetdc:DOMAIN.COMPANY.COM (where "DOMAIN.COMPANY.COM" maps to your domain's name)

Sample Output
DC: \\dc-33.domain.company.com
Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
...
The command completed successfully
```
Скопируйте имя контроллера домена, которое является требуемым значением конфигурации KDC, в данном случае это dc-33.domain.company.com.

## <a name="join-your-os-to-the-active-directory-domain-controller"></a>Присоединение операционной системы к контроллеру домена Active Directory

### <a name="ubuntu"></a>Ubuntu
```bash
sudo apt-get install realmd krb5-user software-properties-common python-software-properties packagekit
```

Измените файл `/etc/network/interfaces`, чтобы IP-адрес вашего контроллера домена AD был указан в качестве параметра dns-nameserver. Пример: 

```/etc/network/interfaces
<...>
# The primary network interface
auth eth0
iface eth0 inet dhcp
dns-nameservers **<AD domain controller IP address>**
dns-search **<AD domain name>**
```

> [!NOTE]
> Сетевой интерфейс (eth0) может отличаться для разных компьютеров. Чтобы узнать, какой из них используется, выполните команду ifconfig и скопируйте интерфейс, имеющий IP-адрес и переданные и полученные байты.

После изменения этого файла перезапустите сетевую службу.

```bash
sudo ifdown eth0 && sudo ifup eth0
```

Теперь убедитесь, что файл `/etc/resolv.conf` содержит строку, аналогичную следующей.  

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

Измените файл `/etc/sysconfig/network-scripts/ifcfg-eth0` (или другой соответствующий файл конфигурации интерфейса), чтобы IP-адрес вашего контроллера домена AD был указан в качестве параметра DNS-сервера.

```/etc/sysconfig/network-scripts/ifcfg-eth0
<...>
PEERDNS=no
DNS1=**<AD domain controller IP address>**
```

После изменения этого файла перезапустите сетевую службу.

```bash
sudo systemctl restart network
```

Теперь убедитесь, что файл `/etc/resolv.conf` содержит строку, аналогичную следующей.  

```Code
nameserver **<AD domain controller IP address>**
```

```bash
sudo realm join contoso.com -U 'user@CONTOSO.COM' -v
<...>
* Success
   
```

### <a name="macos"></a>macOS

- Присоедините macOS к контроллеру домена Active Directory, выполнив следующие действия.

## <a name="configure-kdc-in-krb5conf"></a>Настройка KDC в krb5.conf

Измените `/etc/krb5.conf` в любом редакторе. Настройте следующие ключи.

```bash
sudo vi /etc/krb5.conf

[libdefaults]
  default_realm = DOMAIN.COMPANY.COM
 
[realms]
DOMAIN.COMPANY.COM = {
   kdc = dc-33.domain.company.com
}
```

Сохраните файл krb5.conf и закройте редактор.

> [!NOTE]
> Домен должен быть указан только прописными буквами.


## <a name="test-the-ticket-granting-ticket-retrieval"></a>Тестирование извлечения билета на получение билетов

Получите билет на получение билетов (TGT) из KDC.

```bash
kinit username@DOMAIN.COMPANY.COM
```

Просмотрите доступные билеты с помощью klist. Если kinit выполнен успешно, вы увидите билет. 

```bash
klist

krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM.
```

## <a name="connect-using-azure-data-studio"></a>Подключение с помощью Azure Data Studio

* Создайте профиль подключения.

* Выберите **Проверка подлинности Windows** в качестве типа проверки подлинности.

* Заполните профиль подключения и нажмите кнопку **Подключить**.

После успешного подключения сервер отображается на боковой панели *Серверы*.