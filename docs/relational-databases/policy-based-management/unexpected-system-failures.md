---
title: "Непредвиденные сбои системы | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: performance-monitor
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ddbf332d1e3868450f42ba37cafbe6c4da8bc355
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="unexpected-system-failures"></a>Непредвиденные сбои системы
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Это правило проверяет журнал событий компьютера на наличие системного события 6008. Это событие указывает на непредвиденное завершение работы системы. Система может быть нестабильна и тем самым не обеспечивать устойчивость и целостность, необходимые для размещения экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Немедленно устраните причину непредвиденных перезагрузок сервера или переместите экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на другой компьютер.  
  
  
