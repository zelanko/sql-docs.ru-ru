---
title: sys.pdw_diag_sessions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: bd48648719e04ca1eec15c4594b08cc1d40505b9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/11/2019
ms.locfileid: "56028635"
---
# <a name="syspdwdiagsessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о различных диагностических сеансов, которые были созданы в системе.  
  
|Имя столбца|Тип данных|Описание|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Имя сеанса диагностики.<br /><br /> Ключ для этого представления.||  
|**xml_data**|**nvarchar(4000)**|Полезные данные XML, описывающий сеанса.||  
|**is_active**|**bit**|Флаг, указывающий, активен ли флаг.||  
|**host_address**|**nvarchar(255)**|Адрес компьютере, где размещается определение сеанса (управляющий узел).||  
|**principal_id**|**int**|Идентификатор пользователя, создавшего сеанс на уровне базы данных.||  
|**database_id**|**int**|Идентификатор базы данных, который является областью сеанса диагностики.|  
  
## <a name="see-also"></a>См. также  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
