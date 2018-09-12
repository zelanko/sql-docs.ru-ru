---
title: Увеличение или отключение порога заблокированных процессов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 71db8ef6-341b-4465-99db-5c63e48d4c7d
caps.latest.revision: 8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6a4a515a584a0141e08736ee4190187ea70ac8ff
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43806660"
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
  
  
