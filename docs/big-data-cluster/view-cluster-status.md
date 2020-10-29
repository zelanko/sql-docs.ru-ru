---
title: Ресурсы администрирования для Кластеров больших данных (BDC)
titleSuffix: SQL Server
description: В этой статье объясняется, как просмотреть состояние кластера больших данных с помощью Azure Data Studio, записных книжек и команд Azure Data CLI (azdata).
author: cloudmelon
ms.author: melqin
ms.reviewer: mikeray
ms.date: 10/20/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d469d1b8d89b07748485c9df3f7f7905af52099
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358242"
---
# <a name="administration-resources-for-big-data-clusters-bdc"></a>Ресурсы администрирования для Кластеров больших данных (BDC) 

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

В этой статье описывается, как извне администрировать кластер больших данных SQL Server.

## <a name="know-your-architecture"></a>Знание архитектуры

Начиная с версии SQL Server 2019 (15.x), кластеры больших данных SQL Server обеспечивают развертывание масштабируемых кластеров SQL Server, Spark и контейнеров HDFS, работающих в Kubernetes. В следующих статьях содержится обзор кластера больших данных:
- [Что собой являют кластеры больших данных SQL Server ](big-data-cluster-overview.md)

Кластеры больших данных SQL Server обеспечивают когерентную и отказоустойчивую авторизацию и проверку подлинности. Далее дается обзор безопасности кластера больших данных:
- [Основные понятия безопасности для кластеров больших данных SQL Server](concept-security.md)

## <a name="manage-and-operate-with-tools"></a>Управление инструментами и работа с ними

В следующих статьях описывается, как управлять кластером больших данных и работать с ним такими способами: 

- [Подключение к кластеру больших данных SQL Server с помощью Azure Data Studio](connect-to-big-data-cluster.md)
- [Управление кластерами больших данных для информационной панели контроллера SQL Server](manage-with-controller-dashboard.md)
- [Управление кластерами больших данных SQL Server с помощью записных книжек Azure Data Studio ](notebooks-manage-bdc.md)
- [Управление Кластерами больших данных (BDC) в кластере с помощью записных книжек](cluster-manage-notebooks.md)
- [Запуск примера записной книжки с помощью Spark](notebooks-tutorial-spark.md)

## <a name="monitor-with-tools"></a>Мониторинг с помощью инструментов

Далее описывается мониторинг Кластера больших данных следующими способами: 

- [Выполнение мониторинга кластера BDC с помощью Azure Data Studio](cluster-monitor-ads.md)
- [Выполнение мониторинга кластера BDC с помощью служебной программы Azdata](cluster-monitor-cmdlet.md)
- [Выполнение мониторинга кластера BDC с помощью панели мониторинга Grafana](cluster-monitor-grafana.md)
- [Выполнение мониторинга кластера BDC с помощью записных книжек Juypter и Azure Data Studio](cluster-monitor-notebooks.md)

## <a name="monitor-and-inspect-logs-with-notebooks"></a>Мониторинг и проверка журналов с помощью записных книжек

Далее перечислены многие записные книжки Jupyter, доступные в Azure Data Studio.

- [Мониторинг кластера с помощью записных книжек](cluster-monitor-notebooks.md)
- [Сбор и анализ журналов в кластере с помощью записных книжек](cluster-logging-notebooks.md)

## <a name="big-data-clusters-troubleshooting-resources"></a>Ресурсы по устранению неполадок Кластеров больших данных

В следующих статьях описывается устранение неполадок Кластера больших данных:

- [Устранение неполадок кластера BDC с помощью служебной программы kubectl](cluster-troubleshooting-commands.md) 
- [Устранение неполадок записной книжки pyspark](troubleshoot-pyspark-notebook.md)
- [Устранение неполадок кластера BDC с помощью записных книжек Juypter и Azure Data Studio (ADS)](cluster-troubleshooter-notebooks.md)
- [Восстановление разрешений HDFS](troubleshoot-hdfs-restore-admin.md)

Далее описывается устранение неполадок в Кластере больших данных, развернутом в режиме Active Directory.
- [Устранение неполадок кластера BDC в режиме Active Directory](troubleshoot-active-directory.md) 
- [Устранение неполадок с ошибкой при входе в режим Active Directory](troubleshoot-ad-login-failed-untrusted-domain.md)
- [Устранение неполадок при остановке развертывания в режиме AD BDC](troubleshoot-ad-reverse-lookup-zone.md)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](big-data-cluster-overview.md).