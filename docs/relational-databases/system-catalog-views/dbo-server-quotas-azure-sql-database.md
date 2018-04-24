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
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 8338b6768f25f31b4b217f938357de8090b55326
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
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
  
  
