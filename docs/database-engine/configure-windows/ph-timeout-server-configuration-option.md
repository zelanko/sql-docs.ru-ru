---
title: Параметр конфигурации сервера "ph timeout" | Документы Майкрософт
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
- time limit for protocol handler wait [SQL Server]
- timeout options [SQL Server], ph timeout option
- protocols [SQL Server], timing out
- ph timeout option
ms.assetid: ed19a07c-83fe-4582-9c9e-41b1ce571850
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d918c816bc4a4053435fcd5d71f94c09f9c4ace
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67997923"
---
# <a name="ph-timeout-server-configuration-option"></a>Параметр конфигурации сервера «ph timeout»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  С помощью параметра PH timeout можно задать время в секундах, в течение которого полнотекстовый обработчик протокола будет ожидать подключения к базе данных. Значение по умолчанию составляет 60 секунд. Увеличьте значение ph timeout, если попытки соединения оканчиваются неудачей из-за истечения времени ожидания, например при временных сбоях в сети.  
  
 Полнотекстовой обработчик протокола находится в узле управляющей программы фильтрации и используется для выборки из SQL Server данных, для которых будет создан полнотекстовый индекс. Дополнительные сведения о компонентах полнотекстового поиска см. в разделе [Компонент Full-text Search](../../relational-databases/search/full-text-search.md).  
  
 При попытке выборки строки данных, если обработчик протокола не смог подключиться к SQL Server в течение заданного времени, он выводит ошибку времени ожидания для этой строки. Полнотекстовое средство сбора данных попытается повторно обработать строку позднее. Дополнительные сведения о полнотекстовом средстве сбора данных см. в разделе [Заполнение полнотекстовых индексов](../../relational-databases/search/populate-full-text-indexes.md).  
  
## <a name="see-also"></a>См. также:  
 [Компонент Full-text Search](../../relational-databases/search/full-text-search.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  
