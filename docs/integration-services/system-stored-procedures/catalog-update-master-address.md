---
title: catalog.update_master_address (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
author: haoqian
ms.author: haoqian
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: a400275aa68d9906ad16ae7d1236b019f4e9f6ad
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86912750"
---
# <a name="catalogupdate_master_address-ssisdb-database"></a>catalog.update_master_address (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE[sqlserver2017](../../includes/applies-to-version/sqlserver2017.md)]

Обновите главную конечную точку развертывания [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с горизонтальным увеличением масштаба.

## <a name="syntax"></a>Синтаксис

```sql
catalog.update_master_address [ @MasterAddress = ] masterAddress
```

## <a name="arguments"></a>Аргументы
[ @MasterAddress = ] *masterAddress*  
Главная конечная точка развертывания с горизонтальным увеличением масштаба. Параметр *masterAddress* имеет тип **nvarchar**.  

 ## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
   
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
 
