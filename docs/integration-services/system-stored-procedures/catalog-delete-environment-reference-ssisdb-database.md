---
description: catalog.delete_environment_reference (база данных SSISDB)
title: catalog.delete_environment_reference (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 1f68f157-c4e9-412c-92b3-53a2faaba29b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ec190a40b71b874d2b888adff31ad99a41db1f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456926"
---
# <a name="catalogdelete_environment_reference-ssisdb-database"></a>catalog.delete_environment_reference (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Удаляет ссылку на среду из проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.delete_environment_reference [ @reference_id = ] reference_id  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @reference_id = ] *reference_id*  
 Уникальный идентификатор ссылки на среду. Параметр *reference_id* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   разрешение MODIFY для проекта  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Идентификатор ссылки на среду недопустим  
  
-   Пользователь не имеет соответствующих разрешений  
  
  
