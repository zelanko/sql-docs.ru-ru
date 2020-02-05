---
title: Настройка MSDTC в Linux
description: В этой статье представлено пошаговое руководство по настройке MSDTC в Linux.
author: VanMSFT
ms.author: vanto
ms.date: 08/01/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.openlocfilehash: a39e0a743053db694efc2d0e8176e659d7e376d1
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68995869"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Сведения о настройке координатора распределенных транзакций (Майкрософт) (MSDTC) в Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка координатора распределенных транзакций Майкрософт (MSDTC) в Linux.

> [!NOTE]
> MSDTC в Linux поддерживается в SQL Server 2017 начиная с накопительного пакета обновления 16.

## <a name="overview"></a>Обзор

Чтобы включить распределенные транзакции в SQL Server на Linux, в SQL Server вводится MSDTC и функция сопоставителя конечных точек RPC. По умолчанию процесс сопоставления конечных точек RPC прослушивает порт 135 на предмет входящих запросов RPC и предоставляет удаленным запросам сведения о зарегистрированных компонентах. Удаленные запросы могут использовать сведения, возвращенные сопоставителем конечных точек, для взаимодействия с зарегистрированными компонентами RPC, такими как службы MSDTC. Процессу требуются права суперпользователя для привязки к известным портам (номера портов меньше 1024) в Linux. Чтобы не запускать SQL Server с правами root для процесса сопоставителя конечных точек RPC, системные администраторы должны использовать iptables для создания преобразования сетевых адресов (NAT) для маршрутизации трафика через порт 135 в процесс сопоставления конечных точек RPC SQL Server.

Координатор распределенных транзакций использует два параметра конфигурации для служебной программы mssql-conf.

| Параметр mssql-conf | Description |
|---|---|
| **network.rpcport** | TCP-порт, к которому привязан процесс сопоставителя конечных точек RPC. |
| **distributedtransaction.servertcpport** | Порт, который прослушивает сервер MSDTC. Если параметр не задан, служба MSDTC использует случайный временный порт при перезапуске службы и потребуется перенастроить исключения брандмауэра, чтобы служба MSDTC могла продолжить взаимодействие. |

Дополнительные сведения об этих параметрах и других параметрах, связанных с MSDTC, см. в статье [Настройка SQL Server на Linux с помощью средства mssql-conf](sql-server-linux-configure-mssql-conf.md).

## <a name="supported-msdtc-configurations"></a>Поддерживаемые конфигурации MSDTC

Поддерживаются следующие конфигурации MSDTC.

- Распределенные транзакции OLE-TX относительно SQL Server на базе Linux для поставщиков ODBC.

