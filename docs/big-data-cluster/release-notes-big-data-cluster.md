---
title: Заметки о выпуске кластеров больших данных SQL Server
titleSuffix: SQL Server big data clusters
description: В этой статье описаны последние обновления и известные проблемы для Кластеров больших данных SQL Server.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bc5928a7e3015545d36900b52ef01a42d9694cc0
ms.sourcegitcommit: b4ad3182aa99f9cbfd15f4c3f910317d6128a2e5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73706167"
---
# <a name="sql-server-big-data-clusters-release-notes"></a>Заметки о выпуске кластеров больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Вы можете получать ценную информацию практически в реальном времени из всех данных с помощью [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)], которые обеспечивают полномасштабную среду для работы с большими наборами данных, в том числе с использованием машинного обучения и возможностей искусственного интеллекта.

В этой статье перечислены обновления и известные проблемы для последних выпусков [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] (BDC).

## <a id="rtm"></a> SQL Server 2019

В [!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] впервые представлены кластеры больших данных SQL Server.

Используйте кластеры больших данных SQL Server для решения следующих задач:

- [Развертывание масштабируемых кластеров](../big-data-cluster/deploy-get-started.md) SQL Server, Spark и контейнеров HDFS, выполняемых в Kubernetes. 
- Чтение, запись и обработка больших данных из Transact-SQL или Spark.
- Простое объединение и анализ ценных реляционных данных и больших данных крупного объема.
- Запрос внешних источников данных.
- Хранение больших данных в HDFS под управлением SQL Server.
- Запрос данных из нескольких внешних источников данных через кластер.
- Использование данных для искусственного интеллекта, машинного обучения и других задач анализа.
- [Развертывание и запуск приложений](../big-data-cluster/concept-application-deployment.md) в [!INCLUDE[big-data-clusters](../includes/ssbigdataclusters-nover.md)].
- Виртуализация данных с помощью [Polybase](../relational-databases/polybase/polybase-guide.md). Теперь вы можете запрашивать данные из внешних источников SQL Server, Oracle, Teradata, MongoDB и источников данных ODBC с внешними таблицами.
- Обеспечение высокой доступности для основного экземпляра SQL Server и всех баз данных с использованием технологии групп доступности Always On.

## <a name="sql-server-version"></a>Версия SQL Server

Текущая версия SQL Server — `15.0.2070.34`.

## <a name="image-tags"></a>Теги образов

Тег образа для этого выпуска — `2019-GDR1-ubuntu-16.04`.

[!INCLUDE [sql-server-servicing-updates-version-15](../includes/sql-server-servicing-updates-version-15.md)]

## <a name="supportability"></a>Поддержка

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

### <a name="tools"></a>Инструменты

|Платформа|Поддерживаемые версии|
|---------|---------|
|`azdata`|Должна быть такая же дополнительная версия, что и у сервера (тот же основной экземпляр SQL Server).<br/>Запустите `azdata –-version`, чтобы проверить версию. В настоящее время используется версия `15.0.2070`.|
|Azure Data Studio|Получите последнюю сборку [Azure Data Studio](https://aka.ms/getazuredatastudio).|

### <a name="sql-server-editions"></a>Выпуски SQL Server

|Выпуск|Примечания|
|---------|---------|
|Enterprise<br/>Standard<br/>Разработчик| Выпуск кластера больших данных определяется выпуском основного экземпляра SQL Server. Во время развертывания выпуск Developer развертывается по умолчанию. После развертывания выпуск можно изменить. См. [Настройка основного экземпляра SQL Server](../big-data-cluster/configure-sql-server-master-instance.md). |

## <a name="known-issues"></a>Известные проблемы

### <a name="livy-job-submission-from-azure-data-studio-ads-or-curl-fail-with-500-error"></a>Сбой отправки задания Livy из Azure Data Studio (ADS) или выполнения команды curl с ошибкой 500

**Проблема и последствия для клиентов**: В конфигурации высокой доступности общие ресурсы Spark (sparkhead) настраиваются с несколькими репликами. В этом случае могут возникать сбои при отправке задания Livy из Azure Data Studio (ADS) или `curl`. Для проверки выполните команду `curl` в отношении любых результатов sparkhead pod в отклоненном подключении. Так, `curl https://sparkhead-0:8998/` или `curl https://sparkhead-1:8998` возвращает ошибку 500.

Это происходит в следующих случаях:

- Группы pod Zookeeper или процессы для каждого экземпляра Zookeeper несколько раз перезапускаются.
- Между pod Sparkhead и группами pod Zookeeper нестабильное сетевое подключение.

**Обходной путь**: Перезапуск обоих серверов Livy.

```bash
kubectl -n <clustername> exec sparkhead-0 -c hadoop-livy-sparkhistory supervisorctl restart livy
```

```bash
kubectl -n <clustername> exec sparkhead-1 -c hadoop-livy-sparkhistory supervisorctl restart livy
```

### <a name="create-memory-optimized-table-when-master-instance-in-an-availability-group"></a>Создание оптимизированной для обработки в памяти таблицы, когда основной экземпляр находится в группе доступности

- **Проблема и последствия для клиентов**: Невозможно использовать основную конечную точку, предоставленную для подключения к базам данных группы доступности (прослушивателю), для создания оптимизированных для обработки в памяти таблиц.

- **Обходной путь**: Чтобы создать оптимизированные для обработки в памяти таблицы, когда основной экземпляр SQL Server находится в конфигурации группы доступности, [подключитесь к экземпляру SQL Server](deployment-high-availability.md#instance-connect), предоставьте конечную точку, подключитесь к базе данных SQL Server и создайте оптимизированные для обработки в памяти таблицы в сеансе, созданном с новым подключением.

### <a name="insert-to-external-tables-active-directory-authentication-mode"></a>Укажите для внешних таблиц режим проверки подлинности с Active Directory

- **Проблема и последствия для клиентов**: Если основной экземпляр SQL Server находится в режиме проверки подлинности с Active Directory, запрос, который выбирает элемент исключительно из внешних таблиц, где хотя бы одна из внешних таблиц находится в пуле носителей, и вставляет режим проверки подлинности в другую внешнюю таблицу, возвращает следующее:

   ```
   Msg 7320, Level 16, State 102, Line 1
   Cannot execute the query "Remote Query" against OLE DB provider "SQLNCLI11" for linked server "SQLNCLI11". Only domain logins can be used to query Kerberized storage pool.
   ```

- **Обходной путь**: Измените запрос одним из следующих способов. Присоедините таблицу пулов носителей к локальной таблице или сначала вставьте ее в локальную таблицу, а затем выполните чтение из локальной таблицы, чтобы вставить элемент в пул данных.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]](big-data-cluster-overview.md).
