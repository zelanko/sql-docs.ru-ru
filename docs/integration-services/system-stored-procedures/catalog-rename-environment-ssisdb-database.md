---
title: "Catalog.rename_environment (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: c73d7452-31c5-4f4e-afcc-e9eca760c826
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 504d3ca0f18c9ea11105ebb575d2f5db449f91e4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrenameenvironment-ssisdb-database"></a>catalog.rename_environment (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Переименовывает среду в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
rename_environment [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @new_environment_name= ] new_environment_name  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки, которая содержит среду. *Имя_папки* — **nvarchar(128)**.  
  
 [ @environment_name =] *environment_name*  
 Исходное имя среды. *Environment_name* — **nvarchar(128)**.  
  
 [ @new_environment_name =] *new_environment_name*  
 Новое имя среды. *New_environment_name* — **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения MODIFY для среды  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Недопустимое исходное имя переменной среды  
  
-   Новое имя уже использовано в существующей среде  
  
## <a name="remarks"></a>Замечания  
 Ссылки из проектов на среду не обновляются автоматически при переименовании среды. Ссылки на среду должны обновляться соответствующим образом. Хранимая процедура будет выполнена успешно, даже если вследствие изменения имени среды ссылки на нее оказались недействительными. Ссылки на среду должны обновляться после завершения этой хранимой процедуры.  
  
> [!NOTE]  
>  Проверка и исполнение пакетов, использующих недействительные ссылки на среду, завершится с ошибкой.  
  
  
