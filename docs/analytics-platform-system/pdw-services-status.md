---
title: Состояние - служб на PDW, Analytics Platform System | Документация Майкрософт
description: Состояние служб Parallel Data Warehouse (PDW) для Analytics Platform System.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3db994b4869c1b017a079b404af3d95db1316dad
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960368"
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>Состояние служб Parallel Data Warehouse для Analytics Platform System
Parallel Data Warehouse **состояние служб** страницы в Microsoft Analytics платформы System Configuration Manager показано текущее состояние всех служб SQL Server PDW, а также предоставляет возможность останавливать и запускать службы PDW. Это единственный поддерживаемый способ запуска и остановки службы PDW. Обратите внимание на то, что отдельные компоненты или службы не может запускаться независимо друг от друга.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>Для запуска или остановки служб устройства  
  
1.  Запуск служб устройство, нажмите кнопку **запустить устройство**.  
  
2.  Чтобы остановить службы устройство, нажмите кнопку **остановить устройство**.  
  
Нет необходимости щелкните **применить** при запуске и остановке службы устройство с помощью **запустить устройство** и **остановить устройство**.  
  
![Службы PDW устройств DWConfig](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> Остановка регион PDW, также прекращается агент PDW (sqldwagent) на узлах. Агент PDW требует от узла управления PDW отчетов наблюдение за работоспособностью.  
  
## <a name="see-also"></a>См. также  
[Питания устройства APS, включить или отключить &#40;Analytics Platform System&#41;](power-the-aps-appliance-on-or-off.md)  
  
