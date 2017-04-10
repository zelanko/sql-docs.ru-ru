---
title: "Параметр конфигурации сервера &#171;ft notify bandwidth&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "ft notify bandwidth, параметр"
  - "малые буферы памяти"
  - "память [SQL Server], буферы"
ms.assetid: 9ca284c5-f3e0-4a67-a132-fff376ff0ffe
caps.latest.revision: 19
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 19
---
# Параметр конфигурации сервера &#171;ft notify bandwidth&#187;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используйте параметр **ft notify bandwidth** для указания предельного размера роста пула малых буферов памяти. Малые буферы памяти занимают 64 килобайта (KБ). Значение параметра *max* указывает максимальное количество буферов для управления диспетчером полнотекстовой памяти в малом буферном пуле. Если значение **max** равно нулю, значит, верхнего предела для количества буферов в малом буферном пуле нет.  
  
 Параметр **min** указывает минимальное количество пулов буферов для малого пула буферов памяти. По запросу диспетчера памяти [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все дополнительные буферные пулы будут освобождены, однако это минимальное количество буферов сохранится. Однако если указанное значение **min** равно нулю, то будут освобождены все буфера памяти.  
  
 В определенных обстоятельствах количество буферов, распределенных в настоящий момент, может быть меньше значения, указанного параметром **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Параметр конфигурации сервера «ft crawl bandwidth»](../../database-engine/configure-windows/ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  