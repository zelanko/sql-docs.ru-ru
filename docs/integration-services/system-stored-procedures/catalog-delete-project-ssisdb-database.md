---
title: "Catalog.delete_project (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: f3431445-8dd2-443b-813e-b99db893977e
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: abc0280a693be8e0f9fa9b3ec997c1d38d96ed54
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogdeleteproject-ssisdb-database"></a>catalog.delete_project (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Удаляет существующий проект из папки в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.delete_project [ @folder_name = ] folder_name , [ @project_name = ] project_name  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки, которая содержит проект. *имя_папки* — **nvarchar(128)**.  
  
 [ @project_name =] *project_name*  
 Имя удаляемого проекта. *имя_проекта* — **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Ниже приводятся некоторые условия, которые могут вызвать delete_project хранимой процедура возвращает ошибку.  
  
-   Проект не существует  
  
-   Папка не существует  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Замечания  
 Все объекты и ссылки на среду удаляются вместе с соответствующим проектом. Однако, версии проекта и значимые записи об операциях сохраняются до следующего запуска задания очистки операций.  
  
  

