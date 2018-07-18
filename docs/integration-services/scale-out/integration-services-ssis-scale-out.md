---
title: SQL Server Integration Services (SSIS) Scale Out | Документы Майкрософт
description: В этой статье приводятся общие сведения о компоненте SQL Server Integration Services (SSIS) Scale Out, который обеспечивает выполнение пакетов SSIS с высокой производительностью.
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: dcfbd1c5-c001-4fb7-b9ae-916e49ab6a96
caps.latest.revision: 6
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7fc57db9bc8a305450aa2619d9b7c222fda91763
ms.sourcegitcommit: de5e726db2f287bb32b7910831a0c4649ccf3c4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35334088"
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

-   [Пошаговое руководство. Настройка масштабного развертывания Integration Services](walkthrough-set-up-integration-services-scale-out.md)
