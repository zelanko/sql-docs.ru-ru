---
title: Настройка параметров сбора данных (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
ms.assetid: 850905b6-35d2-4ed1-ab51-de64daa832b2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b9cdabe3a74570c44eba952137d6b9efb856a731
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62918566"
---
# <a name="configure-data-collection-parameters-transact-sql"></a>Настройка параметров сбора данных (Transact-SQL)
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
 [Сбор данных](data-collection.md)   
 [Хранимые процедуры сборщика данных (Transact-SQL)](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql)  
  
  
