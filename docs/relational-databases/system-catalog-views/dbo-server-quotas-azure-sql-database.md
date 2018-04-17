---
title: dbo.server_quotas (база данных SQL Azure) | Документы Microsoft
ms.custom: ''
ms.date: 08/02/2016
ms.prod: ''
ms.reviewer: ''
ms.suite: sql
ms.prod_service: sql-database
ms.service: sql-database
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.server_quotas
- dbo.server_quotas_TSQL
- server_quotas
- server_quotas_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server_quotas
ms.assetid: 34423903-1aaa-4a55-88a6-8228315d84e7
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
monikerRange: = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 66f6e2c1cae1b8743314a8a9ff844040e1f91f35
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="dboserverquotas-azure-sql-database"></a>dbo.server_quotas (база данных SQL Azure)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> **ВАЖНО!** Это относится к  **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]только V11!**  
>   
>  Этот компонент доступен в состоянии предварительной версии. Не полагайтесь на конкретную реализацию этого компонента, так как он может быть изменен или удален в следующей версии.  
  
 Возвращает типы квот баз данных, доступных на сервере.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|quota_name|**nvarchar**|Тип квоты для сервера. Тип **Premium_database** эквивалентны базам данных с резервированием ресурса.|  
|quota_value|**int**|Количество типов квот, допустимое на сервере.|  
  
## <a name="permissions"></a>Разрешения  
 Это представление доступно для всех ролей пользователей с разрешениями на подключение к виртуальной **master** базы данных.  
  
## <a name="see-also"></a>См. также  
 [Управление расширенными базами данных](http://go.microsoft.com/fwlink/?LinkID=311927)  
  
  
