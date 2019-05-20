---
title: Поддержка высокого уровня доступности в SQL Server Integration Services (SSIS) Scale Out с помощью экземпляра отказоустойчивого кластера SQL Server | Документы Майкрософт
description: В этой статье описывается настройка высокой доступности для SSIS Scale Out с помощью экземпляра отказоустойчивого кластера SQL Server.
ms.custom: performance
ms.date: 04/10/2018
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: a834d527b7356383d942ea7b764d33a427d23a70
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/16/2019
ms.locfileid: "65718392"
---
# <a name="scale-out-support-for-high-availability-via-sql-server-failover-cluster-instance"></a>Поддержка Scale Out для обеспечения высокой доступности с помощью экземпляра отказоустойчивого кластера SQL Server

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]



Чтобы обеспечить высокий уровень доступности на стороне мастера Scale Out с использованием экземпляра отказоустойчивого кластера SQL Server, выполните следующие действия:

## <a name="1-prerequisites"></a>1. предварительные требования
Настроить отказоустойчивый кластер Windows. Инструкции см. в записи блога [Установка компонента и средств отказоустойчивого кластера для Windows Server 2012](https://blogs.msdn.com/b/clustering/archive/2012/04/06/10291601.aspx). Установите компоненты и средства на всех узлах кластера.

## <a name="2-install-sql-server-failover-cluster"></a>2. Установка отказоустойчивого кластера SQL Server
Установите отказоустойчивый кластер SQL Server. Инструкции см. в разделе [Установка отказоустойчивого кластера SQL Server](../../sql-server/failover-clusters/install/sql-server-failover-cluster-installation.md). Во время установки на странице "Выбор компонентов" щелкните "Службы ядра СУБД". Запишите сетевое имя SQL Server для последующей настройки.

![Сетевое имя SQL](media/sql-network-name.PNG)

Добавьте вторичный узел в отказоустойчивый кластер SQL Server.

## <a name="3-install-scale-out-master-on-the-primary-node"></a>3. Установка мастера Scale Out в основном узле
Установите службы Integration Services и мастера Scale Out на основной узел с помощью мастера некластеризованной установки. 

Во время установки включите сетевое имя SQL Server в общие имена сертификата мастера Scale Out.

> [!NOTE]
> Чтобы реализовать раздельную отработку отказа для служб SSISDB и мастера Scale Out, выполните шаг [2. Установка мастера Scale Out в основном узле](scale-out-support-for-high-availability.md#2-install-scale-out-master-on-the-primary-node) для конфигурации мастера Scale Out.

## <a name="4-install-scale-out-master-on-the-secondary-node"></a>4. Установка мастера Scale Out во вторичном узле
Выполните шаг [3. Установка мастера Scale Out во вторичном узле](scale-out-support-for-high-availability.md#3-install-scale-out-master-on-the-secondary-node)

## <a name="5-update-the-scale-out-master-service-configuration-file"></a>5. Обновление файла конфигурации для службы мастера Scale Out
Обновите файл конфигурации для службы мастера Scale Out (\<диск\>:\Program Files\Microsoft SQL Server\140\DTS\Binn\MasterSettings.config) на основном и вторичном узлах. Обновите **SqlServerName** на [сетевое имя SQL Server]//[имя экземпляра] или [сетевое имя SQL Server] для экземпляра по умолчанию.

## <a name="6-add-scale-out-master-service-to-sql-server-role-in-windows-failover-cluster"></a>6. Добавление службы мастера Scale Out в роль SQL Server в кластере Windows
В диспетчере отказоустойчивости кластеров установите подключение к кластеру для Scale Out. Выберите роли в обозревателе, щелкните правой кнопкой мыши роль SQL Server и выберите "Добавить ресурс универсальной службы". 

![Универсальная служба](media/generic-service.PNG)

В мастере создания ресурса выберите службу мастера Scale Out и завершите работу мастера. 

Включите службу мастера Scale Out.

![Включение службы](media/bring-online.PNG)

> [!NOTE]
> Чтобы реализовать раздельную отработку отказа для служб SSISDB и мастера Scale Out, выполните шаг [7. Настройка роли службы мастера Scale Out для отказоустойчивого кластера Windows](scale-out-support-for-high-availability.md#7-configure-the-scale-out-master-service-role-of-the-windows-server-failover-cluster)

## <a name="7-install-scale-out-workers"></a>7. Установка рабочих ролей Scale Out
Установите рабочую роль Scale Out на рабочие узлы. Во время установки укажите https://[сетевое имя SQL Server]:[порт мастера] в качестве конечной точки мастера. 

> [!NOTE]
> Чтобы реализовать раздельную отработку отказа для служб SSISDB и мастера Scale Out, укажите DNS-имя хоста службы мастера Scale Out вместо сетевого имени SQL Server.

## <a name="8-install-scale-out-worker-client-certificate"></a>8. Установка сертификата клиента рабочей роли Scale Out
Установите сертификат рабочей роли на всех узлах отказоустойчивого кластера SQL Server. См. раздел [Установка сертификата клиента рабочей роли Scale Out](walkthrough-set-up-integration-services-scale-out.md#InstallCert).

> [!NOTE]
> Диспетчер Scale Out не поддерживает отказоустойчивый кластер SQL Server. Если для добавления рабочей роли Scale Out вы используете диспетчер Scale Out, вам по-прежнему требуется вручную установить сертификат рабочей роли на все узлы мастера.

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения см. в следующих статьях:
-   [Главная роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-master.md)
-   [Рабочая роль масштабного развертывания служб Integration Services (SSIS)](integration-services-ssis-scale-out-worker.md)
