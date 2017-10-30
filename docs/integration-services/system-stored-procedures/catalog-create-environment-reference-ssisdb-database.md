---
title: "Catalog.create_environment_reference (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 496136e8a0073ba93f003d8dfa539afb48d2c5dc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreateenvironmentreference-ssisdb-database"></a>catalog.create_environment_reference (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Создает ссылку на среду для проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_environment_reference [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @environment_name = ] environment_name  
     , [ @reference_location = ] reference_location  
  [  , [ @environment_folder_name = ] environment_folder_name ]  
  [  , [ @reference_id = ] reference_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки проекта, которая ссылается на среду. *Имя_папки* — **nvarchar(128)**.  
  
 [ @project_name =] *project_name*  
 Имя проекта, ссылающегося на среду. *Project_name* — **nvarchar(128)**.  
  
 [ @environment_name =] *environment_name*  
 Имя среды, на которую указывает ссылка. *Environment_name* — **nvarchar(128)**.  
  
 [ @reference_location =] *reference_location*  
 Указывает, может среда находиться в той же папке, что и проект (относительная ссылка), или в другой папке (абсолютная ссылка). Значение `R` указывает, что ссылка относительная. Значение `A` указывает, что ссылка абсолютная. *Reference_location* — **char(1)**.  
  
 [ @environment_folder_name =] *environment_folder_name*  
 Имя папки, в которой находится среда, на которую указывает ссылка. Это значение требуется для абсолютных ссылок. *Environment_folder_name* — **nvarchar(128)**.  
  
 [ @reference_id =] *reference_id*  
 Возвращает уникальный идентификатор для новой ссылки. Этот параметр является необязательным. *Reference_id* — **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проект и разрешение READ на среду  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Недопустимое имя папки  
  
-   Недопустимое имя проекта  
  
-   Пользователь не имеет соответствующих разрешений.  
  
-   Абсолютная ссылка задается с помощью `A` знаку в *reference_location* параметра, но имя папки не указан с *environment_folder_name* параметр.  
  
## <a name="remarks"></a>Замечания  
 Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени и требуют, чтобы она находилась в той же папке, что и проект. Абсолютные ссылки указывают среду с применением имени и папки и могут указывать среды, находящиеся в иной папке, чем проект. Проект может ссылаться на несколько сред.  
  
  

