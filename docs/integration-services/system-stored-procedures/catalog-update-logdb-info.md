---
description: catalog.update_logdb_info (база данных SSISDB)
title: catalog.update_logdb_info (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
author: haoqian
ms.author: haoqian
monikerRange: '>= sql-server-2017'
ms.openlocfilehash: 3dbfe1b83132998d946e7b7d192be40fdf4f2856
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97465695"
---
# <a name="catalogupdate_logdb_info-ssisdb-database"></a>catalog.update_logdb_info (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE[sqlserver2017](../../includes/applies-to-version/sqlserver2017.md)]

Обновление сведений о ведении журнала [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] Scale Out.

## <a name="syntax"></a>Синтаксис

```sql
catalog.update_logdb_info [ @server_name = ] server_name, [ @connection_string = ] connection_string
```

## <a name="arguments"></a>Аргументы
[ @server_name = ] *server_name*  
 SQL Server, используемый для ведения журнала Scale Out. Параметр *server_name* имеет тип **nvarchar**.  

 [ @connection_string = ] *connection_string*  
 Строка подключения, используемая для ведения журнала Scale Out. Параметр *connection_string* имеет тип **nvarchar**.

 ## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  

## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
   
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
 
