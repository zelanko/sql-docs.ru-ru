---
title: Как использовать распределенные транзакции с SQL Server в Docker | Документация Майкрософт
description: В этой статье описываются способы использования Dprovides пошаговые инструкции по настройке MSDTC на платформе Linux.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 09/24/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>= sql-server-ver15 || = sqlallproducts-allversions'
ms.openlocfilehash: 3242f0d074dc3c2f33fc83de4604a20bfdcbd64a
ms.sourcegitcommit: df21af652d0906ade8cc9ca3985a7ba5569f0db6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2018
ms.locfileid: "47049414"
---
# <a name="how-to-use-distributed-transactions-with-sql-server-on-docker"></a>Как использовать распределенные транзакции с SQL Server в Docker

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

В этой статье объясняется, как настроить SQL Server в Docker для распределенных транзакций.

Начиная с предварительной версией SQL Server 2019, образы контейнеров поддерживает Microsoft координатор распределенных транзакций (MSDTC) требуется для распределенных транзакций. Чтобы узнать требования связи для службы MSDTC, см. в разделе [Настройка координатора распределенных транзакций Microsoft (MSDTC) на платформе Linux](sql-server-linux-configure-msdtc.md). В этой статье объясняется, особые требования и сценарии, связанные с контейнерами SQL Server Docker.

## <a name="configuration"></a>Конфигурация

Чтобы включить транзакции MSDTC в контейнерах для docker, необходимо задать две новые переменные среды:

- **MSSQL_RPC_PORT**: выполняет привязку к службе сопоставителя конечных точек RPC и будет прослушивать TCP-порта.  
- **MSSQL_DTC_TCP_PORT** порт что служба MSDTC настроена на прослушивание.

### <a name="pull-and-run"></a>Извлечение и запуск

Приведенный ниже показано, как использовать эти переменные среды для извлечения и запуска контейнера, настроенный для MSDTC. Это позволяет взаимодействовать с любым приложением, на все узлы.

```bash
docker run \
   -e 'ACCEPT_EULA=Y' -e 'MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>' \
   -e 'MSSQL_RPC_PORT=13500' -e 'MSSQL_DTC_TCP_PORT=51000' \
   -p 51433:1433 -p 13500:13500 -p 51000:51000  \
   -d mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu
```

Следующая команда отображает ту же команду для Docker в Windows в PowerShell:

```PowerShell
docker run `
   -e "ACCEPT_EULA=Y" -e "MSSQL_SA_PASSWORD=<YourStrong!Passw0rd>" `
   -e "MSSQL_RPC_PORT=13500" -e "MSSQL_DTC_TCP_PORT=51000" `
   -p 51433:1433 -p 13500:13500 -p 51000:51000 `
   -d "mcr.microsoft.com/mssql/server:vNext-CTP2.0-ubuntu"
```

В этой команде **RPC Endpoint Mapper** службы привязан к порту 13500 и **MSDTC** службы привязан к порту 51000 в пределах виртуальной сети docker. SQL Server TDS обмен данными происходит через порт 1433 в пределах виртуальной сети docker. Эти порты доступны извне к узлу в качестве TDS 51433, RPC endpoint mapper 13500, порта и порта для MSDTC 51000.

> [!NOTE]
> Сопоставитель конечных точек RPC и порта для MSDTC не совпадали на узле и в контейнере. Поэтому хотя Сопоставитель конечных точек RPC-порт был настроен для 13500 на контейнер, он потенциально могут быть сопоставлены со порта 13501 или любой другой доступный порт на сервере узла.

## <a name="configure-the-firewall"></a>Настройка брандмауэра

Для связи с и через узел, необходимо также настроить брандмауэр на сервере узла для контейнеров. Откройте порты брандмауэра для всех docker контейнер предоставляет для внешней связи. В предыдущем примере это будет порты 135, 51433 и 51000. Ниже приведены порты, на самом узле и не портов, которыми они сопоставляются в контейнере. Таким образом Если затем порта конечной точки RPC порт для переназначения 51000 контейнера был сопоставлен с портом узла 51001, 51001 (не 51000) должен быть открыт в брандмауэре для связи с узлом.  

В следующем примере показано, как для создания этих правил в Ubuntu.

```bash
sudo ufw allow from any to any port 51433 proto tcp
sudo ufw allow from any to any port 51000 proto tcp
sudo ufw allow from any to any port 135 proto tcp
```

В следующем примере показано, как это можно сделать на Red Hat Enterprise Linux (RHEL):

```bash
sudo firewall-cmd --zone=public --add-port=51999/tcp --permanent
sudo firewall-cmd --zone=public --add-port=51433/tcp --permanent
sudo firewall-cmd --zone=public --add-port=135/tcp --permanent
sudo firewall-cmd --reload
```

## <a name="configure-port-routing-on-the-host"></a>Настройка маршрутизации порт на узле

Если контейнер docker входит в распределенные транзакции с сервером, внешним по отношению к узел, затем узел необходимо настроить порт маршрутизации. Дополнительные сведения см. в разделе [Настройка маршрутизации порта](sql-server-linux-configure-msdtc.md#configure-port-routing).

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о MSDTC в Linux, см. в разделе [Настройка координатора распределенных транзакций Microsoft (MSDTC) на платформе Linux](sql-server-linux-configure-msdtc.md).