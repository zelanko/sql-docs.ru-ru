---
title: Параметр конфигурации сервера "ft notify bandwidth" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 375e7c8a1bb520f5a3004c5279682d5b3f145b13
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62782499"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>Параметр конфигурации сервера «ft notify bandwidth»
  Используйте параметр **ft notify bandwidth** для указания предельного размера роста пула малых буферов памяти. Малые буферы памяти занимают 64 килобайта (KБ). Значение параметра *max* указывает максимальное количество буферов для управления диспетчером полнотекстовой памяти в малом буферном пуле. Если `max` значение равно нулю, верхний предел числа буферов, которые могут находиться в небольшом буферном пуле, отсутствует.  
  
 Параметр **min** указывает минимальное количество пулов буферов для малого пула буферов памяти. По запросу [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] диспетчера памяти все дополнительные буферные пулы будут освобождены, но будет поддерживаться это минимальное количество буферов. Однако если указанное значение **min** равно нулю, то будут освобождены все буфера памяти.  
  
 При определенных обстоятельствах количество буферов, выделенных в настоящий момент, меньше, чем значение, заданное параметром **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [Параметр конфигурации сервера «пропускная способность для ft-сканирования»](ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
