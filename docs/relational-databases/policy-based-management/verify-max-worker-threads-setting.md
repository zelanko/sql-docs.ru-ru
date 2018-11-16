---
title: Проверка параметра максимального числа рабочих потоков | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 2d94adfd-3ba1-493a-b29a-b436f9d583df
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 8389f139a979393ad27eac957f696c607c300606
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51511949"
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
  
  
