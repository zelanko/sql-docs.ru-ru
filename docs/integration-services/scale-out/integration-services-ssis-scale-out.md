---
title: SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
description: В этой статье приводятся общие сведения о компоненте SQL Server Integration Services (SSIS) Scale Out, который обеспечивает выполнение пакетов SSIS с высокой производительностью.
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bea5d30cb17920584c4d4eafdf888eeedbc014e6
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58282948"
---
# <a name="integration-services-ssis-scale-out"></a>Масштабное развертывание служб Integration Services (SSIS)
Компонент SQL Server [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (SSIS) Scale Out обеспечивает выполнение пакетов SSIS с высокой производительностью, распределяя его по нескольким компьютерам. После настройки Scale Out можно выполнять несколько пакетов параллельно, в режиме горизонтального масштабирования, из SQL Server Management Studio (SSMS).

## <a name="components"></a>Components
[!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out состоит из мастера [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out и одной или нескольких рабочих ролей [!INCLUDE[ssIS_md](../../includes/ssis-md.md)] Scale Out.

-   Главная роль масштабного развертывания отвечает за управление масштабным развертыванием и получает запросы на выполнение пакетов от пользователей. Дополнительные сведения см. в разделе [Мастер Scale Out](integration-services-ssis-scale-out-master.md).

-   Рабочие роли Scale Out получают задачи на выполнение от мастера Scale Out и выполняют пакеты. Дополнительные сведения см. в разделе [Рабочая роль Scale Out](integration-services-ssis-scale-out-worker.md).

## <a name="configuration-options"></a>Параметры конфигурации
Компонент Scale Out можно настроить в следующих конфигурациях:

-   **с одним компьютером**: мастер Scale Out и рабочая роль Scale Out выполняются на одном компьютере;

-   **с несколькими компьютерами**: каждая рабочая роль Scale Out находится на отдельном компьютере.

## <a name="what-you-can-do"></a>Возможные действия
После настройки Scale Out вы можете выполнять указанные ниже действия.

-   Параллельно выполнять несколько пакетов, развернутых в каталоге SSISDB. Дополнительные сведения см. в статье [Выполнение пакетов в масштабном развертывании](run-packages-in-integration-services-ssis-scale-out.md).

-   Управлять топологией Scale Out в диспетчере Scale Out. Дополнительные сведения см. в статье [Диспетчер Integration Services Scale Out](integration-services-ssis-scale-out-manager.md).

## <a name="next-steps"></a>Следующие шаги
-   [Начало работы с SSIS Scale Out на одном компьютере](get-started-with-ssis-scale-out-onebox.md)

-   [Пошаговое руководство. Настройка Integration Services Scale Out](walkthrough-set-up-integration-services-scale-out.md)
