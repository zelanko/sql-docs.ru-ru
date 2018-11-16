---
title: Задание значения OFF для параметра базы данных AUTO_SHRINK | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 16403850-d745-4754-b84f-5f01aaecd24e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c48e0671052d612a52703aa7d367e03257cf1e14
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51667343"
---
# <a name="set-the-autoshrink-database-option-to-off"></a>Задание значения параметра базы данных AUTO_SHRINK, равного OFF
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет, имеет ли параметр базы данных AUTO_SHRINK значение OFF. Нередко сжатие и расширение базы данных ведет к физической фрагментации.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Присвойте параметру базы данных AUTO_SHRINK значение OFF. Если известно, что освобождаемое место не понадобится в будущем, можно освободить это место, выполнив сжатие базы данных вручную.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 Статья [315512](https://go.microsoft.com/fwlink/?linkid=117750)базы знаний Майкрософт  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
