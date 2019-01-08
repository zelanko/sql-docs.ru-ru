---
title: Задание значения OFF для параметра базы данных AUTO_CLOSE | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a4353653f4a39a3e7b6dca0a22e8de358ce65c08
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52762026"
---
# <a name="set-the-autoclose-database-option-to-off"></a>Задание значения OFF для параметра базы данных AUTO_CLOSE
  Это правило проверяет, имеет ли параметр AUTO_ CLOSE значение OFF. Если параметр AUTO_CLOSE имеет значение ON, это может привести к снижению производительности баз данных, к которым часто выполняются обращения, из-за увеличения издержек на открытие и закрытие базы данных после каждого соединения. Параметр AUTO_CLOSE также очищает кэш процедур после каждого соединения.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 При частом обращении к базе данных присвойте параметру AUTO_CLOSE базы данных значение OFF.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
