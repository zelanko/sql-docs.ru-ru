---
title: Заметки о выпуске кластеров больших данных SQL Server
titleSuffix: SQL Server big data clusters
description: В этой статье описаны последние обновления и известные проблемы для Кластеров больших данных SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 02/13/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 9de368594383ef1f7fe3ae3c062f92873fb15698
ms.sourcegitcommit: 49082f9b6b3bc8aaf9ea3f8557f40c9f1b6f3b0b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2020
ms.locfileid: "77256907"
---
# <a name="sql-server-2019-big-data-clusters-release-notes"></a>Заметки о выпуске Кластеров больших данных SQL Server 2019

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Следующие заметки о выпуске применимы к [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]. Эта статья разбита на разделы для каждого выпуска. Каждый выпуск содержит ссылку на статью поддержки, где описаны изменения накопительного пакета обновления, а также ссылки на скачиваемые файлы пакета Linux. В этой статье также перечислены [известные проблемы](#known-issues) для последних выпусков [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC).

## <a name="supported-platforms"></a>Поддерживаемые платформы

В этом разделе описываются платформы, поддерживаемые [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC).

### <a name="kubernetes-platforms"></a>Платформы Kubernetes

|Платформа|Поддерживаемые версии|
|---------|---------|
|Kubernetes|Для BDC требуется версия Kubernetes не ниже 1.13. См. раздел [Версия Kubernetes и политика поддержки отклонения версий](https://kubernetes.io/docs/setup/release/version-skew-policy/) для получения информации о политике поддержки версий Kubernetes.|
|Служба Azure Kubernetes (AKS)|Для BDC требуется версия AKS не ниже 1.13.<br/>См. информацию о политике поддержки версий в разделе [Поддерживаемые версии Kubernetes в AKS](/azure/aks/supported-kubernetes-versions).|

### <a name="host-os-for-kubernetes"></a>Операционная система узла для Kubernetes

|Платформа|Поддерживаемые версии|
|---------|---------|
|Red Hat Enterprise Linux|7.3, 7.4, 7.5, 7.6|
|Ubuntu|16.04|

### <a name="sql-server-editions"></a>Выпуски SQL Server

|Выпуск|Примечания|
|---------|---------|
|Enterprise<br/>Standard<br/>Разработчик| Выпуск кластера больших данных определяется выпуском основного экземпляра SQL Server. Во время развертывания выпуск Developer развертывается по умолчанию. После развертывания выпуск можно изменить. См. [Настройка основного экземпляра SQL Server](../big-data-cluster/configure-sql-server-master-instance.md). |

## <a name="tools"></a>Инструменты

|Платформа|Поддерживаемые версии|
|---------|---------|
|`azdata`|Должна быть такая же дополнительная версия, что и у сервера (тот же основной экземпляр SQL Server).<br/><br/>Запустите `azdata –-version`, чтобы проверить версию.<br/><br/>Начиная с SQL Server 2019 CU2 используется версия `15.0.4013`.|
|Azure Data Studio|Получите последнюю сборку [Azure Data Studio](https://aka.ms/getazuredatastudio).|

## <a name="release-history"></a>История выпусков

В следующей таблице указана история выпусков для [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].

| Release               | Версия       | Дата выпуска |
|-----------------------|---------------|--------------|
| [CU2](#cu2)           | 15.0.4013.40    | 2020-02-13   |
| [CU1](#cu1)           | 15.0.4003.23   | 2020-01-07   |
| [GDR1](#rtm)            | 15.0.2070.34  | 2019-11-04   |

## <a name="how-to-install-updates"></a>Установка обновлений

Сведения об установке обновлений см. в статье [Обновление [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](deployment-upgrade.md).

## <a id="cu2"></a> CU2 (февраль 2020 г.)

Выпуск накопительного пакета обновления 2 (CU2) для SQL Server 2019. Версия ядра СУБД SQL Server в этом выпуске — 15.0.4003.23.

|Версия пакета | Тег образа |
|-----|-----|
|15.0.4013.40 |[2019-CU2-ubuntu-16.04]

## <a id="cu1"></a> CU1 (январь 2020 г.)

Выпуск накопительного пакета обновления 1 (CU1) для SQL Server 2019. Версия ядра СУБД SQL Server в этом выпуске — 15.0.4003.23.

|Версия пакета | Тег образа |
|-----|-----|
|15.0.4003.23|[2019-CU1-ubuntu-16.04]

## <a id="rtm"></a> GDR1 (ноябрь 2019 г.)

Выпуск SQL Server 2019 для общего распространения 1 (GDR1) — общедоступная версия [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-nover.md)]. Версия ядра СУБД SQL Server в этом выпуске — 15.0.2070.34.

|Версия пакета | Тег образа |
|-----|-----|
|15.0.2070.34|[2019-GDR1-ubuntu-16.04]

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="known-issues"></a>Известные проблемы

### <a name="deployment-with-private-repository"></a>Развертывание в частном репозитории

- **Проблема и последствия для клиентов**: К обновлению из частного репозитория предъявляются особые требования.

- **Возможное решение**: Если вы используете частный репозиторий, чтобы предварительно извлечь образы для развертывания или обновления BDC, убедитесь, что текущие образы сборки, а также образы целевой сборки находятся в частном репозитории. Так вы сможете при необходимости успешно выполнить откат. Кроме того, если вы изменили учетные данные частного репозитория с момента первоначального развертывания, обновите соответствующий секрет в Kubernetes, прежде чем выполнять обновление. `azdata` не поддерживает обновление учетных данных с помощью переменных среды `AZDATA_PASSWORD` и `AZDATA_USERNAME`. Создайте секрет с помощью [`kubectl edit secrets`](https://kubernetes.io/docs/concepts/configuration/secret/#editing-a-secret). 

Обновление с использованием других репозиториев не поддерживается для текущих и целевых сборок.

### <a name="upgrade-may-fail-due-to-timeout"></a>Сбой обновления из-за истечения времени ожидания

- **Проблема и последствия для клиентов**: Обновление может завершиться ошибкой из-за истечения времени ожидания.

   В приведенном ниже коде показано, как может выглядеть ошибка:

   ```
   >azdata.EXE bdc upgrade --name <mssql-cluster>
   Upgrading cluster to version 15.0.4003

   NOTE: Cluster upgrade can take a significant amount of time depending on
   configuration, network speed, and the number of nodes in the cluster.

   Upgrading Control Plane.
   Control plane upgrade failed. Failed to upgrade controller.
   ```

   Эта ошибка чаще всего возникает при обновлении BDC в Службе Kubernetes Azure (AKS).

- **Возможное решение**: Увеличьте время ожидания для обновления. 

   Чтобы увеличить время ожидания для обновления, измените схему конфигурации обновления. Чтобы изменить схему конфигурации обновления, выполните следующие действия:

   1. Выполните следующую команду:

      ```bash
      kubectl edit configmap controller-upgrade-configmap
      ```

   2.   Измените следующие поля:

       **`controllerUpgradeTimeoutInMinutes`**  — указывает количество минут ожидания завершения обновления базы данных контроллера или контроллера. Значение по умолчанию — 5. Используйте значение не ниже 20.

       **`totalUpgradeTimeoutInMinutes`** : Определяет совокупный интервал времени, в течение которого контроллер и база данных контроллера должны завершить обновление (обновление контроллера и базы данных контроллера). Значение по умолчанию — 10. Используйте значение не ниже 40.

       **`componentUpgradeTimeoutInMinutes`** : Определяет время, необходимое для выполнения каждого следующего этапа обновления.  Значение по умолчанию — 30. Замените на 45.

   3.   Сохраните и закройте.

   Ниже приведен скрипт Python для установки времени ожидания.

   ```python
   from kubernetes import client, config
   import json

   def set_upgrade_timeouts(namespace, controller_timeout=20, controller_total_timeout=40, component_timeout=45):
       """ Set the timeouts for upgrades

       The timeout settings are as follows

       controllerUpgradeTimeoutInMinutes: sets the max amount of time for the controller
           or controllerdb to finish upgrading

       totalUpgradeTimeoutInMinutes: sets the max amount of time to wait for both the
           controller and controllerdb to complete their upgrade

       componentUpgradeTimeoutInMinutes: sets the max amount of time allowed for
           subsequent phases of the upgrade to complete
       """
       config.load_kube_config()

       upgrade_config_map = client.CoreV1Api().read_namespaced_config_map("controller-upgrade-configmap", namespace)

       upgrade_config = json.loads(upgrade_config_map.data["controller-upgrade"])

       upgrade_config["controllerUpgradeTimeoutInMinutes"] = controller_timeout

       upgrade_config["totalUpgradeTimeoutInMinutes"] = controller_total_timeout

       upgrade_config["componentUpgradeTimeoutInMinutes"] = component_timeout

       upgrade_config_map.data["controller-upgrade"] = json.dumps(upgrade_config)

       client.CoreV1Api().patch_namespaced_config_map("controller-upgrade-configmap", namespace, upgrade_config_map)
   ```

### <a name="livy-job-submission-from-azure-data-studio-ads-or-curl-fail-with-500-error"></a>Сбой отправки задания Livy из Azure Data Studio (ADS) или выполнения команды curl с ошибкой 500

- **Проблема и последствия для клиентов**: В конфигурации высокой доступности общие ресурсы Spark `sparkhead` настраиваются с несколькими репликами. В этом случае могут возникать сбои при отправке задания Livy из Azure Data Studio (ADS) или `curl`. Для проверки выполните команду `curl` в отношении любых результатов `sparkhead` pod в отклоненном подключении. Так, `curl https://sparkhead-0:8998/` или `curl https://sparkhead-1:8998` возвращает ошибку 500.

   Это происходит в следующих случаях:

   - Группы pod Zookeeper или процессы для каждого экземпляра Zookeeper несколько раз перезапускаются.
   - Между pod `sparkhead` и группами pod Zookeeper нестабильное сетевое подключение.

- **Возможное решение**: Перезапуск обоих серверов Livy.

   ```bash
   kubectl -n <clustername> exec sparkhead-0 -c hadoop-livy-sparkhistory supervisorctl restart livy
   ```

   ```bash
   kubectl -n <clustername> exec sparkhead-1 -c hadoop-livy-sparkhistory supervisorctl restart livy
   ```

### <a name="create-memory-optimized-table-when-master-instance-in-an-availability-group"></a>Создание оптимизированной для обработки в памяти таблицы, когда основной экземпляр находится в группе доступности

- **Проблема и последствия для клиентов**: Невозможно использовать основную конечную точку, предоставленную для подключения к базам данных группы доступности (прослушивателю), для создания оптимизированных для обработки в памяти таблиц.

- **Возможное решение**: Чтобы создать оптимизированные для обработки в памяти таблицы, когда основной экземпляр SQL Server находится в конфигурации группы доступности, [подключитесь к экземпляру SQL Server](deployment-high-availability.md#instance-connect), предоставьте конечную точку, подключитесь к базе данных SQL Server и создайте оптимизированные для обработки в памяти таблицы в сеансе, созданном с новым подключением.

### <a name="insert-to-external-tables-active-directory-authentication-mode"></a>Укажите для внешних таблиц режим проверки подлинности с Active Directory

- **Проблема и последствия для клиентов**: Если основной экземпляр SQL Server находится в режиме проверки подлинности с Active Directory, запрос, который выбирает элемент исключительно из внешних таблиц, где хотя бы одна из внешних таблиц находится в пуле носителей, и вставляет режим проверки подлинности в другую внешнюю таблицу, возвращает следующее:

   ```
   Msg 7320, Level 16, State 102, Line 1
   Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "SQLNCLI11". Only domain logins can be used to query Kerberized storage pool.
   ```

- **Возможное решение**: Измените запрос одним из следующих способов. Присоедините таблицу пулов носителей к локальной таблице или сначала вставьте ее в локальную таблицу, а затем выполните чтение из локальной таблицы, чтобы вставить элемент в пул данных.

### <a name="transparent-data-encryption-capabilities-can-not-be-used-with-databases-that-are-part-of-the-availability-group-in-the-sql-server-master-instance"></a>Функции прозрачного шифрования данных нельзя использовать с базами данных, которые являются частью группы доступности в главном экземпляре SQL Server.

- **Проблема и последствия для клиентов**: В конфигурации высокой доступности базы данных с включенным шифрованием нельзя использовать после отработки отказа, так как главный ключ, используемый для шифрования, отличается для каждой реплики. 

- **Возможное решение**: Решение для этой проблемы отсутствует. Рекомендуется не включать шифрование в этой конфигурации, пока не выйдет исправление.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md).