- Распределенные транзакции XA относительно SQL Server на базе Linux с использованием поставщиков ODBC и JDBC. Для транзакций XA, выполняемых с помощью поставщика ODBC, нужно использовать Microsoft ODBC Driver for SQL Server версии 17.3 или более поздней. Дополнительные сведения см. в статье [Основные сведения о транзакциях XA](../connect/jdbc/understanding-xa-transactions.md#configuration-instructions).

- Распределенные транзакции на связанном сервере.

## <a name="msdtc-configuration-steps"></a>Шаги настройки MSDTC

Настройка взаимодействия и функциональности MSDTC состоит из трех шагов. Если необходимые действия по настройке не выполнены, SQL Server не включит функции MSDTC.

- Настройте **network.rpcport** и **distributedtransaction.servertcpport** с помощью mssql-conf.
- Настройте брандмауэр, чтобы разрешить обмен данными через **distributedtransaction.servertcpport** и порт 135.
- Настройте маршрутизацию сервера Linux таким образом, чтобы RPC-взаимодействие через порт 135 перенаправлялось на **network.rpcport** SQL Server.

Более подробные сведения по каждому шагу приведены в следующих разделах.

## <a name="configure-rpc-and-msdtc-ports"></a>Настройка портов MSDTC и RPC

Сначала настройте **network.rpcport** и **distributedtransaction.servertcpport** с помощью mssql-conf. Этот шаг относится к SQL Server и является типичным для всех поддерживаемых дистрибутивов.

1. Используйте mssql-conf, чтобы задать значение **network.rpcport**. В следующем примере задается значение 13500.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport 13500
   ```

2. Задайте значение **distributedtransaction.servertcpport**. В следующем примере задается значение 51999.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport 51999
   ```

3. Перезапуск SQL Server.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="configure-the-firewall"></a>Настройка брандмауэра

В качестве второго шага настройте брандмауэр, чтобы разрешить обмен данными через **servertcpport** и порт 135.  Это позволяет процессу сопоставления конечных точек RPC и процессу MSDTC взаимодействовать во внешней среде с другими диспетчерами транзакций и координаторами. Фактические шаги будут зависеть от дистрибутива Linux и брандмауэра. 

В следующем примере показано, как создать эти правила в **Ubuntu**.

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

В следующем примере показано, как это можно сделать в **Red Hat Enterprise Linux (RHEL)** .

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

Перед настройкой маршрутизации портов в следующем разделе нужно настроить брандмауэр. В некоторых случаях обновление брандмауэра может очистить правила маршрутизации портов.

## <a name="configure-port-routing"></a>Настройка маршрутизации портов

Настройте таблицу маршрутизации сервера Linux таким образом, чтобы RPC-взаимодействие через порт 135 перенаправлялось на **network.rpcport** SQL Server. Механизм настройки перенаправления портов в разных дистрибутивах может отличаться. В следующих разделах приведены рекомендации для Ubuntu, SUS Enterprise Linux (SLES) и Red Hat Enterprise Linux (RHEL).

### <a name="port-routing-in-ubuntu-and-sles"></a>Маршрутизация портов в Ubuntu и SLES

Ubuntu и SLES не используют службу **firewalld**, поэтому правила **iptable** являются эффективным механизмом для обеспечения маршрутизации портов. Правила **iptable** могут не сохраняться во время перезагрузки, поэтому описание следующих команд также содержит инструкции по восстановлению правил после перезагрузки.

1. Создайте правила маршрутизации для порта 135. В следующем примере порт 135 направляется на порт RPC 13500, определенный в предыдущем разделе. Замените `<ipaddress>` IP-адресом вашего сервера.

   ```bash
   sudo iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   sudo iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   Параметр `--comment RpcEndPointMapper` в предыдущих командах помогает управлять этими правилами в последующих командах.

2. Просмотрите созданные правила маршрутизации с помощью следующей команды.

   ```bash
   sudo iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. Сохраните правила маршрутизации в файл на компьютере.

   ```bash
   sudo iptables-save > /etc/iptables.conf
   ```

4. Чтобы перезагрузить правила после перезагрузки, добавьте следующую команду в `/etc/rc.local` (для Ubuntu) или в `/etc/init.d/after.local` (для SLES).

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

   > [!NOTE]
   > Для изменения файлов **rc.local** или **after.local** нужны права суперпользователя (sudo).

Команды **iptables-save** и **iptables-restore** вместе с конфигурацией запуска `rc.local`/`after.local` предоставляют базовый механизм сохранения и восстановления записей iptables. В зависимости от дистрибутива Linux могут быть доступны расширенные или автоматизированные варианты. Например, в Ubuntu альтернативой является пакет **iptables-persistent** для обеспечения сохраняемости записей.

> [!IMPORTANT]
> При выполнении предыдущих действий предполагается использование фиксированного IP-адреса. Если IP-адрес для вашего экземпляра SQL Server изменяется (из-за ручного вмешательства или DHCP), нужно удалить и повторно создать правила маршрутизации, если они были созданы с помощью iptables. Если нужно повторно создать или удалить существующие правила маршрутизации, можно использовать следующую команду для удаления старых правил `RpcEndPointMapper`.
> 
> ```bash
> sudo iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

### <a name="port-routing-in-rhel"></a>Маршрутизация портов в RHEL

В дистрибутивах, использующих службу **firewalld**, например Red Hat Enterprise Linux, одну службу можно использовать как для открытия порта на сервере, так и для внутреннего перенаправления портов. Например, в Red Hat Enterprise Linux для создания сохраняемых правил перенаправления портов и управления ими нужно использовать службу **firewalld** (через служебную программу **firewall-cmd** с `-add-forward-port` или аналогичными параметрами), а не iptables.

```bash
sudo firewall-cmd --permanent --add-forward-port=port=135:proto=tcp:toport=13500
sudo firewall-cmd --reload
```

## <a name="verify"></a>Проверка

На этом этапе SQL Server должен иметь возможность участвовать в распределенных транзакциях. Чтобы убедиться, что SQL Server ожидает передачи данных, выполните команду **netstat** (если используется RHEL, вам может потребоваться сначала установить пакет **net-tools**).

```bash
sudo netstat -tulpn | grep sqlservr
```

Выходные данные должны иметь следующий вид.

```bash
tcp 0 0 0.0.0.0:1433 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 127.0.0.1:1434 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:13500 0.0.0.0:* LISTEN 13911/sqlservr
tcp 0 0 0.0.0.0:51999 0.0.0.0:* LISTEN 13911/sqlservr
tcp6 0 0 :::1433 :::* LISTEN 13911/sqlservr
tcp6 0 0 ::1:1434 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::13500 :::* LISTEN 13911/sqlservr
tcp6 0 0 :::51999 :::* LISTEN 13911/sqlservr
```

Однако после перезагрузки SQL Server не начинает прослушивание **servertcpport** до первой распределенной транзакции. В этом случае вы не увидите, как SQL Server прослушивает порт 51999 в этом примере, до первой распределенной транзакции.

## <a name="configure-authentication-on-rpc-communication-for-msdtc"></a>Настройка проверки подлинности при RPC-взаимодействии для MSDTC

По умолчанию MSDTC для SQL Server на Linux не использует проверку подлинности для RPC-взаимодействия. Однако если хост-компьютер присоединен к домену Active Directory (AD), можно настроить MSDTC для использования RPC-взаимодействия с проверкой подлинности, используя следующие параметры **mssql-conf**.

| Параметр | Description |
|---|---|
| **distributedtransaction.allowonlysecurerpccalls**          | Настройка только безопасных удаленных вызовов процедур (RPC) для распределенных транзакций. Значение по умолчанию — 0. |
| **distributedtransaction.fallbacktounsecurerpcifnecessary** | Настройка только безопасных удаленных вызовов процедур (RPC) для распределенных транзакций. Значение по умолчанию — 0. |
| **distributedtransaction.turnoffrpcsecurity**               | Включение или отключение безопасности RPC для распределенных транзакций. Значение по умолчанию — 0. |

## <a name="additional-guidance"></a>Дополнительные рекомендации

### <a name="active-directory"></a>Active Directory

Корпорация Майкрософт рекомендует использовать координатор распределенных транзакций с включенным RPC, если сервер SQL Server зарегистрирован в конфигурации Active Directory (AD). Если в SQL Server настроено использование проверки подлинности Active Directory, координатор распределенных транзакций по умолчанию использует защиту RPC с помощью взаимной проверки подлинности.

### <a name="windows-and-linux"></a>Windows и Linux

Если клиент с операционной системой Windows необходимо включить в распределенную транзакцию с SQL Server на Linux, он должен иметь следующую минимальную версию операционной системы Windows.

| Операционная система | Минимальная версия | Сборка ОС |
|---|---|---|
| [Windows Server](https://docs.microsoft.com/windows-server/get-started/windows-server-release-info) | 1903 | 18362.30.190401-1528 |
| [Windows 10](https://docs.microsoft.com/windows/release-information/) | 1903 | 18362.267 |

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения об SQL Server на Linux см. в статье [SQL Server на Linux](sql-server-linux-overview.md).
