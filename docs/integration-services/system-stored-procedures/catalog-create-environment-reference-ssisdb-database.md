---
title: "catalog.create_environment_reference (база данных SSISDB) | Документы Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
caps.latest.revision: "19"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 22f4ff117ea95ffa394afcd230348c4ab0f525d1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="catalogcreateenvironmentreference-ssisdb-database"></a>catalog.create_environment_reference (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

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
 [ @folder_name = ] *folder_name*  
 Имя папки проекта, которая ссылается на среду. Параметр *folder_name* имеет тип **nvarchar(128)**.  
  
 [ @project_name = ] *project_name*  
 Имя проекта, ссылающегося на среду. Параметр *project_name* имеет тип **nvarchar(128)**.  
  
 [ @environment_name = ] *environment_name*  
 Имя среды, на которую указывает ссылка. Параметр *environment_name* имеет тип **nvarchar(128)**.  
  
 [ @reference_location = ] *reference_location*  
 Указывает, может среда находиться в той же папке, что и проект (относительная ссылка), или в другой папке (абсолютная ссылка). Значение `R` указывает, что ссылка относительная. Значение `A` указывает, что ссылка абсолютная. Параметр *reference_location* имеет тип **char(1)**.  
  
 [ @environment_folder_name = ] *environment_folder_name*  
 Имя папки, в которой находится среда, на которую указывает ссылка. Это значение требуется для абсолютных ссылок. Параметр *environment_folder_name* имеет тип **nvarchar(128)**.  
  
 [ @reference_id = ] *reference_id*  
 Возвращает уникальный идентификатор для новой ссылки. Этот параметр является необязательным. Параметр *reference_id* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проект и разрешение READ на среду  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Недопустимое имя папки  
  
-   Недопустимое имя проекта  
  
-   Пользователь не имеет соответствующих разрешений.  
  
-   Задана абсолютная ссылка с помощью символа `A` в параметре *reference_location*, но имя папки в параметре *environment_folder_name* не указано.  
  
## <a name="remarks"></a>Замечания  
 Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени и требуют, чтобы она находилась в той же папке, что и проект. Абсолютные ссылки указывают среду с применением имени и папки и могут указывать среды, находящиеся в иной папке, чем проект. Проект может ссылаться на несколько сред.  
  
  
