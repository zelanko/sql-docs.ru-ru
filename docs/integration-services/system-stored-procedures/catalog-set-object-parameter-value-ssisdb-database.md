---
title: catalog.set_object_parameter_value (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: fb887543-f92f-404d-9495-a1dd23a6716e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8c9263e3855fcb9617baf3d9d3d7e0a55d079316
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85674538"
---
# <a name="catalogset_object_parameter_value-ssisdb-database"></a>catalog.set_object_parameter_value (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Задает значение параметра в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Связывает значение с переменной среды или назначает литеральное значение, которое используется по умолчанию, если не назначены другие значения.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_object_parameter_value [ @object_type = ] object_type   
    , [ @folder_name = ] folder_name   
    , [ @project_name = ] project_name   
    , [ @parameter_name = ] parameter_name   
    , [ @parameter_value = ] parameter_value   
 [  , [ @object_name = ] object_name ]  
 [  , [ @value_type = ] value_type ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [@object_type =] *object_type*  
 Тип параметра. Значение `20` указывает параметр проекта, значение `30` — параметр пакета. Параметр *object_type* имеет тип **smallInt**.  
  
 [@folder_name =] *folder_name*  
 Имя папки, в которой содержится параметр. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [@project_name =] *project_name*  
 Имя проекта, в котором содержится параметр. Параметр *project_name* имеет тип **nvarchar(128)** .  
  
 [@parameter_name =] *parameter_name*  
 Имя параметра. Параметр *parameter_name* имеет тип **nvarchar(128)** .  
  
 [@parameter_value =] *parameter_value*  
 Значение параметра. Параметр *parameter_value* имеет тип **sql_variant**.  
  
 [@object_name =] *object_name*  
 Имя пакета. Этот аргумент обязателен, если параметр является параметром пакета. Параметр *object_name* имеет тип **nvarchar(260)** .  
  
 [@value_type =] *value_type*  
 Тип значения параметра. Символ `V` указывает, что *parameter_value* является литеральным значением, которое используется по умолчанию, если до исполнения не будет назначено других значений. Символ `R` означает, что *parameter_value* является указанным в ссылке значением и что ему было задано имя переменной среды. Этот аргумент является необязательным. По умолчанию используется символ `V`. Параметр *value_type* имеет тип **char(1)** .  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке перечислены некоторые условия, при которых хранимая процедура может вызвать ошибку.  
  
-   Недопустимый тип параметра.  
  
-   Недопустимое имя проекта  
  
-   Недопустимое имя пакета для параметров пакета.  
  
-   Недопустимый тип значения.  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Remarks  
  
-   Если никакое значение *value_type* не указано, то по умолчанию используется литеральное значение *parameter_value*. Если используется литеральное значение, параметру *value_set* в представлении [object_parameters](../../integration-services/system-views/catalog-object-parameters-ssisdb-database.md) присваивается значение `1`. Значение NULL недопустимо.  
  
-   Если *value_type* содержит символ `R`, обозначающий указанное в ссылке значение, то *parameter_value* ссылается на имя переменной среды.  
  
-   Значение `20` можно использовать в *object_type* для обозначения параметра проекта. В этом случае значение *object_name* не является обязательным, и любое значение, указанное для *object_name*, будет пропущено. Это значение используется, когда пользователь хочет задать параметр проекта.  
  
-   Значение `30` можно использовать в *object_type* для обозначения параметра пакета. В этом случае значение *object_name* используется для обозначения соответствующего пакета. Если значение *object_name* не указано, хранимая процедура возвращает сообщение об ошибке и прекращает выполнение.  
  
  
