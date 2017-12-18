---
title: "Добавление рабочей роли Scale Out служб SSIS с помощью диспетчера Scale Out | Документы Майкрософт"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ef11448d03bd188aaea425225312af9f681f530c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Добавление рабочей роли Scale Out с помощью диспетчера Scale Out

Диспетчер Scale Out служб Integration Services значительно упрощает добавление рабочей роли Scale Out в существующую среду Scale Out. 

С помощью приведенных ниже действий вы можете добавить рабочую роль Scale Out в свою топологию Scale Out:

## <a name="1-install-scale-out-worker"></a>1. Установка рабочей роли Scale Out
В мастере установки SQL Server на странице **Выбор компонентов** выберите компоненты "Службы Integration Services" и "Рабочая роль Scale Out". 
![Выбор рабочей роли](media/feature-select-worker.PNG)

На странице **Настройка Integration Services Scale Out — рабочий узел** можно просто нажать кнопку "Далее", чтобы пропустить настройку. Ее можно будет выполнить с помощью **диспетчере Scale Out** после установки.

Завершите работу мастера установки.

## <a name="2-open-firewall-on-scale-out-master-computer"></a>2. Открытие брандмауэра на компьютере мастера Scale Out
Откройте порт, указанный во время установки мастера Scale Out (по умолчанию 8391), и порт SQL Server (по умолчанию 1433), используя брандмауэр Windows на компьютере с мастером Scale Out.

## <a name="3-add-scale-out-worker-with-scale-out-manager"></a>3. Добавление рабочей роли Scale Out с помощью диспетчера Scale Out
Запустите SQL Server Management Studio с правами администратора и подключитесь к экземпляру SQL Server мастера Scale Out.

Щелкните правой кнопкой мыши **SSISDB** в обозревателе объектов и выберите пункт **Управление Scale Out...** 

![Управление Scale Out](media/manage-scale-out.PNG)

В открывшемся окне **диспетчера Scale Out** переключитесь на **диспетчера рабочей роли**. Нажмите кнопку "+" и следуйте инструкциям в диалоговом окне подключения рабочей роли. Дополнительные сведения см. в разделе [Диспетчер Scale Out](integration-services-ssis-scale-out-manager.md).
