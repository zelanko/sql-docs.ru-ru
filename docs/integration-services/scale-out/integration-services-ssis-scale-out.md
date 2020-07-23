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
ms.openlocfilehash: ecbaefa45dd7088d7747c20c3e404cc4c744ad29
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86918979"
---
# <a name="integration-services-ssis-scale-out"></a>Горизонтальное увеличение масштаба служб Integration Services (SSIS)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


Компонент SQL Server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) с горизонтальным увеличением масштаба обеспечивает выполнение пакетов SSIS с высокой производительностью, распределяя его по нескольким компьютерам. После настройки развертывания с горизонтальным увеличением масштаба можно выполнять несколько пакетов параллельно, в режиме горизонтального увеличения масштаба, из SQL Server Management Studio (SSMS).

## <a name="components"></a>Components
Развертывание [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] с горизонтальным увеличением масштаба состоит из мастера [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] горизонтального увеличения масштаба и одной или нескольких рабочих ролей [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] горизонтального увеличения масштаба.

-   Главная роль горизонтального увеличения масштаба отвечает за управление масштабным развертыванием и получает запросы на выполнение пакетов от пользователей. Дополнительные сведения см. в разделе [Мастер горизонтального увеличения масштаба](integration-services-ssis-scale-out-master.md).

-   Рабочие роли горизонтального увеличения масштаба получают задачи на выполнение от мастера горизонтального увеличения масштаба и выполняют пакеты. Дополнительные сведения см. в разделе [Рабочая роль горизонтального увеличения масштаба](integration-services-ssis-scale-out-worker.md).

## <a name="configuration-options"></a>Варианты настройки
Компонент с горизонтальным увеличением масштаба можно настроить в следующих конфигурациях:

-   **с одним компьютером**: мастер горизонтального увеличения масштаба и рабочая роль горизонтального увеличения масштаба выполняются на одном компьютере;

-   **с несколькими компьютерами**: каждая рабочая роль горизонтального увеличения масштаба находится на отдельном компьютере.

## <a name="what-you-can-do"></a>Возможные действия
После настройки развертывания с горизонтальным увеличением масштаба вы можете выполнять указанные ниже действия.

-   Параллельно выполнять несколько пакетов, развернутых в каталоге SSISDB. Дополнительные сведения см. в статье [Выполнение пакетов в развертывании с горизонтальным увеличением масштаба](run-packages-in-integration-services-ssis-scale-out.md).

-   Управлять топологией горизонтального увеличения масштаба в диспетчере горизонтального увеличения масштаба. Дополнительные сведения см. в статье [Диспетчер горизонтального увеличения масштаба Integration Services](integration-services-ssis-scale-out-manager.md).

## <a name="next-steps"></a>Дальнейшие действия
-   [Начало работы с развертыванием SSIS с горизонтальным увеличением масштаба на одном компьютере](get-started-with-ssis-scale-out-onebox.md)

-   [Пошаговое руководство. Настройка развертывания Integration Services с горизонтальным увеличением масштаба](walkthrough-set-up-integration-services-scale-out.md)
