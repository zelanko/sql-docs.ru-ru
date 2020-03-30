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
ms.openlocfilehash: d9373bcb994614a1726801c6cd8c85a9bc46bced
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "68038572"
---
# <a name="catalogupdate_master_address-ssisdb-database"></a>catalog.update_master_address (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Обновите главную конечную точку развертывания [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с горизонтальным увеличением масштаба.

## <a name="syntax"></a>Синтаксис

```sql
catalog.update_master_address [@MasterAddress = ] masterAddress
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
 
