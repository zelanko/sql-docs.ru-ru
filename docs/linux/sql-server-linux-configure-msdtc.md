---
title: Как настроить MSDTC на платформе Linux
description: В этой статье приведены пошаговые инструкции для настройки MSDTC на Linux.
author: VanMSFT
ms.author: vanto
ms.date: 03/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: c44458e1a68c842b6433d7a137865ae8451c136c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68077609"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Настройка координатора распределенных транзакций Microsoft (MSDTC) на платформе Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка координатора распределенных транзакций Microsoft (MSTDC) на платформе Linux. В предварительной версии SQL Server 2019 появилась поддержка MSDTC в Linux.

## <a name="overview"></a>Обзор

Распределенные транзакции на SQL Server в Linux включены путем введения MSDTC RPC endpoint mapper функциональные возможности и в SQL Server. По умолчанию процесс сопоставление конечных точек RPC прослушивает порт 135 для входящих запросов RPC и предоставляет сведения о зарегистрированных компонентов удаленные запросы. Удаленные запросы можно использовать сведения, возвращаемые функцией Сопоставитель конечных точек для взаимодействия с зарегистрированных компонентов RPC, такие как службы MSDTC. Процесс требует права суперпользователя для привязки к известных портов (номера портов ниже 1024) на платформе Linux. Чтобы избежать запуск SQL Server с правами привилегированного пользователя для процесса сопоставления конечной точки RPC, системным администраторам необходимо использовать iptables создать преобразование сетевых адресов для маршрутизации трафика через порт 135 для процесса сопоставление конечных точек RPC SQL Server.

SQL Server 2019 представлены два параметра конфигурации для mssql-conf служебной программы.

| параметр MSSQL-conf | Описание |
|---|---|
| **Network.rpcport** | Процесс RPC endpoint mapper связывает TCP-порта. |
| **distributedtransaction.servertcpport** | Порт, который прослушивает сервер MSDTC. Если не задано, служба MSDTC использует случайный эфемерный порт на перезапуска службы и исключения брандмауэра потребуется изменить конфигурацию, чтобы убедиться, что служба MSDTC может продолжать взаимодействие. |

