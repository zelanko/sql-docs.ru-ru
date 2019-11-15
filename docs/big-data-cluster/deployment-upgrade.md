---
title: Обновление до нового выпуска
titleSuffix: SQL Server Big Data Clusters
description: Сведения об обновлении кластеров больших данных SQL Server до нового выпуска.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f44ef17a712d0d5a19707cf94e7d3e4196a2aba3
ms.sourcegitcommit: b4ad3182aa99f9cbfd15f4c3f910317d6128a2e5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73706308"
---
# <a name="how-to-upgrade-includebig-data-clusters-2019includesssbigdataclusters-ss-novermd"></a>Обновление [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья содержит указания по обновлению кластера больших данных SQL Server до нового выпуска. Описанные в этой статье действия позволяют перейти с предварительной версии на служебное обновление SQL Server 2019.

## <a name="backup-and-delete-the-old-cluster"></a>Резервное копирование и удаление старого кластера

В настоящее время пути обновления кластеров больших данных отсутствуют. Единственный способ перехода на новый выпуск заключается в удалении и повторном создании кластера вручную. Каждый выпуск имеет уникальную версию `azdata`, которая не совместима с предыдущей версией. Кроме того, если старому кластеру потребовалось скачать образ контейнера на новом узле, последний образ может быть несовместим с более старыми образами в кластере. Обратите внимание, что новый образ извлекается только при использовании тега образа `latest` в файле конфигурации развертывания для параметров контейнера. По умолчанию каждый выпуск имеет определенный тег образа, соответствующий версии выпуска SQL Server. Для обновления до последнего выпуска сделайте следующее.

1. Перед удалением старого кластера выполните резервное копирование данных в основном экземпляре SQL Server и в HDFS. Для основного экземпляра SQL Server можно использовать [резервное копирование и восстановление SQL Server](data-ingestion-restore-database.md). Для HDFS можно [скопировать данные с помощью `curl`](data-ingestion-curl.md).

1. Удалите старый кластер с помощью команды `azdata delete cluster`.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Используйте версию `azdata`, соответствующую вашему кластеру. Не удаляйте старый кластер с более новой версией `azdata`.

   > [!Note]
   > Выполнение команды `azdata bdc delete` приведет к тому, что все объекты, созданные в пространстве имен с именем кластера больших данных, будут удалены, однако само пространство имен удалено не будет. Пространство имен можно повторно использовать для последующих развертываний, если оно пусто и в нем не созданы другие приложения.

1. Удаление старой версии `azdata`

   ```powershell
   pip3 uninstall -r https://azdatacli.blob.core.windows.net/python/azdata/2019-rc1/requirements.txt
   ```

1. Установка последней версии `azdata`. Следующие команды устанавливают `azdata` из последнего выпуска:

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux:**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > В каждом выпуске путь к версии `azdata``n-1` изменяется. Даже если вы ранее устанавливали `azdata`, перед созданием кластера нужно выполнить переустановку из актуального пути.

## <a id="azdataversion"></a> Проверка версии azdata

Перед развертыванием нового кластера больших данных убедитесь, что вы используете последнюю версию `azdata` с параметром `--version`.

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Установка нового выпуска

После удаления предыдущего кластера больших данных и установки последней версии `azdata` разверните новый кластер больших данных с помощью актуальных инструкций по развертыванию. Дополнительные сведения см. в статье [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md). Затем восстановите все необходимые базы данных или файлы.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](big-data-cluster-overview.md).
