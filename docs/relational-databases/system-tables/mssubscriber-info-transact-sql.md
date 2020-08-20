---
description: MSsubscriber_info (Transact-SQL)
title: MSsubscriber_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscriber_info_TSQL
- MSsubscriber_info
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscriber_info system table
ms.assetid: 5ca22f41-6020-4f72-8110-e69baf3447cb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 5b807bcb3595a20bcce849b6526e9729c960d5bc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88480751"
---
# <a name="mssubscriber_info-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **MSsubscriber_info** содержит по одной строке для каждой пары "издатель-подписчик", которая принудительно отправила подписки от локального распространителя. Эта таблица хранится в базе данных распространителя.  
  
 **Примечание** . Эта системная таблица устарела и поддерживается для поддержки предыдущих версий [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|Имя издателя.|  
|**абонент**|**sysname**|Имя подписчика.|  
|**type**|**tinyint**|Тип подписчика:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчика.<br /><br /> **1** = источник данных ODBC.|  
|**пользователей**|**sysname**|Имя входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Хранится в зашифрованном формате, если подписчик добавляется в режиме проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**password**|**nvarchar (524)**|Пароль для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Хранится в зашифрованном формате, если подписчик добавляется в режиме проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**description**|**nvarchar(255)**|Описание подписчика.|  
|**security_mode**|**int**|Реализованный режим безопасности:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Проверка подлинности.<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Проверка подлинности Windows.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
