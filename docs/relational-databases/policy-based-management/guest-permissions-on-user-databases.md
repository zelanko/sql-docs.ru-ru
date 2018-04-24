---
title: Разрешения гостя для пользовательских баз данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
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
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3f60f2892375b18623924a0dcefe57f18d66b8a8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="guest-permissions-on-user-databases"></a>Разрешения гостя для пользовательских баз данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило определяет, имеет ли пользователь «Гость» разрешение на доступ к базе данных. Это правило применяется только к пользовательским базам данных.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Отмените разрешения гостя для доступа к базе данных, если оно не требуется.  
  
 Пользователь guest не может быть удален, однако пользователь guest может быть отключен путем отмены его разрешения на CONNECT с помощью инструкции REVOKE CONNECT FROM GUEST в базе данных, отличной от master, tempdb или msdb.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Обеспечение безопасности SQL Server](../../relational-databases/security/securing-sql-server.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
