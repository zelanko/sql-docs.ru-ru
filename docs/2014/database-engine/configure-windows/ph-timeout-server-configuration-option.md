---
title: Параметр конфигурации сервера "ph timeout" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 25a89c00466cf4a702202f6a6fb4959f1d845c41
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62781342"
---
# <a name="ph-timeout-server-configuration-option"></a>Параметр конфигурации сервера «ph timeout»
  С помощью параметра PH timeout можно задать время в секундах, в течение которого полнотекстовый обработчик протокола будет ожидать подключения к базе данных. Значение по умолчанию — 60 секунд. Увеличьте значение ph timeout, если попытки соединения оканчиваются неудачей из-за истечения времени ожидания, например при временных сбоях в сети.  
  
 Полнотекстовой обработчик протокола находится в узле управляющей программы фильтрации и используется для выборки из SQL Server данных, для которых будет создан полнотекстовый индекс. Дополнительные сведения о компонентах полнотекстового поиска см. в разделе [Компонент Full-text Search](../../relational-databases/search/full-text-search.md).  
  
 При попытке выборки строки данных, если обработчик протокола не смог подключиться к SQL Server в течение заданного времени, он выводит ошибку времени ожидания для этой строки. Полнотекстовое средство сбора данных попытается повторно обработать строку позднее. Дополнительные сведения о полнотекстовом средстве сбора данных см. в разделе [Заполнение полнотекстовых индексов](../../relational-databases/indexes/indexes.md).  
  
## <a name="see-also"></a>См. также  
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
