---
title: Как настроить MSDTC на платформе Linux | Документация Майкрософт
description: В этой статье приведены пошаговые инструкции для настройки MSDTC на Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: a06dfa03442cfbcff2f8815f9c946afbd9ff771c
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269677"
---
# <a name="how-to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-on-linux"></a>Настройка координатора распределенных транзакций Microsoft (MSDTC) на платформе Linux

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье описывается настройка координатора распределенных транзакций Microsoft (MSTDC) на платформе Linux. В предварительной версии SQL Server 2019 появилась поддержка MSDTC в Linux.

## <a name="overview"></a>Обзор

Распределенные транзакции на SQL Server в Linux включены путем введения MSDTC RPC endpoint mapper функциональные возможности и в SQL Server. По умолчанию процесс сопоставление конечных точек RPC прослушивает порт 135 для входящих запросов RPC и перенаправляет, соответствующие компоненты (например, служба MSDTC). Процесс требует привилегий суперпользователя для привязки к известных портов (номера портов ниже 1024) на платформе Linux. Во избежание запуск SQL Server с правами привилегированного пользователя для процесса сопоставления конечной точки RPC, системные администраторы должны использовать iptables для создания преобразования NAT для маршрутизации трафика через порт 135 для процесса сопоставление конечных точек RPC SQL Server.

SQL Server 2019 представлены два параметра конфигурации для mssql-conf служебной программы.

| параметр MSSQL-conf | Описание |
|---|---|
| **Network.rpcport** | Процесс RPC endpoint mapper связывает TCP-порта. |
| **Network.servertcpport** | Порт, который прослушивает сервер MSDTC. Если не задано, служба MSDTC использует случайный эфемерный порт на перезапуска службы и исключения брандмауэра, необходимо будет повторно настроить, чтобы убедиться, что служба MSDTC может продолжать взаимодействие. |

Дополнительные сведения об этих параметрах и других параметров MSDTC см. в разделе [Настройка SQL Server в Linux с использованием средство mssql-conf](sql-server-linux-configure-mssql-conf.md#msdtc).

## <a name="supported-msdtc-configurations"></a>Поддерживаемые конфигурации MSDTC

Поддерживаются следующие конфигурации MSDTC.

- OLE-TX распределенных транзакций в SQL Server в Linux для поставщиков JDBC и ODBC.
- XA распределенных транзакций в SQL Server в Linux с помощью поставщиков JDBC.
- Распределенные транзакции на связанный сервер.

Ограничения и известные проблемы для MSDTC в предварительной версии, см. в разделе [заметки о выпуске для предварительной версии SQL Server 2019 в Linux](sql-server-linux-release-notes-2019.md#msdtc).

## <a name="msdtc-configuration-steps"></a>Действия по настройке MSDTC

Существует три действия для настройки обмена данными MSDTC и функциональные возможности. Если все необходимые шаги не выполняются, SQL Server не включит функциональности MSDTC.

- Настройка **network.rpcport** и **distributedtransaction.servertcpport** с помощью mssql-conf.
- Настройка брандмауэра, разрешающее соединение через **rpcport**, **servertcpport**и порт 135.
- Настройка маршрутизации сервера Linux, таким образом, чтобы соединение RPC через порт 135 перенаправляется в SQL Server **network.rpcport**.

Следующие разделы содержат подробные инструкции для каждого шага.

## <a name="configure-rpc-and-msdtc-ports"></a>Настройка портов RPC и MSDTC

Во-первых, настройте **network.rpcport** и **distributedtransaction.servertcpport** с помощью mssql-conf.

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

Последним шагом является настройка брандмауэра, разрешающее соединение через **rpcport**, **servertcpport**и порт 135.  Это обеспечивает сопоставление конечных точек RPC и процесса MSDTC для внешней связи с другими диспетчерами транзакций и координаторы. Фактические действия для этого зависит от дистрибутива Linux и брандмауэра. 

В следующем примере показано, как для создания этих правил в Ubuntu.

```bash
sudo ufw allow from any to any port 51999 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

В следующем примере показано, как это можно сделать на Red Hat Enterprise Linux (RHEL):

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

Важно настроить брандмауэр перед настройкой Маршрутизация порта в следующем разделе. Обновление брандмауэра можно очистить правила маршрутизации порта в некоторых случаях.

## <a name="configure-port-routing"></a>Настройка маршрутизации порта

Настроить таблицу маршрутизации сервера Linux таким образом, чтобы соединение RPC через порт 135 перенаправляется в SQL Server **network.rpcport**. С помощью правил iptable не может сохраняться во время перезагрузки, поэтому приведенные ниже команды также предоставляют инструкции по восстановлению правила после перезагрузки.

1. Создайте правила маршрутизации для порт 135. В следующем примере порт 135 направляется RPC-порт, 13500, определенный в предыдущем разделе. Замените `<ipaddress>` IP-адресом вашего сервера.

   ```bash
   iptables -t nat -A PREROUTING -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL  \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   iptables -t nat -A OUTPUT -d <ip> -p tcp --dport 135 -m addrtype --dst-type LOCAL \
      -j DNAT --to-destination <ip>:13500 -m comment --comment RpcEndPointMapper
   ```

   `--comment RpcEndPointMapper` Параметр в предыдущих командах помогает в управлении эти правила в последующих командах.

2. Просмотрите правила маршрутизации, созданную с помощью следующей команды:

   ```bash
   iptables -S -t nat | grep "RpcEndPointMapper"
   ```

3. Сохраните файл на компьютере правила маршрутизации.

   ```bash
   iptables-save > /etc/iptables.conf
   ```

4. Чтобы перезагрузить правила после перезагрузки, добавьте следующую команду, чтобы `/etc/rc.local` (для Ubuntu или RHEL) или `/etc/init.d/after.local` (для SLES):

   ```bash
   iptables-restore < /etc/iptables.conf
   ```

**Сохранить iptables** и **iptables восстановления** команды предоставляют базовый механизм для сохранения и восстановления записи iptables. В зависимости от дистрибутива Linux может быть более сложные или автоматические параметры, доступные. Например, является альтернативой Ubuntu **постоянных iptables** пакета, чтобы сделать записи постоянного. Или для Red Hat Enterprise Linux, можно использовать службу firewalld (с помощью служебной программы конфигурации брандмауэра cmd вместе с параметром – добавить-вперед-порт или аналогичные параметры) для создания постоянного правила вместо использования iptables перенаправления портов.

> [!IMPORTANT]
> В предыдущих шагах предполагается фиксированный IP-адрес. При изменении IP-адрес для экземпляра SQL Server (из-за вмешательства пользователя либо DHCP) необходимо удалить и повторно создать правила маршрутизации. Если вам нужно повторно создать или удалить существующие правила маршрутизации, можно использовать следующую команду для удаления старого `RpcEndPointMapper` правила:
> 
> ```bash
> iptables -S -t nat | grep "RpcEndPointMapper" | sed 's/^-A //' | while read rule; do iptables -t nat -D $rule; done
> ```

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

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о SQL Server в Linux, см. в разделе [SQL Server в Linux](sql-server-linux-overview.md).
