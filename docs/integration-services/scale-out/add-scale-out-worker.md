---
title: Добавление рабочей роли Scale Out служб SSIS с помощью диспетчера Scale Out | Документы Майкрософт
ms.description: This article describes how to add an SSIS Scale Out Worker to an existing Scale Out environment by using Scale Out Manager.
ms.custom: ''
ms.date: 12/19/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: scale-out
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: 2de6918bf7cb795ba1871b4ac56068c719e721d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Добавление рабочей роли Scale Out с помощью диспетчера Scale Out

Диспетчер Integration Services Scale Out упрощает добавление рабочей роли Scale Out в существующую среду Scale Out. 

Чтобы добавить рабочую роль Scale Out в топологию Scale Out, выполните указанные ниже действия.

## <a name="1-install-scale-out-worker"></a>1. Установка рабочей роли Scale Out
В мастере установки SQL Server на странице **Выбор компонентов** выберите компоненты "Службы Integration Services" и "Рабочая роль Scale Out". 
![Выбор рабочей роли](media/feature-select-worker.PNG)

На странице **Настройка развертывания служб Integration Services — рабочий узел** можно нажать кнопку **Далее**, чтобы пока пропустить настройку. Ее можно будет выполнить с помощью **диспетчера Scale Out** после установки.

Завершите работу мастера установки.

## <a name="2-open-the-firewall-on-the-scale-out-master-computer"></a>2. Открытие брандмауэра на компьютере мастера Scale Out
Откройте порт, указанный во время установки мастера Scale Out (по умолчанию 8391), и порт SQL Server (по умолчанию 1433) в брандмауэре Windows на компьютере с мастером Scale Out.

## <a name="3-add-a-scale-out-worker-with-scale-out-manager"></a>3. Добавление рабочей роли Scale Out с помощью диспетчера Scale Out
Запустите SQL Server Management Studio с правами администратора и подключитесь к экземпляру SQL Server мастера Scale Out.

В обозревателе объектов щелкните правой кнопкой мыши узел **SSISDB** и выберите пункт **Управление развертыванием**. 

![Управление Scale Out](media/manage-scale-out.PNG)

В диалоговом окне **диспетчера Scale Out** перейдите в **диспетчер рабочей роли**. Нажмите кнопку **+** и следуйте инструкциям в диалоговом окне **Подключение узла рабочей роли**. 

## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения см. в разделе [Диспетчер Scale Out](integration-services-ssis-scale-out-manager.md).