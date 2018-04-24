---
title: Размер сетевого пакета не должен превышать 8060 байт | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: performance-monitor
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 86db5da1-afe4-4fbb-8bf8-33cedc7e4361
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c8dd5eae32fdb5d8984d7cf510f9b04a6ad09b51
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="network-packet-size-should-not-exceed-8060-bytes"></a>Размер сетевого пакета не должен превышать 8060 байт
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Если значение, заданное для параметра хранимой процедуры sp_configure 'network packet size', или размер пакета любого вошедшего в систему пользователя превышает 8 060 байт, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выполняет другие операции выделения памяти. Это может привести к увеличению виртуального адресного пространства процессов, которое не зарезервировано для буферного пула.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Размер сетевого пакета не должен превышать 8 060 байт.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Статья 903002 базы знаний Майкрософт](http://go.microsoft.com/fwlink/?linkid=117749)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
