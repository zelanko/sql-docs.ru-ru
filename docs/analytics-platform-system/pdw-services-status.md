---
title: Состояние службы PDW (система платформы аналитики)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fc9bee2-c372-4c4a-956c-fb54215d8918
caps.latest.revision: 14
ms.openlocfilehash: 727adf27c5118130682d8d63eb120c67380ac20d
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="pdw-services-status"></a>Состояние службы PDW
Parallel Data Warehouse **состояние служб** текущее состояние всех служб SQL Server PDW страницы в Microsoft Analytics платформы System Configuration Manager, а также предоставляет возможность останавливать и запускать службы PDW. Это единственный поддерживаемый способ запуска и остановки службы PDW. Обратите внимание, что отдельные компоненты и службы не может запускаться независимо друг от друга.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>Чтобы запустить или остановить службы устройства  
  
1.  Для запуска служб устройство, нажмите кнопку **запуска устройства**.  
  
2.  Чтобы остановить службы устройство, нажмите кнопку **остановить устройство**.  
  
Нет необходимости щелкните **применить** при запуске и остановке службы устройства с помощью **запуска устройства** и **остановить устройство**.  
  
![DWConfig Appliance PDW Services](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> Остановка регион PDW также приводит к прекращению агента PDW (sqldwagent) на узлах область HDInsight. Область HDInsight по-прежнему работает, однако наблюдение за работоспособностью, будут недоступны. (Агент PDW требуется узла управления PDW для наблюдения за работоспособностью.)  
  
## <a name="see-also"></a>См. также  
[Питание устройства APS об отключении &#40;система платформы аналитики&#41;](power-the-aps-appliance-on-or-off.md)  
  
