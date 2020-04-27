---
title: Параметр конфигурации сервера "ft crawl bandwidth" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- large memory buffers
- memory [SQL Server], buffers
- ft crawl bandwidth option
ms.assetid: e5864ad9-92f5-43b5-95de-46d68ded8694
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f603987608a4c6456e01efc171bc93301069f046
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62782180"
---
# <a name="ft-crawl-bandwidth-server-configuration-option"></a>Параметр конфигурации сервера «ft crawl bandwidth»
  Параметр **ft crawl bandwidth** используют для того, чтобы указать размер, до которого может расти пул больших буферов памяти. Большие буферы памяти имеют размер 4 МБ. Значение параметра **max** указывает максимальное количество буферов, которое должен поддерживать диспетчер полнотекстовой памяти в большом буферном пуле. Если значение **max** нулевое, верхний предел числа буферных пулов отсутствует.  
  
 Параметр **min** указывает минимальное количество буферов памяти, которое нужно поддерживать в больших пулах буферов памяти. По запросу диспетчера памяти [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все дополнительные буферные пулы будут освобождены, однако это минимальное количество буферов сохранится. Однако если указанное значение **min** равно нулю, то будут освобождены все буфера памяти.  
  
 При некоторых обстоятельствах число выделенных в данный момент буферов может быть меньше значения, указанного в параметре **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [Параметр конфигурации сервера "ft notify bandwidth"](ft-notify-bandwidth-server-configuration-option.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
