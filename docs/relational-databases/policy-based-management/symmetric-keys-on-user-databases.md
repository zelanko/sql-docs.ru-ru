---
title: Симметричные ключи в пользовательских базах данных | Документация Майкрософт
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
ms.assetid: 3333ab5b-2518-4753-a0a8-57df5e5af74f
caps.latest.revision: 6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: be15cf6291d6cdeefe64f6dc6be77fe604dde30d
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="symmetric-keys-on-user-databases"></a>Симметричные ключи в пользовательских базах данных
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет, используют ли симметричные ключи длиной менее 128 бит алгоритмы шифрования RC2 или RC4.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 При создании симметричных ключей для шифрования данных используйте 128-битный алгоритм AES. Если алгоритм AES не поддерживается в операционной системе, следует применять алгоритм 3DES.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Выбор алгоритма шифрования](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
