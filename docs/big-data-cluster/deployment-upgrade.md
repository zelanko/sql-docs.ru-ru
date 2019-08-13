---
title: Обновление до нового выпуска
titleSuffix: SQL Server big data clusters
description: Сведения об обновлении кластеров больших данных SQL Server 2019 (предварительная версия) до нового выпуска.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7bdb1eb59fd36d065df9dba0f6d6879c1a294914
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/25/2019
ms.locfileid: "68419392"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>Обновление кластеров больших данных SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья содержит указания по обновлению кластера больших данных SQL Server до нового выпуска. Действия, описанные в этой статье, касаются обновления между выпусками предварительной версии.

## <a name="backup-and-delete-the-old-cluster"></a>Резервное копирование и удаление старого кластера

Сейчас единственный способ обновления кластера больших данных до нового выпуска заключается в ручном удалении и повторном создании кластера. Каждый выпуск имеет уникальную версию **azdata**, которая не совместима с предыдущей версией. Кроме того, если старому кластеру потребовалось скачать образ на новом узле, последний образ может быть несовместим с более старыми образами в кластере. Для обновления до последнего выпуска сделайте следующее.

1. Перед удалением старого кластера выполните резервное копирование данных в основном экземпляре SQL Server и в HDFS. Для основного экземпляра SQL Server можно использовать [резервное копирование и восстановление SQL Server](data-ingestion-restore-database.md). Для HDFS можно [скопировать данные с помощью **curl**](data-ingestion-curl.md).

1. Удалите старый кластер с помощью команды `azdata delete cluster`.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Используйте версию **azdata**, соответствующую кластеру. Не удаляйте старый кластер с более новой версией **azdata**.

1. До CTP 3.2 средство **azdata** называлось **mssqlctl**. Если установлены какие-либо предыдущие выпуски **mssqlctl** или **azdata**, нужно обязательно удалить их перед установкой последней версии **azdata**.

   Для CTP 2.3 или более поздней версии выполните приведенную ниже команду. Замените `ctp3.1` в команде на удаляемую версию **mssqlctl**. Если используется версия младше CTP 3.1, добавьте тире перед номером версии (например, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r https://mcr.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

1. Установите последнюю версию **azdata**. Следующие команды устанавливают **azdata** для CTP 3.2.

   **Windows:**

   ```powershell
   pip3 install -r https://aka.ms/azdata
   ```

   **Linux:**

   ```bash
   pip3 install -r https://aka.ms/azdata --user
   ```

   > [!IMPORTANT]
   > В каждом выпуске путь к **azdata** изменяется. Даже если вы ранее устанавливали **azdata** или **mssqlctl**, перед созданием кластера нужно выполнить переустановку из актуального пути.

## <a id="azdataversion"></a> Проверка версии azdata

Перед развертыванием нового кластера больших данных убедитесь, что вы используете последнюю версию **azdata** с параметром `--version`.

```bash
azdata --version
```

## <a name="install-the-new-release"></a>Установка нового выпуска

После удаления предыдущего кластера больших данных и установки последней версии **azdata** разверните новый кластер больших данных с помощью актуальных инструкций по развертыванию. Дополнительные сведения см. в статье [Развертывание кластеров больших данных SQL Server в Kubernetes](deployment-guidance.md). Затем восстановите все необходимые базы данных или файлы.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах больших данных см. в статье [Что такое кластеры больших данных SQL Server?](big-data-cluster-overview.md)
