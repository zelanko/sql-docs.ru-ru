---
title: Горизонтальное увеличение масштаба SQL Server Integration Services (SSIS) | Документы Майкрософт
description: В этой статье приводятся общие сведения о компоненте SQL Server Integration Services (SSIS) с горизонтальным увеличением масштаба, который обеспечивает выполнение пакетов SSIS с высокой производительностью.
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4b4a5b5f27f959f3a04bb3cf5468d198d3ef5267
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71295655"
---
# <a name="integration-services-ssis-scale-out"></a>Горизонтальное увеличение масштаба служб Integration Services (SSIS)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Компонент SQL Server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Scale Out обеспечивает выполнение пакетов SSIS с высокой производительностью, распределяя его по нескольким компьютерам. После настройки развертывания с горизонтальным увеличением масштаба можно выполнять несколько пакетов параллельно, в режиме горизонтального увеличения масштаба, из SQL Server Management Studio (SSMS).

## <a name="components"></a>Components
[!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out состоит из мастера [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out и одной или нескольких рабочих ролей [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out.

-   Главная роль горизонтального увеличения масштаба отвечает за управление масштабным развертыванием и получает запросы на выполнение пакетов от пользователей. Дополнительные сведения см. в разделе [Мастер Scale Out](integration-services-ssis-scale-out-master.md).

-   Рабочие роли горизонтального увеличения масштаба получают задачи на выполнение от мастера горизонтального увеличения масштаба и выполняют пакеты. Дополнительные сведения см. в разделе [Рабочая роль Scale Out](integration-services-ssis-scale-out-worker.md).

## <a name="configuration-options"></a>Варианты настройки
Компонент с горизонтальным увеличением масштаба можно настроить в следующих конфигурациях:

-   **с одним компьютером**: мастер Scale Out и рабочая роль Scale Out выполняются на одном компьютере;

-   **с несколькими компьютерами**: каждая рабочая роль Scale Out находится на отдельном компьютере.

## <a name="what-you-can-do"></a>Возможные действия
После настройки развертывания с горизонтальным увеличением масштаба вы можете выполнять указанные ниже действия.

-   Параллельно выполнять несколько пакетов, развернутых в каталоге SSISDB. Дополнительные сведения см. в статье [Выполнение пакетов в масштабном развертывании](run-packages-in-integration-services-ssis-scale-out.md).

-   Управлять топологией горизонтального увеличения масштаба в диспетчере горизонтального увеличения масштаба. Дополнительные сведения см. в статье [Диспетчер Integration Services Scale Out](integration-services-ssis-scale-out-manager.md).

## <a name="next-steps"></a>Дальнейшие действия
-   [Начало работы с SSIS Scale Out на одном компьютере](get-started-with-ssis-scale-out-onebox.md)

-   [Пошаговое руководство. Настройка масштабного развертывания Integration Services](walkthrough-set-up-integration-services-scale-out.md)
