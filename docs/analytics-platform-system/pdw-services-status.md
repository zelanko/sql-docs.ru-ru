---
title: PDW служб состояния — Analytics Platform System | Документы Microsoft
description: Состояние служб хранилища параллельных данных (PDW) для Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e2252bb821f9522515f1625b0fc118323cb50d1f
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>Параллельное хранилище данных состояния службы для система платформы аналитики
Parallel Data Warehouse **состояние служб** текущее состояние всех служб SQL Server PDW страницы в Microsoft Analytics платформы System Configuration Manager, а также предоставляет возможность останавливать и запускать службы PDW. Это единственный поддерживаемый способ запуска и остановки службы PDW. Обратите внимание, что отдельные компоненты и службы не может запускаться независимо друг от друга.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>Чтобы запустить или остановить службы устройства  
  
1.  Для запуска служб устройство, нажмите кнопку **запуска устройства**.  
  
2.  Чтобы остановить службы устройство, нажмите кнопку **остановить устройство**.  
  
Нет необходимости щелкните **применить** при запуске и остановке службы устройства с помощью **запуска устройства** и **остановить устройство**.  
  
![Службы PDW DWConfig](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> Остановка регион PDW также приводит к прекращению агента PDW (sqldwagent) на узлах область HDInsight. Область HDInsight по-прежнему работает, однако наблюдение за работоспособностью, будут недоступны. (Агент PDW требуется узла управления PDW для наблюдения за работоспособностью.)  
  
## <a name="see-also"></a>См. также  
[Питание устройства APS об отключении &#40;система платформы аналитики&#41;](power-the-aps-appliance-on-or-off.md)  
  
