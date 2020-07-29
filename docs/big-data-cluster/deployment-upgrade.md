---
title: Обновление до нового выпуска
titleSuffix: SQL Server Big Data Clusters
description: Сведения об обновлении кластеров больших данных SQL Server до нового выпуска.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 02/13/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: dedae90b5242282fb550ebc59c5a4d98d21506f3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85764072"
---
# <a name="how-to-upgrade-big-data-clusters-2019"></a>Обновление [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

Способ обновления зависит от текущей версии Кластера больших данных SQL Server. Чтобы выполнить обновление поддерживаемого выпуска, включая выпуск для общего распространения (GDR), накопительное обновление (CU) или исправление QFE, можно выполнить обновление на месте. Обновление на месте CTP-версии или версии-кандидата BDC не поддерживается. Необходимо удалить и повторно создать кластер. В следующих разделах описаны шаги для каждого сценария.

- [Обновление поддерживаемого выпуска](#upgrade-from-supported-release)
- [Обновление развертывания BDC версии-кандидата или CTP-версии](#update-a-bdc-deployment-from-ctp-or-release-candidate)

>[!NOTE]
>Первый поддерживаемый выпуск Кластеров больших данных — SQL Server 2019 GDR1.

## <a name="upgrade-release-notes"></a>Заметки о выпуске обновления

Прежде чем продолжить, просмотрите [известные проблемы в заметках о выпуске обновления](release-notes-big-data-cluster.md#known-issues).

## <a name="upgrade-from-supported-release"></a>Обновление поддерживаемого выпуска

В этом разделе объясняется, как обновить поддерживаемый выпуск BDC SQL Server (начиная с версии SQL Server 2019 GDR1) до более нового поддерживаемого выпуска.

1. Выполните резервное копирование главного экземпляра SQL Server.
2. Выполните резервное копирование HDFS.

   ```
   azdata bdc hdfs cp --from-path <path> --to-path <path>
   ```
   
   Пример: 

   ```
   azdata bdc hdfs cp --from-path hdfs://user/hive/warehouse/%%D --to-path ./%%D
   ```

3. Обновите `azdata`.

   Следуйте инструкциям по установке `azdata`. 
   - [Установщик Windows](deploy-install-azdata-installer.md)
   - [Linux — apt](deploy-install-azdata-linux-package.md)
   - [Linux — yum](deploy-install-azdata-yum.md)
   - [Linux — zypper](deploy-install-azdata-zypper.md)

   >[!NOTE]
   >Если `azdata` был установлен с помощью `pip`, необходимо вручную удалить его перед установкой с помощью установщика Windows или диспетчера пакетов Linux.

1. Обновите Кластер больших данных.

   ```
   azdata bdc upgrade -n <clusterName> -t <imageTag> -r <containerRegistry>/<containerRepository>
   ```

   Например, в следующем скрипте используется тег образа `2019-CU4-ubuntu-16.04`:

   ```
   azdata bdc upgrade -n bdc -t 2019-CU4-ubuntu-16.04 -r mcr.microsoft.com/mssql/bdc
   ```

>[!NOTE]
>Последние версии тегов образов можно найти в статье [Заметки о выпуске кластеров больших данных SQL Server](release-notes-big-data-cluster.md).

>[!IMPORTANT]
>Если вы используете частный репозиторий, чтобы предварительно извлечь образы для развертывания или обновления BDC, убедитесь, что текущие образы сборки, а также образы целевой сборки находятся в частном репозитории. Так вы сможете при необходимости успешно выполнить откат. Кроме того, если вы изменили учетные данные частного репозитория с момента первоначального развертывания, обновите соответствующие переменные среды DOCKER_PASSWORD и DOCKER_USERNAME. Обновление с использованием других частных репозиториев не поддерживается для текущих и целевых сборок.

### <a name="increase-the-timeout-for-the-upgrade"></a>Увеличение времени ожидания для обновления

Если определенные компоненты не обновятся в выделенное время, может произойти превышение времени ожидания. В приведенном ниже коде показано, как может выглядеть ошибка:

   ```
   >azdata.EXE bdc upgrade --name <mssql-cluster>
   Upgrading cluster to version 15.0.4003

   NOTE: Cluster upgrade can take a significant amount of time depending on
   configuration, network speed, and the number of nodes in the cluster.

   Upgrading Control Plane.
   Control plane upgrade failed. Failed to upgrade controller.
   ```

Если вы хотите увеличить время ожидания для обновления, используйте параметры **--controller-timeout** и **--component-timeout**, чтобы указать более высокие значения времени ожидания при обновлении. Этот параметр доступен только начиная с выпуска SQL Server 2019 CU2. Пример:

   ```bash
   azdata bdc upgrade -t 2019-CU4-ubuntu-16.04 --controller-timeout=40 --component-timeout=40 --stability-threshold=3
   ```
**--controller-timeout** — указывает количество минут ожидания завершения обновления для базы данных контроллера или контроллера.
**--component-timeout** — определяет время, необходимое для выполнения каждого следующего этапа обновления.

Чтобы увеличить время ожидания для обновления до выпуска SQL Server 2019 CU2, измените схему конфигурации обновления. Чтобы изменить схему конфигурации обновления, выполните следующие действия:

Выполните следующую команду:

   ```bash
   kubectl edit configmap controller-upgrade-configmap
   ```

Измените следующие поля:

   **controllerUpgradeTimeoutInMinutes**: указывает количество минут ожидания завершения обновления базы данных контроллера или контроллера. Значение по умолчанию — 5. Используйте значение не ниже 20.
   **totalUpgradeTimeoutInMinutes**: определяет совокупный интервал времени, в течение которого контроллер и база данных контроллера должны завершить обновление (обновление контроллера и базы данных контроллера). Значение по умолчанию — 10. Используйте значение не ниже 40.
   **componentUpgradeTimeoutInMinutes**: определяет время, необходимое для выполнения каждого следующего этапа обновления. Значение по умолчанию — 30. Замените на 45.

Сохраните и закройте.

## <a name="update-a-bdc-deployment-from-ctp-or-release-candidate"></a>Обновление развертывания BDC версии-кандидата или CTP-версии

Обновление на месте CTP-версии или сборки версии-кандидата Кластеров больших данных SQL Server не поддерживается. В следующем разделе объясняется, как вручную удалить и повторно создать кластер.

### <a name="backup-and-delete-the-old-cluster"></a>Резервное копирование и удаление старого кластера

Обновление на месте для кластеров больших данных, развернутых до версии SQL Server 2019 GDR1, не поддерживается. Единственный способ обновить до нового выпуска — вручную удалить и повторно создать кластер. Каждый выпуск имеет уникальную версию `azdata`, которая не совместима с предыдущей версией. Кроме того, если новый образ контейнера скачивается в кластер, развернутый с помощью другой более старой версии, последний образ может быть несовместим со старыми образами в кластере. Новый образ извлекается при использовании тега образа `latest` в файле конфигурации развертывания для параметров контейнера. По умолчанию каждый выпуск имеет определенный тег образа, соответствующий версии выпуска SQL Server. Для обновления до последнего выпуска сделайте следующее.

1. Перед удалением старого кластера выполните резервное копирование данных в основном экземпляре SQL Server и в HDFS. Для основного экземпляра SQL Server можно использовать [резервное копирование и восстановление SQL Server](data-ingestion-restore-database.md). Для HDFS можно [скопировать данные с помощью `curl`](data-ingestion-curl.md).

1. Удалите старый кластер с помощью команды `azdata delete cluster`.

   ```bash
    azdata bdc delete --name <old-cluster-name>
   ```

   > [!Important]
   > Используйте версию `azdata`, соответствующую вашему кластеру. Не удаляйте старый кластер с более новой версией `azdata`.

   > [!Note]
   > Выполнение команды `azdata bdc delete` приведет к тому, что все объекты, созданные в пространстве имен с именем кластера больших данных, будут удалены, однако само пространство имен удалено не будет. Пространство имен можно повторно использовать для последующих развертываний, если оно пусто и в нем не созданы другие приложения.

1. Удалите старую версию `azdata`.

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

### <a name="verify-the-azdata-version"></a><a id="azdataversion"></a> Проверка версии azdata

Перед развертыванием нового кластера больших данных убедитесь, что вы используете последнюю версию `azdata` с параметром `--version`.

```bash
azdata --version
```

### <a name="install-the-new-release"></a>Установка нового выпуска

После удаления предыдущего кластера больших данных и установки последней версии `azdata` разверните новый кластер больших данных с помощью актуальных инструкций по развертыванию. Дополнительные сведения см. в статье [Развертывание [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)] в Kubernetes](deployment-guidance.md). Затем восстановите все необходимые базы данных или файлы.

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ss-nover.md)]](big-data-cluster-overview.md).