Дополнительные сведения об этих параметрах и других параметров MSDTC см. в разделе [Настройка SQL Server в Linux с использованием средство mssql-conf](sql-server-linux-configure-mssql-conf.md#msdtc).

## <a name="supported-msdtc-configurations"></a>Поддерживаемые конфигурации MSDTC

Поддерживаются следующие конфигурации MSDTC.

- OLE-TX распределенных транзакций в SQL Server в Linux для поставщиков ODBC.
- XA распределенных транзакций в SQL Server в Linux с помощью JDBC и ODBC поставщиков. Транзакции XA, выполняемых с помощью поставщика ODBC необходимо использовать драйвер Microsoft ODBC для SQL Server версии 17.3 или более поздней версии.
- Распределенные транзакции на связанный сервер.

Ограничения и известные проблемы для MSDTC в предварительной версии, см. в разделе [заметки о выпуске для предварительной версии SQL Server 2019 в Linux](sql-server-linux-release-notes-2019.md#msdtc).

## <a name="msdtc-configuration-steps"></a>Действия по настройке MSDTC

Существует три действия для настройки обмена данными MSDTC и функциональные возможности. Если все необходимые шаги не выполняются, SQL Server не включит функциональности MSDTC.

- Настройка **network.rpcport** и **distributedtransaction.servertcpport** с помощью mssql-conf.
- Настройка брандмауэра, разрешающее соединение через **distributedtransaction.servertcpport** и порт 135.
- Настройка маршрутизации сервера Linux, таким образом, чтобы соединение RPC через порт 135 перенаправляется в SQL Server **network.rpcport**.

Следующие разделы содержат подробные инструкции для каждого шага.

## <a name="configure-rpc-and-msdtc-ports"></a>Настройка портов RPC и MSDTC

Во-первых, настройте **network.rpcport** и **distributedtransaction.servertcpport** с помощью mssql-conf. Этот шаг, если связанные с SQL Server и общими между всех поддерживаемых дистрибутивов.

1. Используйте mssql-conf, чтобы задать **network.rpcport** значение. В следующем примере его к 13500.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set network.rpcport 13500
   ```

2. Задайте **distributedtransaction.servertcpport** значение. В следующем примере его к 51999.

   ```bash
   sudo /opt/mssql/bin/mssql-conf set distributedtransaction.servertcpport 51999
   ```

3. Перезапуск SQL Server.

   ```bash
   sudo systemctl restart mssql-server
   ```

## <a name="configure-the-firewall"></a>Настройка брандмауэра

Второй шаг — Настройка брандмауэра, разрешающее соединение через **servertcpport** и порт 135.  Это обеспечивает сопоставление конечных точек RPC и процесса MSDTC для внешней связи с другими диспетчерами транзакций и координаторы. Фактические действия для этого зависит от дистрибутива Linux и брандмауэра. 

В следующем примере показано, как для создания этих правил на **Ubuntu**.

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

В следующем примере показано, как это можно сделать на **Red Hat Enterprise Linux (RHEL)** :

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

Важно настроить брандмауэр перед настройкой Маршрутизация порта в следующем разделе. Обновление брандмауэра можно очистить правила маршрутизации порта в некоторых случаях.

## <a name="configure-port-routing"></a>Настройка маршрутизации порта

Настроить таблицу маршрутизации сервера Linux таким образом, чтобы соединение RPC через порт 135 перенаправляется в SQL Server **network.rpcport**. Механизм настройки для перенаправления на другой дистрибутив портов могут отличаться. Следующие разделы содержат рекомендации по Ubuntu, SUS Enterprise Linux (SLES) и Red Hat Enterprise Linux (RHEL).

### <a name="port-routing-in-ubuntu-and-sles"></a>Порт маршрутизации в Ubuntu и SLES

Не используйте Ubuntu и SLES **firewalld** службы, поэтому **iptable** правила, эффективный механизм для достижения метрика маршрутизации. **Iptable** правила не может сохраняться во время перезагрузки, поэтому приведенные ниже команды также предоставляют инструкции по восстановлению правила после перезагрузки.

1. Создайте правила маршрутизации для порт 135. В следующем примере порт 135 направляется RPC-порт, 13500, определенный в предыдущем разделе. Замените `<ipaddress>` IP-адресом вашего сервера.

   ```bash
   sudo iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   sudo iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   `--comment RpcEndPointMapper` Параметр в предыдущих командах помогает в управлении эти правила в последующих командах.

2. Просмотрите правила маршрутизации, созданную с помощью следующей команды:

   ```bash
   sudo iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. Сохраните файл на компьютере правила маршрутизации.

   ```bash
   sudo iptables-save > /etc/iptables.conf
   ```

4. Чтобы перезагрузить правила после перезагрузки, добавьте следующую команду, чтобы `/etc/rc.local` (для Ubuntu) или `/etc/init.d/after.local` (для SLES):

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

   > [!NOTE]
   > Необходимо иметь права суперпользователя (sudo), чтобы изменить **rc.local** или **after.local** файлов.

**Сохранить iptables** и **iptables восстановления** команды, вместе с параметром `rc.local` / `after.local` конфигурации запуска предоставляют базовый механизм для сохранения и восстановления iptables операции. В зависимости от дистрибутива Linux может быть более сложные или автоматические параметры, доступные. Например, является альтернативой Ubuntu **постоянных iptables** пакета, чтобы сделать записи постоянного.

> [!IMPORTANT]
> В предыдущих шагах предполагается фиксированный IP-адрес. При изменении IP-адрес для экземпляра SQL Server (из-за вмешательства пользователя либо DHCP) необходимо удалить и повторно создать правила маршрутизации, если они были созданы с помощью iptables. Если вам нужно повторно создать или удалить существующие правила маршрутизации, можно использовать следующую команду для удаления старого `RpcEndPointMapper` правила:
> 
> ```bash
> sudo iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

### <a name="port-routing-in-rhel"></a>Порт, маршрутизации в RHEL

Для дистрибутивов, использующих **firewalld** службы, например Red Hat Enterprise Linux, той же службе может использоваться для обоих открытия порта на сервере и внутренний порт перенаправления. Например, в Red Hat Enterprise Linux, следует использовать **firewalld** службы (с помощью **брандмауэра cmd** служебную программу конфигурации с `-add-forward-port` или аналогичные параметры) для создания и управления постоянный порт Правила перенаправления вместо использования iptables.

```bash
sudo firewall-cmd --permanent --add-forward-port=port=135:proto=tcp:toport=13500
sudo firewall-cmd --reload
```

## <a name="verify"></a>Проверка

На этом этапе SQL Server должен иметь возможность участвовать в распределенных транзакциях. Чтобы проверить, что SQL Server прослушивает, запустите **netstat** команды (при использовании RHEL, может потребоваться сначала установить **net-tools** пакета):

```bash
sudo netstat -tulpn | grep sqlservr
```

Вы должны увидеть результат, аналогичный приведенному ниже:

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

Тем не менее, после перезагрузки SQL Server не начать прослушивание **servertcpport** до первого распределенную транзакцию. В этом случае не отображался SQL Server прослушивает порт 51999 в этом примере до первой распределенной транзакции.

## <a name="configure-authentication-on-rpc-communication-for-msdtc"></a>Настройка проверки подлинности на взаимодействие на основе RPC для службы MSDTC

MSDTC для SQL Server в Linux не использует проверку подлинности на взаимодействие на основе RPC по умолчанию. Тем не менее, когда хост-компьютер присоединен к домену Active Directory (AD), это можно настроить MSDTC для использования прошедшего проверку подлинности по протоколу RPC с использованием следующих **mssql-conf** параметры:

| Параметр | Описание |
|---|---|
| **distributedtransaction.allowonlysecurerpccalls**          | Настройте безопасные вызовы RPC только для распределенных транзакций. |
| **distributedtransaction.fallbacktounsecurerpcifnecessary** | Настройка безопасности, которые вызывает только RPC для распределенных транзакций. |
| **distributedtransaction.turnoffrpcsecurity**               | Включение или отключение безопасности RPC для распределенных транзакций. |

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server в Linux, см. в разделе [SQL Server в Linux](sql-server-linux-overview.md).
