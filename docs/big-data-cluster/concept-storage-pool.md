---
title: Что такое пул носителей?
titleSuffix: SQL Server big data clusters
description: Сведения о роли пула носителей SQL Server в кластере больших данных SQL Server 2019, а также архитектуре и функциональных возможностях пула носителей SQL.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 10/01/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 4d810220e0bd1148d4f572638c3ac67d4c3b44c0
ms.sourcegitcommit: ae474d21db4f724523e419622ce79f611e956a22
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/20/2020
ms.locfileid: "92257247"
---
# <a name="what-is-the-storage-pool-big-data-clusters-2019"></a>Что такое пул носителей ([!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)])?

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается роль *пула носителей SQL Server* в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (BDC). В следующих разделах содержатся сведения об архитектуре и функциональных возможностях пула носителей SQL.

## <a name="storage-pool-architecture"></a>Архитектура пула носителей

Пул носителей — это локальный кластер HDFS (Hadoop) в экосистеме SQL Server BDC. Он предоставляет постоянное хранилище для неструктурированных и частично структурированных данных. Файлы данных, такие как Parquet или текст с разделителями, могут храниться в пуле носителей. Для постоянного хранения к каждому pod в пуле прикреплен постоянный том. Доступ к файлам пула носителей осуществляется через [Polybase](../relational-databases/polybase/polybase-guide.md) посредством SQL Server или напрямую с помощью шлюза Apache Knox.

Классическая конфигурация HDFS состоит из набора обычных компьютеров с подключенным хранилищем. Данные распределяются по блокам на узлах, что приводит к отказоустойчивости и возможности использования параллельной обработки. Один из узлов в кластере выступает в качестве узла имен и содержит метаданные о файлах, расположенных в узлах данных.

![Классическая конфигурация HDFS](media/concept-storage-pool/classic-hdfs-setup.png)

Пул носителей состоит из узлов хранилища, которые являются членами кластера HDFS. Он выполняет один или несколько pod Kubernetes для каждого pod, в котором размещаются следующие контейнеры:

- Контейнер Hadoop, связанный с постоянным томом (хранилищем). Все контейнеры этого типа вместе образуют кластер Hadoop. В контейнере Hadoop находится процесс диспетчера узлов YARN, который может создавать рабочие процессы Apache Spark по требованию. На головном узле Spark размещаются контейнеры хранилища метаданных Hive, журнала Spark и журнала заданий YARN.
- Экземпляр SQL Server для чтения данных из HDFS с использованием технологии OpenRowSet.
- `collectd` для сбора данных метрик.
- `fluentbit` для сбора данных журналов.

![Архитектура пула носителей](media/concept-storage-pool/scale-big-data-on-demand.png)

## <a name="responsibilities"></a>Обязанности

Узлы хранилища предназначены для выполнения следующих задач:

- Прием данных через Apache Spark.
- Хранение данных в HDFS (Parquet и текстовый формат с разделителями). HDFS также обеспечивает сохраняемость данных, так как данные HDFS распределены по всем узлам хранения в BDC SQL.
- доступ к данным через конечные точки HDFS и SQL Server.

## <a name="accessing-data"></a>Доступ к данным

Ниже приведены основные методы доступа к данным в пуле носителей.

- Задания Spark.
- Использование внешних таблиц SQL Server для разрешения запросов данных с помощью вычислительных узлов PolyBase и экземпляров SQL Server, выполняющихся на узлах HDFS.

Взаимодействовать с HDFS можно также с помощью следующих средств.

- Azure Data Studio.
- [!INCLUDE [azure-data-cli-azdata](../includes/azure-data-cli-azdata.md)].
- kubectl для отправки команд в контейнер Hadoop.
- Шлюз HTTP HDFS.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] см. в следующих ресурсах.

- [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md)
- [Семинар. Архитектура [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] Майкрософт](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
