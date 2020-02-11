---
title: Состояние служб PDW
description: Состояние служб параллельного хранилища данных (PDW) для аналитической системы платформы аналитики.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2789c8b74420a56a32d08a0339d4ee6d3cc112d1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400853"
---
# <a name="parallel-data-warehouse-services-status-for-analytics-platform-system"></a>Состояние служб параллельного хранилища данных для системы аналитики
На странице " **состояние служб** параллельного хранилища данных" в Microsoft Analytics Platform System Configuration Manager показано текущее состояние всех служб SQL Server PDW, а также возможность ЗАПУСКАТЬ службы PDW. Это единственный поддерживаемый метод запуска и остановки служб PDW. Обратите внимание, что отдельные компоненты или службы не могут быть запущены независимо.  
  
#### <a name="to-start-or-stop-the-appliance-services"></a>Запуск или завершение служб устройства  
  
1.  Чтобы запустить службы устройств, нажмите кнопку **запустить устройство**.  
  
2.  Чтобы отключить службы устройств, нажмите кнопку " **Закрыть устройство**".  
  
Не обязательно нажимайте кнопку **Применить** при запуске и остановке служб устройства с помощью команды **запустить устройство** и **остановить устройство**.  
  
![Службы PDW устройств DWConfig](./media/pdw-services-status/SQL_Server_PDW_DWConfig_ApplPDWServices.png "SQL_Server_PDW_DWConfig_ApplPDWServices")  
  
> [!NOTE]  
> Остановка региона PDW также останавливает работу агента PDW (склдважент) на узлах. Агенту PDW требуется узел элемента управления PDW, чтобы сообщить о мониторинге работоспособности.  
  
## <a name="see-also"></a>См. также:  
[Включите или отключите устройство APS &#40;ную систему платформы аналитики&#41;](power-the-aps-appliance-on-or-off.md)  
  
