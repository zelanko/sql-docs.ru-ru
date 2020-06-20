---
title: Задание значения OFF для параметра базы данных AUTO_SHRINK | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 42d79ed13a691c3d39a28e7ab35a740a9f613fac
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85066674"
---
# <a name="set-the-auto_shrink-database-option-to-off"></a>Задание значения параметра базы данных AUTO_SHRINK, равного OFF
  Это правило проверяет, имеет ли параметр базы данных AUTO_SHRINK значение OFF. Нередко сжатие и расширение базы данных ведет к физической фрагментации.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Присвойте параметру базы данных AUTO_SHRINK значение OFF. Если известно, что освобождаемое место не понадобится в будущем, можно освободить это место, выполнив сжатие базы данных вручную.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 Статья [315512](https://go.microsoft.com/fwlink/?linkid=117750)базы знаний Майкрософт  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
