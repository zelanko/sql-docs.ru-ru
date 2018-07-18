---
title: Проверка параметра максимального числа рабочих потоков | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
caps.latest.revision: 15
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e883e16aed0a8745235fa3779c3b1a984f041c36
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37270700"
---
# <a name="verify-max-worker-threads-setting"></a>Проверка параметра максимального числа рабочих потоков
  Это правило проверяет возможные неверные значения параметра сервера «max worker threads». Установка низкого значения параметра «max worker threads» может привести к так называемой «нехватке потоков», необходимых для своевременного обслуживания входящих клиентских запросов. Однако слишком большое значение может вызвать неэффективное расходование адресного пространства, поскольку каждому активному потоку требуется 512 КБ на 32-разрядном сервере и до 4 МБ на 64-разрядном сервере.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Выберите для параметра NIB max worker threads значение 0. Это позволит [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] автоматически определить нужное число активных рабочих потоков для пользовательских запросов.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Настройка параметра конфигурации сервера max worker threads](../../database-engine/configure-windows/configure-the-max-worker-threads-server-configuration-option.md)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
