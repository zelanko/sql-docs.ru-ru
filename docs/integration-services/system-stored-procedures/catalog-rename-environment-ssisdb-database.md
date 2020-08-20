---
description: catalog.rename_environment (база данных SSISDB)
title: catalog.rename_environment (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: c73d7452-31c5-4f4e-afcc-e9eca760c826
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6641ff60f49534a303d3f60110dbdd63aab2ed29
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477156"
---
# <a name="catalogrename_environment-ssisdb-database"></a>catalog.rename_environment (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Переименовывает среду в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.rename_environment [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @new_environment_name= ] new_environment_name  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки, которая содержит среду. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [ @environment_name = ] *environment_name*  
 Исходное имя среды. Параметр *environment_name* имеет тип **nvarchar(128)** .  
  
 [ @new_environment_name = ] *new_environment_name*  
 Новое имя среды. Параметр *new_environment_name* имеет тип **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения MODIFY для среды  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Недопустимое исходное имя переменной среды  
  
-   Новое имя уже использовано в существующей среде  
  
## <a name="remarks"></a>Комментарии  
 Ссылки из проектов на среду не обновляются автоматически при переименовании среды. Ссылки на среду должны обновляться соответствующим образом. Хранимая процедура будет выполнена успешно, даже если вследствие изменения имени среды ссылки на нее оказались недействительными. Ссылки на среду должны обновляться после завершения этой хранимой процедуры.  
  
> [!NOTE]  
>  Проверка и исполнение пакетов, использующих недействительные ссылки на среду, завершится с ошибкой.  
  
  
