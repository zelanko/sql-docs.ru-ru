---
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 45065f7cde525d65997df2c97c972d684cadd90f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139824"
---
# <a name="mssubscriber_info-transact-sql"></a>MSsubscriber_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSsubscriber_info** содержит по одной строке для каждой пары "издатель-подписчик", которая принудительно отправила подписки от локального распространителя. Эта таблица хранится в базе данных распространителя.  
  
 **Примечание** . Эта системная таблица устарела и поддерживается для поддержки предыдущих версий [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="definition"></a>Определение  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**издателя**|**имеет sysname**|Имя издателя.|  
|**абонент**|**имеет sysname**|Имя подписчика.|  
|**type**|**tinyint**|Тип подписчика:<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] подписчика.<br /><br /> **1** = источник данных ODBC.|  
|**пользователей**|**имеет sysname**|Имя входа для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Хранится в зашифрованном формате, если подписчик добавляется в режиме проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**пароль**|**nvarchar (524)**|Пароль для проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Хранится в зашифрованном формате, если подписчик добавляется в режиме проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**nописание**|**nvarchar(255)**|Описание подписчика.|  
|**security_mode**|**int**|Реализованный режим безопасности:<br /><br /> **** =  0[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверка подлинности.<br /><br /> **** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] проверка подлинности Windows.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
