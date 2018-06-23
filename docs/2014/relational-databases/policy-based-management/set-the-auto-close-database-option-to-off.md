---
title: Задание значения OFF для параметра базы данных AUTO_CLOSE | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: e6b03364-263a-4ec4-9794-de9869d396ce
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 88bd1025b928837d68aef3be0b5e4d1fbceb17a2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191408"
---
# <a name="set-the-autoclose-database-option-to-off"></a>Задание значения OFF для параметра базы данных AUTO_CLOSE
  Это правило проверяет, имеет ли параметр AUTO_ CLOSE значение OFF. Если параметр AUTO_CLOSE имеет значение ON, это может привести к снижению производительности баз данных, к которым часто выполняются обращения, из-за увеличения издержек на открытие и закрытие базы данных после каждого соединения. Параметр AUTO_CLOSE также очищает кэш процедур после каждого соединения.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 При частом обращении к базе данных присвойте параметру AUTO_CLOSE базы данных значение OFF.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметры ALTER DATABASE SET &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
