---
title: Проверка параметра максимального числа рабочих потоков | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
caps.latest.revision: 17
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 335d466db042684a725a334238be5fbcee42c3d4
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32952789"
---
# <a name="verify-max-worker-threads-setting"></a>Проверка параметра максимального числа рабочих потоков
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет возможные неверные значения параметра сервера «max worker threads». Установка низкого значения параметра «max worker threads» может привести к так называемой «нехватке потоков», необходимых для своевременного обслуживания входящих клиентских запросов. Однако слишком большое значение может вызвать неэффективное расходование адресного пространства, поскольку каждому активному потоку требуется до 4 МБ на 64-разрядном сервере.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Выберите для параметра NIB max worker threads значение 0. Это позволит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определить нужное число активных рабочих потоков для пользовательских запросов.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Настройка параметра конфигурации сервера max worker threads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
