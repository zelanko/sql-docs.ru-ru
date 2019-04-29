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
manager: craigg
ms.openlocfilehash: 951b49c0356ae27cb58041af5186becfd12853bb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62677068"
---
# <a name="unexpected-system-failures"></a>Непредвиденные сбои системы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет журнал событий компьютера на событие SYSTEM Event 6008. Это событие указывает на непредвиденное завершение работы системы. Система может быть нестабильна и тем самым не обеспечивать устойчивость и целостность, необходимые для размещения экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Немедленно устраните причину непредвиденных перезагрузок сервера или переместите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другой компьютер.  
  
  
