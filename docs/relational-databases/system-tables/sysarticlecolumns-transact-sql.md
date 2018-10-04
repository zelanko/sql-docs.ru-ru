---
title: sysarticlecolumns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sysarticlecolumns
- sysarticlecolumns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysarticlecolumns system table
ms.assetid: 55918592-e05d-43b6-843b-7e4d82fa6275
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35046a8831d38d433e60127b983a16043e657668
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47635032"
---
# <a name="sysarticlecolumns-transact-sql"></a>sysarticlecolumns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysarticlecolumns** таблица содержит по одной строке для каждого столбца таблицы, публикуется в публикации транзакций или моментальных снимков, который сопоставляет каждый столбец с его статьей. Эта таблица хранится в базе данных публикации.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**artid**|**int**|Определяет статью.|  
|**идентификатора столбца**|**smallint**|Идентифицирует столбец в статье.|  
|**is_udt**|**bit**|Указывает, принадлежит ли столбец к пользовательскому типу данных (UDT). Значение **1** означает столбец определяемого пользователем ТИПА.|  
|**is_xml**|**bit**|Указывает, является ли столбец **xml** столбца. Значение **1** указывает XML-столбец.|  
|**is_max**|**bit**|Указывает, является ли столбец столбцом типа данных больших значений **varchar(max)**, **nvarchar(max)**, и **varbinary(max)**. Значение **1** означает столбец больших значений.|  
  
## <a name="see-also"></a>См. также  
 [Таблицы репликации &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
