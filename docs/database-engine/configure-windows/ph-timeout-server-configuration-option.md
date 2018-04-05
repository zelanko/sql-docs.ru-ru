---
title: Параметр конфигурации сервера "ph timeout" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: ''
ms.component: configure-windows
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9e99b38210816277160ab4f0991318dc7f3f266a
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="ph-timeout-server-configuration-option"></a>Параметр конфигурации сервера «ph timeout»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  С помощью параметра PH timeout можно задать время в секундах, в течение которого полнотекстовый обработчик протокола будет ожидать подключения к базе данных. Значение по умолчанию — 60 секунд. Увеличьте значение ph timeout, если попытки соединения оканчиваются неудачей из-за истечения времени ожидания, например при временных сбоях в сети.  
  
 Полнотекстовой обработчик протокола находится в узле управляющей программы фильтрации и используется для выборки из SQL Server данных, для которых будет создан полнотекстовый индекс. Дополнительные сведения о компонентах полнотекстового поиска см. в разделе [Компонент Full-text Search](../../relational-databases/search/full-text-search.md).  
  
 При попытке выборки строки данных, если обработчик протокола не смог подключиться к SQL Server в течение заданного времени, он выводит ошибку времени ожидания для этой строки. Полнотекстовое средство сбора данных попытается повторно обработать строку позднее. Дополнительные сведения о полнотекстовом средстве сбора данных см. в разделе [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md).  
  
## <a name="see-also"></a>См. также:  
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
