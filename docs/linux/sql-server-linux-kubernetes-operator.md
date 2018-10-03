---
title: SQL Server Always On доступности группы Kubernetes оператор глобальным требованиям
description: В этой статье описывается параметры для SQL Server Kubernetes Always On доступности группы оператор глобальным требованиям
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f8667c74843ab26b251c5a23a1e93f7f26e72fef
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47759362"
---
# <a name="sql-server-always-on-availability-group-kubernetes-operator-parameters"></a>SQL Server Always On доступности Kubernetes оператор параметры группы

Группы доступности AlwaysOn, в Kubernetes требуется оператор. Оператор описан в yaml-файл.  Пример спецификации в [учебником](tutorial-sql-server-ag-kubernetes.md).

В этой статье объясняется переменных глобальной среды оператор.

## <a name="example"></a>Пример

В следующем примере описывается развертывание для `mssql-operator`.

## <a name="global-environment-variables"></a>Глобальные переменные среды

* `MSSQL_K8S_POD_NAMESPACE` 
  * Обязательно
  * **Описание**: пространство имен Kubernetes от оператора.

* `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`
  * Необязательно
  * **Описание**: продолжительность внешних sql server запись аренды для поддержания sql server для записи и предотвратить разделенной сценариев. Вторичные реплики дождитесь этого срока действия, после выбора нового лидера.

* `MSSQL_K8S_MONITOR_PERIOD_SECONDS`
  * Необязательно
  * **Описание**: период для наблюдения, если состояние группы доступности. Определяет, насколько быстро реплики являются добавлены и удалены. Должно быть меньше, чем `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`.
  * **По умолчанию**: 1

* `MSSQL_K8S_LEASE_DURATION_SECONDS`
  * Необязательно
  * **Описание**: продолжительность аренды руководитель группы доступности. Определяет, как долго вторичные реплики ожидания повторного выбора, если произошел сбой первичной реплики. Это отличается от Аренда записи SQL Server. 
  * **По умолчанию**: 10
  
  >[!NOTE]
  >Другие параметры автоматически вычисляется на основе `MSSQL_K8S_LEASE_DURATION_SECONDS`.

* `MSSQL_K8S_RENEW_DEADLINE_SECONDS`
  * Необязательно
  * **Описание**: длительность первичной действующего повторных попыток обновления лидерство перед прекращением. Должно быть меньше, чем `MSSQL_K8S_LEASE_DURATION_SECONDS`.
  * **По умолчанию**:  `MSSQL_K8S_LEASE_DURATION_SECONDS` /2

* `MSSQL_K8S_RETRY_PERIOD_SECONDS`
  * Необязательно
  * **Описание**: длительность действующего [master](http://kubernetes.io/docs/concepts/architecture/master-node-communication/) ожидания, обновление аренды лидером. Должно быть меньше, чем `MSSQL_K8S_LEASE_DURATION_SECONDS`.
  * **По умолчанию**:  `MSSQL_K8S_RENEW_DEADLINE_SECONDS` /2

* `MSSQL_K8S_ACQUIRE_PERIOD_SECONDS` 
  * Необязательно
  * **Описание**: период, вторичные реплики опроса, если истек срок действия аренды лидером. 
  * **По умолчанию**: 1


  ## <a name="next-steps"></a>Следующие шаги

[Группы доступности SQL Server в кластере Kubernetes](sql-server-ag-kubernetes.md)
