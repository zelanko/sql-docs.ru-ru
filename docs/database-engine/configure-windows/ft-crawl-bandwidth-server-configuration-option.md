---
title: "Параметр конфигурации сервера \"ft crawl bandwidth\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: configure-windows
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
caps.latest.revision: "25"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0a5c69319c2a88bd84adaabf81f66ecfbc6cc73a
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a>Параметр конфигурации сервера «ft crawl bandwidth»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Параметр **ft crawl bandwidth** используют для того, чтобы указать размер, до которого может расти пул больших буферов памяти. Большие буферы памяти имеют размер 4 МБ. Значение параметра **max** указывает максимальное количество буферов, которое должен поддерживать диспетчер полнотекстовой памяти в большом буферном пуле. Если значение **max** нулевое, верхний предел числа буферных пулов отсутствует.  
  
 Параметр **min** указывает минимальное количество буферов памяти, которое нужно поддерживать в больших пулах буферов памяти. По запросу диспетчера памяти [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все дополнительные буферные пулы будут освобождены, однако это минимальное количество буферов сохранится. Однако если указанное значение **min** равно нулю, то будут освобождены все буфера памяти.  
  
 При некоторых обстоятельствах число выделенных в данный момент буферов может быть меньше значения, указанного в параметре **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Параметр конфигурации сервера "ft notify bandwidth"](../../database-engine/configure-windows/ft-notify-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
