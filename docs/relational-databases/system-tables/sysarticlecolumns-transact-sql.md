---
description: sysarticlecolumns (Transact-SQL)
title: Системное представление sysarticlecolumns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns system table
ms.assetid: 55918592-e05d-43b6-843b-7e4d82fa6275
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 142ed0bfaad34607422b69929450ae9f7b09bd9e
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89540234"
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Таблица **системное представление sysarticlecolumns** содержит по одной строке для каждого столбца таблицы, опубликованного в публикации моментальных снимков или транзакций, и сопоставляет каждый столбец с его статьей. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Определяет статью.|  
|**идентификатора столбца**|**smallint**|Идентифицирует столбец в статье.|  
|**is_udt**|**bit**|Указывает, принадлежит ли столбец к пользовательскому типу данных (UDT). Значение **1** указывает на столбец определяемого пользователем типа.|  
|**is_xml**|**bit**|Указывает, является ли столбец **XML-** столбцом. Значение **1** указывает на XML-столбец.|  
|**is_max**|**bit**|Указывает, является ли столбец столбцом типа данных больших значений, **varchar (max)**, **nvarchar (max)** и **varbinary (max)**. Значение **1** указывает на столбец с большим значением.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;&#41;Transact-SQL ](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
