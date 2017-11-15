---
title: "Проверка параметра максимального числа рабочих потоков | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
caps.latest.revision: "17"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c76c1cf549dfdba5babe5ae137f0c457a033dd5
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="verify-max-worker-threads-setting"></a>Проверка параметра максимального числа рабочих потоков
  Это правило проверяет возможные неверные значения параметра сервера «max worker threads». Установка низкого значения параметра «max worker threads» может привести к так называемой «нехватке потоков», необходимых для своевременного обслуживания входящих клиентских запросов. Однако слишком большое значение может вызвать неэффективное расходование адресного пространства, поскольку каждому активному потоку требуется до 4 МБ на 64-разрядном сервере.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Выберите для параметра NIB max worker threads значение 0. Это позволит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определить нужное число активных рабочих потоков для пользовательских запросов.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Настройка параметра конфигурации сервера max worker threads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
