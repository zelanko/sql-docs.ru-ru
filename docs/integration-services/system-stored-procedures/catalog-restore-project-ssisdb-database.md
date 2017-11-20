---
title: "Catalog.restore_project (база данных SSISDB) | Документы Microsoft"
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
ms.assetid: 8adee525-579b-4d2f-b807-e2ecc07fb2e9
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 23074fc664591411666315036e3493e1b7b26134
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrestoreproject-ssisdb-database"></a>catalog.restore_project (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Восстанавливает проект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с переходом к предыдущей версии.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.restore_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project _name  
    , [ @object_version_lsn = ] object_version_lsn  
  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки, которая содержит проект. *Имя_папки* — **nvarchar(128)**.  
  
 [ @project _name =] *project_name*  
 Имя проекта. *Project_name* — **nvarchar(128)**.  
  
 [ @object_version_lsn =] *object_version_lsn*  
 Версия проекта. *Object_version_lsn* — **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Сведения о проекте, возвращаются в виде **varbinary(MAX)** как часть результирующий набор, если *project_name* найден.  
  
 **Нет РЕЗУЛЬТИРУЮЩИЙ НАБОР** возвращается, если проект невозможно восстановить в указанную папку.  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Версия проекта не существует или не соответствует имени проекта  
  
-   Проект не существует  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Замечания  
 Когда восстанавливается проект, всем параметрам присваиваются значения по умолчанию, а все ссылки на среды остаются без изменения. Максимальное количество версий проекта, которые сохраняются в каталоге определяется свойством каталога **MAX_VERSIONS_PER_PROJECT**, как показано в [catalog_property](../../integration-services/system-views/catalog-catalog-properties-ssisdb-database.md) представления.  
  
> [!WARNING]  
>  После восстановления проекта ссылки на среду могут стать недействительными.  
  
  

