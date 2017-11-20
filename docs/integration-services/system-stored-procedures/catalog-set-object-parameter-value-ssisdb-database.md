---
title: "Catalog.set_object_parameter_value (база данных SSISDB) | Документы Microsoft"
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
ms.assetid: fb887543-f92f-404d-9495-a1dd23a6716e
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 3a5dc70b1e955b3c702dc9e9dbe4776cc4ebd5ac
ms.contentlocale: ru-ru
ms.lasthandoff: 10/20/2017

---
# <a name="catalogsetobjectparametervalue-ssisdb-database"></a>catalog.set_object_parameter_value (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задает значение параметра в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Связывает значение с переменной среды или назначает литеральное значение, которое используется по умолчанию при назначении другие значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_object_parameter_value [@object_type =] object_type   
    , [@folder_name =] folder_name   
    , [@project_name =] project_name   
    , [@parameter_name =] parameter _name   
    , [@parameter_value =] parameter_value   
 [  , [@object_name =] object_name ]  
 [  , [@value_type =] value_type ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [@object_type =] *object_type*  
 Тип параметра. Значение `20` указывает параметр проекта, значение `30` — параметр пакета. *Object_type* — **smallInt**.  
  
 [@folder_name =] *имя_папки*  
 Имя папки, в которой содержится параметр. *Имя_папки* — **nvarchar(128)**.  
  
 [@project_name =] *project_name*  
 Имя проекта, в котором содержится параметр. *Project_name* — **nvarchar(128)**.  
  
 [@parameter_name =] *parameter_name*  
 Имя параметра. *Parameter_name* — **nvarchar(128)**.  
  
 [@parameter_value =] *parameter_value*  
 Значение параметра. *Parameter_value* — **sql_variant**.  
  
 [@object_name =] *object_name*  
 Имя пакета. Этот аргумент обязателен, если параметр является параметром пакета. *Object_name* — **nvarchar(260)**.  
  
 [@value_type =] *value_type*  
 Тип значения параметра. Используйте символ `V` указывает, что *parameter_value* является литеральное значение, которое используется по умолчанию, если перед выполнением назначены другие значения. Используйте символ `R` указывает, что *parameter_value* является значением, на которую указывает ссылка и ему было присвоено имя переменной среды. Этот аргумент является необязательным. По умолчанию используется символ `V`. *Value_type* — **char(1)**.  
  
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
 В следующем списке перечислены некоторые условия, при которых хранимая процедура может вызвать ошибку.  
  
-   Недопустимый тип параметра.  
  
-   Недопустимое имя проекта  
  
-   Недопустимое имя пакета для параметров пакета.  
  
-   Недопустимый тип значения.  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Замечания  
  
-   Если не *value_type* указано, литеральное значение для *parameter_value* используется по умолчанию. Если используется литеральное значение, *value_set* в [object_parameters](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md) задано представление `1`. Значение NULL недопустимо.  
  
-   Если *value_type* содержит символ `R`, которая задает значение, на которую указывает ссылка, *parameter_value* ссылается на имя переменной среды.  
  
-   Значение `20` могут быть использованы для *object_type* для обозначения параметра проекта. В этом случае значение для *object_name* не является обязательным и любое значение, указанное для *object_name* игнорируется. Это значение используется, когда пользователь хочет задать параметр проекта.  
  
-   Значение `30` могут быть использованы для *object_type* для обозначения параметра пакета. В этом случае значение для *object_name* используется для обозначения соответствующего пакета. Если *object_name* не указан, хранимая процедура возвращает ошибку и завершается.  
  
  

