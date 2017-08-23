---
title: "Добавление служб SSIS масштабирования работника с масштабированием Manager | Документы Microsoft"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b769236330941a107865a0b133961bce5bf6b85b
ms.contentlocale: ru-ru
ms.lasthandoff: 08/03/2017

---
# <a name="add-a-scale-out-worker-with-scale-out-manager"></a>Добавить работника для горизонтального масштабирования с масштабированием Manager

Интеграция шкалы ожидания диспетчера служб значительно отказаться сложности Добавление шкалы Out работника в существующую среду масштабное развертывание. 

Ниже действия позволяют добавлять работника Out шкалы топологию масштабное развертывание:

## <a name="1-install-scale-out-worker"></a>1. Установить работника для горизонтального масштабирования
В мастере установки SQL Server выберите службы Integration Services и масштаб Out работника на **Выбор компонентов** страницы. 
![Выбор рабочей роли](media/feature-select-worker.PNG)

На **конфигурации Integration Services шкалы Out - рабочий узел** , просто щелкните «Далее», чтобы пропустить настройку здесь и используйте **шкалы ожидания диспетчера** делать после установки.

Завершение работы мастера установки.

## <a name="2-open-firewall-on-scale-out-master-computer"></a>2. Откройте брандмауэр на шкале Out главного компьютера
Открыть порт, указанный во время масштабирования Out установочной копии (по умолчанию 8391) и порт для SQL Server (по умолчанию 1433) с помощью брандмауэра Windows на компьютере шкалы Out Master.

## <a name="3-add-scale-out-worker-with-scale-out-manager"></a>3. Добавить работника для горизонтального масштабирования с масштабированием Manager
Запуск от имени администратора SQL Server Management Studio и подключитесь к экземпляру SQL Server шкалы Out образца.

Щелкните правой кнопкой мыши **SSISDB** в обозревателе объектов и выбрать **управление масштабное развертывание...** . 

![Управление горизонтального масштабирования](media/manage-scale-out.PNG)

В стека вверх **шкалы ожидания диспетчера**, переключитесь в **диспетчера рабочих процессов**. Нажмите кнопку «+» кнопки и следуйте инструкциям в диалоговом окне подключения работника. Дополнительные сведения см. в разделе [шкалы ожидания диспетчера](integration-services-ssis-scale-out-manager.md).

