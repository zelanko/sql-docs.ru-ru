---
title: Задание значения OFF для параметра базы данных AUTO_CLOSE | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 6b9fda04dd570d0077b692b86937e401bac54e42
ms.sourcegitcommit: ef6e3ec273b0521e7c79d5c2a4cb4dcba1744e67
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2018
ms.locfileid: "51512909"
---
# <a name="set-the-autoclose-database-option-to-off"></a>Задание значения OFF для параметра базы данных AUTO_CLOSE
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет, имеет ли параметр AUTO_ CLOSE значение OFF. Если параметр AUTO_CLOSE имеет значение ON, это может привести к снижению производительности баз данных, к которым часто выполняются обращения, из-за увеличения издержек на открытие и закрытие базы данных после каждого соединения. Параметр AUTO_CLOSE также очищает кэш процедур после каждого соединения.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 При частом обращении к базе данных присвойте параметру AUTO_CLOSE базы данных значение OFF.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
