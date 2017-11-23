---
title: "sys.pdw_diag_sessions (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
ms.assetid: 4d23688a-cddb-4eed-8231-ecde2a0b0e65
caps.latest.revision: "7"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8f9a5a3a19e840c37661b0db95fe5141824e267a
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="syspdwdiagsessions-transact-sql"></a>sys.pdw_diag_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  Содержит сведения о различных диагностических сеансов, которые были созданы в системе.  
  
|Имя столбца|Тип данных|Description|Диапазон|  
|-----------------|---------------|-----------------|-----------|  
|**name**|**nvarchar(255)**|Имя сеанса диагностики.<br /><br /> Ключ для этого представления.||  
|**xml_data**|**nvarchar(4000)**|Полезные данные XML, описывающий сеанса.||  
|**is_active**|**bit**|Флаг, указывающий, активен ли флаг.||  
|**host_address**|**nvarchar(255)**|Адрес компьютера, размещение определение сеанса (узел элемента управления).||  
|**principal_id**|**int**|Идентификатор пользователя, создавшего сеанс на уровне базы данных.||  
|**database_id**|**int**|Идентификатор базы данных, которая является областью сеанса диагностики.|  
  
## <a name="see-also"></a>См. также:  
 [Хранилище данных SQL и представления каталога хранилища параллельных данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
