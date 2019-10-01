---
title: Обновление до нового выпуска
titleSuffix: SQL Server big data clusters
description: Узнайте, как обновить [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] (Предварительная версия) до нового выпуска.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bb1bf33c9ccb342e6afc4d22d67463791c0d67b6
ms.sourcegitcommit: 36c3ead6f2a3628f58040acf47f049f0b0957b8a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2019
ms.locfileid: "71688276"
---
# <a name="how-to-upgrade-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Обновление [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья содержит указания по обновлению кластера больших данных SQL Server до нового выпуска. Действия, описанные в этой статье, касаются обновления между выпусками предварительной версии.

## <a name="backup-and-delete-the-old-cluster"></a>Резервное копирование и удаление старого кластера

Сейчас единственный способ обновления кластера больших данных до нового выпуска заключается в ручном удалении и повторном создании кластера. Каждый выпуск имеет уникальную версию `azdata`, которая не совместима с предыдущей версией. Кроме того, если старому кластеру потребовалось скачать образ на новом узле, последний образ может быть несовместим с более старыми образами в кластере. Для обновления до последнего выпуска сделайте следующее.

1. Перед удалением старого кластера выполните резервное копирование данных в основном экземпляре SQL Server и в HDFS. Для основного экземпляра SQL Server можно использовать [резервное копирование и восстановление SQL Server](data-ingestion-restore-database.md). Для HDFS [можно скопировать данные с помощью `curl`](data-ingestion-curl.md).

1. Удалите старый кластер с помощью команды `azdata delete cluster`.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Используйте версию `azdata`, соответствующую кластеру. Не удаляйте старый кластер с более новой версией `azdata`.

   > [!Note]
   > Выполнение команды `azdata bdc delete` приведет к тому, что все объекты, созданные в пространстве имен с именем кластера больших данных, будут удалены, но не будут самим пространством имен. Пространство имен можно повторно использовать для последующих развертываний, если оно пусто и другие приложения не были созданы в.

1. До CTP 3,2 был вызван `azdata` `mssqlctl`. Если у вас есть предыдущие выпуски `mssqlctl` или `azdata`, перед установкой последней версии `azdata` важно сначала удалить.

   Для CTP 2.3 или более поздней версии выполните приведенную ниже команду. Замените `ctp3.1` в команде на версию `mssqlctl`, которую вы удаляете. Если используется версия младше CTP 3.1, добавьте тире перед номером версии (например, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r https://aka.ms/azdata
   ```

1. Установите последнюю версию `azdata`. Следующие команды устанавливают @no__t – 0 для версии-кандидата:

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux:**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > Для каждого выпуска изменяется путь к `azdata`. Даже если вы ранее устанавливали `azdata` или `mssqlctl`, перед созданием нового кластера необходимо переустановить из последнего пути.

## <a id="azdataversion"></a> Проверка версии azdata

Перед развертыванием нового кластера больших данных убедитесь, что используется последняя версия `azdata` с параметром `--version`:

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Установка нового выпуска

После удаления предыдущего кластера больших данных и установки последней версии `azdata` разверните новый кластер больших данных с помощью текущих инструкций по развертыванию. Дополнительные сведения см. [в статье развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md). Затем восстановите все необходимые базы данных или файлы.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в разделе [что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](big-data-cluster-overview.md).
