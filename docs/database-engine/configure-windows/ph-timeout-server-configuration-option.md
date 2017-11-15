---
title: "Параметр конфигурации сервера \"ph timeout\" | Документы Майкрософт"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
caps.latest.revision: "28"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 118ea83ca4d3268f55a6ec1e0c6db68958dad9f4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="ph-timeout-server-configuration-option"></a>Параметр конфигурации сервера «ph timeout»
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  С помощью параметра PH timeout можно задать время в секундах, в течение которого полнотекстовый обработчик протокола будет ожидать подключения к базе данных. Значение по умолчанию — 60 секунд. Увеличьте значение ph timeout, если попытки соединения оканчиваются неудачей из-за истечения времени ожидания, например при временных сбоях в сети.  
  
 Полнотекстовой обработчик протокола находится в узле управляющей программы фильтрации и используется для выборки из SQL Server данных, для которых будет создан полнотекстовый индекс. Дополнительные сведения о компонентах полнотекстового поиска см. в разделе [Компонент Full-text Search](../../relational-databases/search/full-text-search.md).  
  
 При попытке выборки строки данных, если обработчик протокола не смог подключиться к SQL Server в течение заданного времени, он выводит ошибку времени ожидания для этой строки. Полнотекстовое средство сбора данных попытается повторно обработать строку позднее. Дополнительные сведения о полнотекстовом средстве сбора данных см. в разделе [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md).  
  
## <a name="see-also"></a>См. также:  
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
