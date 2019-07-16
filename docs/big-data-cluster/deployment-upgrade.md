---
title: Обновление до нового выпуска
titleSuffix: SQL Server big data clusters
description: Сведения об обновлении кластеров SQL Server 2019 больших данных (Предварительная версия) до нового выпуска.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 67ca9b09db398538b4adeedc9008dcb2f14f258f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958409"
---
# <a name="how-to-upgrade-sql-server-big-data-clusters"></a>Обновление кластеров больших данных в SQL Server

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Статья содержит рекомендации по обновлению кластера больших данных SQL Server до нового выпуска. В частности, действия, описанные в этой статье применяются к обновление между предварительных выпусков.

## <a name="backup-and-delete-the-old-cluster"></a>Резервное копирование и удаление старого кластера

В настоящее время единственный способ обновления до нового выпуска кластерам больших данных — вручную удаления и повторного создания кластера. Каждый выпуск содержит уникальной версии **mssqlctl** , не совместим с предыдущей версией. Кроме того Если кластер старых нужно было загрузить изображения на новый узел, последний образ может оказаться несовместимым с старые образы в кластере. Чтобы обновить до последней версии, следуйте инструкциям ниже:

1. Перед удалением старого кластера, резервное копирование данных на экземпляре SQL Server master и в HDFS. Для главного экземпляра SQL Server, можно использовать [Архивация и восстановление SQL Server](data-ingestion-restore-database.md). Для HDFS вы [можно скопировать данные с **curl**](data-ingestion-curl.md).

1. Удалите старый кластер с `mssqlctl delete cluster` команды.

   ```bash
    mssqlctl bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Используйте версию **mssqlctl** , соответствующий кластер. Не удаляйте кластер старых с новой версией **mssqlctl**.

1. Если у вас есть все предыдущие выпуски **mssqlctl** установлен, очень важно удалить **mssqlctl** перед установкой последней версии.

   Для CTP-версия 2.3 или более поздней версии выполните следующую команду. Замените `ctp3.0` в команде с версией **mssqlctl** , при удалении. Если версия до версии CTP 3.0, добавить дефис перед номер версии (например, `ctp-2.5`).

   ```powershell
   pip3 uninstall -r  https://private-repo.microsoft.com/python/ctp3.0/mssqlctl/requirements.txt
   ```

1. Установите последнюю версию **mssqlctl**. Следующие команды устанавливают **mssqlctl** для CTP-версии 3.1:

   **Windows:**

   ```powershell
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt
   ```

   **Linux:**

   ```bash
   pip3 install -r  https://private-repo.microsoft.com/python/ctp3.1/mssqlctl/requirements.txt --user
   ```

   > [!IMPORTANT]
   > Для каждого выпуска, путь к **mssqlctl** изменения. Даже если вы ранее установили **mssqlctl**, необходимо переустановить из последней пути перед созданием нового кластера.

## <a id="mssqlctlversion"></a> Проверка версии mssqlctl

Перед развертыванием нового кластера больших данных, убедитесь, что вы используете последнюю версию **mssqlctl** с `--version` параметр:

```bash
mssqlctl --version
```

## <a name="install-the-new-release"></a>Установить новый выпуск

После удаления предыдущего кластера больших данных и установки последней версии **mssqlctl**, развернуть новый кластер больших данных с помощью текущей инструкции по развертыванию. Дополнительные сведения см. в разделе [развертывание больших данных в SQL Server кластеров Kubernetes](deployment-guidance.md). Затем восстановите все необходимые базы данных или файлов.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о кластерах большие данные см. в разделе [Каковы кластеров SQL Server с большими данными](big-data-cluster-overview.md).
