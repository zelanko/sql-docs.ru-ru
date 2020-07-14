---
title: Параметр конфигурации сервера "ft notify bandwidth" | Документы Майкрософт
description: Описание параметра ft notify bandwidth. Сведения о том, как он влияет на количество буферов, размещаемых SQL Server в пуле малых буферов памяти.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: cb6bf13a1f8e71f419350946d156f2504274b6d0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85772464"
---
# <a name="ft-notify-bandwidth-server-configuration-option"></a>Параметр конфигурации сервера «ft notify bandwidth»
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Используйте параметр **ft notify bandwidth** для указания предельного размера роста пула малых буферов памяти. Малые буферы памяти занимают 64 килобайта (KБ). Значение параметра *max* указывает максимальное количество буферов для управления диспетчером полнотекстовой памяти в малом буферном пуле. Если значение **max** равно нулю, значит, верхнего предела для количества буферов в малом буферном пуле нет.  
  
 Параметр **min** указывает минимальное количество пулов буферов для малого пула буферов памяти. По запросу диспетчера памяти [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] все дополнительные буферные пулы будут освобождены, однако это минимальное количество буферов сохранится. Однако если указанное значение **min** равно нулю, то будут освобождены все буфера памяти.  
  
 В определенных обстоятельствах количество буферов, распределенных в настоящий момент, может быть меньше значения, указанного параметром **min** .  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Параметр конфигурации сервера "ft crawl bandwidth"](../../database-engine/configure-windows/ft-crawl-bandwidth-server-configuration-option.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
