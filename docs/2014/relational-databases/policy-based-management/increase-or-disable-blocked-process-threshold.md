---
title: Увеличение или отключение порога заблокированных процессов | Документация Майкрософт
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
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 73ad11cc25186b1516634190a1ade3f591d16800
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109916"
---
# <a name="increase-or-disable-blocked-process-threshold"></a>Увеличение или отключение порога заблокированных процессов
  Это правило проверяет, имеет ли параметр «blocked process threshold» значение 0 (отключен) или значение, большее или равное 5 (секундам). Присвоение параметру «blocked process threshold» значения от 1 до 4 может привести к постоянной работе монитора взаимоблокировок. Эти значения следует использовать только для устранения неполадок. Их нельзя устанавливать на долгое время или в рабочей среде без участия представителей службы поддержки пользователей [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
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
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  