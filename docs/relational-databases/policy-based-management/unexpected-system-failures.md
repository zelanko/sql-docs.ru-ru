---
title: Непредвиденные сбои системы | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 050d7dbf22965cfc3b150f4ff42e3a0e437e7e8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610362"
---
# <a name="unexpected-system-failures"></a>Непредвиденные сбои системы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет журнал событий компьютера на событие SYSTEM Event 6008. Это событие указывает на непредвиденное завершение работы системы. Система может быть нестабильна и тем самым не обеспечивать устойчивость и целостность, необходимые для размещения экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Немедленно устраните причину непредвиденных перезагрузок сервера или переместите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другой компьютер.  
  
  
