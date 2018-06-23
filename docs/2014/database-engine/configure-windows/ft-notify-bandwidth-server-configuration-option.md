---
title: Параметр конфигурации сервера "ft notify bandwidth" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- ft notify bandwidth opion
- small memory buffers
- memory [SQL Server], buffers
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
caps.latest.revision: 19
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ea5b6663c2d2b599fa4f0ec3abd1b003fcc1c17c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36180112"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>Параметр конфигурации сервера «ft notify bandwidth»
  Используйте параметр **ft notify bandwidth** для указания предельного размера роста пула малых буферов памяти. Малые буферы памяти занимают 64 килобайта (KБ). Значение параметра *max* указывает максимальное количество буферов для управления диспетчером полнотекстовой памяти в малом буферном пуле. Если `max` значение равно нулю, то нет верхнего предела на число буферов в малом буферном пуле.  
  
 Параметр **min** указывает минимальное количество пулов буферов для малого пула буферов памяти. По запросу диспетчера памяти [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все дополнительные буферные пулы будут освобождены, однако это минимальное количество буферов сохранится. Однако если указанное значение **min** равно нулю, то будут освобождены все буфера памяти.  
  
 В определенных обстоятельствах количество буферов, распределенных в настоящий момент, может быть меньше значения, указанного параметром **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [Параметр конфигурации сервера "ft crawl bandwidth"](ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
