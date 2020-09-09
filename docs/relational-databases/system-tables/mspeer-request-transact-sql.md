---
description: MSpeer_request (Transact-SQL)
title: MSpeer_request (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSpeer_request
- MSpeer_request_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSpeer_request system table
ms.assetid: ed048c46-7a2f-4ad0-bc7c-c2d65e83b4fb
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 5b4c0352e9e0b0fab04be0dbbc1ff2a62d691c48
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89545596"
---
# <a name="mspeer_request-transact-sql"></a>MSpeer_request (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица MSpeer_request используется в одноранговой репликации для отслеживания состояния запросов для данной публикации. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|идентификатор|**int**|Идентификатор запроса.|  
|публикация|**sysname**|Имя публикации, для которой был инициирован запрос состояния.|  
|sent_date|**datetime**|Дата и время инициализации запроса состояния.|  
|description|**nvarchar(4000)**|Определяемые пользователем данные, которые могут использоваться для идентификации отдельных запросов состояния.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
