---
title: "Увеличение или отключение порога заблокированных процессов | Документация Майкрософт"
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
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
caps.latest.revision: "8"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 01454bfb5bf11f0ed6136bd4caca4937f198ba0b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="increase-or-disable-blocked-process-threshold"></a>Увеличение или отключение порога заблокированных процессов
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Это правило проверяет, имеет ли параметр "Порог блокированного процесса" значение 0 (отключен) или значение, большее или равное 5 (секундам). Присвоение параметру «blocked process threshold» значения от 1 до 4 может привести к постоянной работе монитора взаимоблокировок. Эти значения следует использовать только для устранения неполадок. Их нельзя устанавливать на долгое время или в рабочей среде без участия представителей службы поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Чтобы решить эту проблему, присвойте параметру «blocked process threshold» значение 5 (секунд) или больше либо отключите порог блокировки процессов, присвоив этому параметру значение 0. Чтобы присвоить параметру «blocked process threshold» значение `5` секунд, выполните следующую инструкцию:  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 5 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Параметр конфигурации сервера «blocked process threshold»](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
