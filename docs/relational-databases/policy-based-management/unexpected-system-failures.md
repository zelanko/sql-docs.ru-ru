---
title: Непредвиденные сбои системы | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 8fb34965fe6392ac09b2582f5d840f0da90294d5
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68021468"
---
# <a name="unexpected-system-failures"></a>Непредвиденные сбои системы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет журнал событий компьютера на событие SYSTEM Event 6008. Это событие указывает на непредвиденное завершение работы системы. Система может быть нестабильна и тем самым не обеспечивать устойчивость и целостность, необходимые для размещения экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Немедленно устраните причину непредвиденных перезагрузок сервера или переместите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другой компьютер.  
  
  
