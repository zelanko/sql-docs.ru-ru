---
title: Настройка параметров сбора данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: data-collection
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f49cfcfef48c7f652ca6a5f05a7c49a97efe38fc
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="configure-data-collection-parameters-transact-sql"></a>Настройка параметров сбора данных (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Перед созданием пользовательского набора сбора необходимо настроить параметры сбора данных. Это делается с помощью хранимых процедур, предоставляемых со сборщиком данных. Эта задача решается с помощью редактора запросов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] для выполнения следующей процедуры.  
  
> [!NOTE]  
>  Параметры сбора данных можно настроить только один раз. После настройки эти параметры будут использоваться для всех создаваемых дополнительных наборов сбора.  
  
### <a name="configure-data-collection-parameters"></a>Настройка параметров сбора данных  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]подключитесь к базе данных, в которой будет создан пользовательский набор сбора.  
  
2.  В редакторе запросов выполните следующие инструкции.  
  
    ```sql  
    USE msdb;  
    EXEC sp_syscollector_set_warehouse_instance_name N'INSTANCE_NAME';-- where instance name is the name of the SQL Server instance  
    EXEC sp_syscollector_set_warehouse_database_name N'MDW';  
    EXEC sp_syscollector_set_cache_directory N'D:\tempdata';  
    ```  
  
## <a name="see-also"></a>См. также:  
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
