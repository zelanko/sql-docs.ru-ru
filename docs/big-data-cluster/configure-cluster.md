---
title: Настройка кластера
titleSuffix: Configure a SQL Server big data cluster
description: Общие сведения о настройке кластера больших данных SQL Server
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: rahul.ajmera
ms.date: 08/04/2020
ms.topic: overview
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b75f6946af9a13d6a8202c627d4c24a2225a51c1
ms.sourcegitcommit: 4545b502e3cae7136411fd9a7c15450315665f38
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/12/2020
ms.locfileid: "94549996"
---
# <a name="configure-a-sql-server-big-data-cluster"></a>Настройка кластера больших данных SQL Server

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Во время развертывания в кластере больших данных SQL Server 2019 можно настроить свойства главного экземпляра SQL Server, Apache Spark и Apache Hadoop.

Кластеры больших данных не поддерживают изменение свойств конфигурации после развертывания.

## <a name="configuration-scopes"></a>Области конфигурации
Конфигурация Кластеров больших данных включает два уровня: `service` и `resource`. Иерархия параметров также следует этому порядку — от высшего к низшему. Компоненты Кластеров больших данных принимают значение параметра, определенное на самом низком уровне. Если параметр не определен в заданной области, он наследует значение из более высокой родительской области.

Например, вы можете определить число ядер по умолчанию для использования драйвером Spark в области `resources` пула носителей и Sparkhead. Это можно сделать двумя способами. 
- Задайте число ядер по умолчанию в области службы `Spark`.  
- Задайте число ядер по умолчанию в области ресурсов `storage-0` и `sparkhead`.

В первом сценарии все ресурсы низшей области службы Spark (пул носителей и Sparkhead) *наследуют* число ядер по умолчанию из значения службы Spark по умолчанию.

Во втором сценарии каждый ресурс будет использовать значение, определенное в соответствующей области.

Если число ядер по умолчанию настроено как в области службы, так и в области ресурсов, значение из области ресурсов будет переопределять значение из области службы, так как это самая низкая **настроенная пользователем** область для заданного параметра.

Конкретные сведения о конфигурации см. в соответствующих статьях:

Руководство. 
- [Настройка главного экземпляра [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](configure-sql-server-master-instance.md)
- [Настройка Apache Spark и Apache Hadoop в Кластерах больших данных](configure-spark-hdfs.md)

Справочные материалы. 
- [Свойства конфигурации главного экземпляра SQL Server](reference-config-master-instance.md)
- [Свойства конфигурации Apache Spark и Apache Hadoop (HDFS)](reference-config-spark-hadoop.md)
