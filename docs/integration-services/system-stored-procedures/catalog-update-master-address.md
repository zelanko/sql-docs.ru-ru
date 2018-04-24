---
title: catalog.update_master_address (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
caps.latest.revision: 1
author: haoqian
ms.author: haoqian
manager: craigg
ms.workload: Inactive
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: ee47c3bbd6d0e8f29152ca0869b3315855180a0f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="catalogupdatemasteraddress-ssisdb-database"></a>catalog.update_master_address (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Обновите главную конечную точку [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

## <a name="syntax"></a>Синтаксис

```sql
catalog.update_master_address [@MasterAddress = ] masterAddress
```

## <a name="arguments"></a>Аргументы
[ @MasterAddress = ] *masterAddress*  
Главная конечная точка Scale Out. Параметр *masterAddress* имеет тип **nvarchar**.  

 ## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
   
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
 
