---
title: "Catalog.revoke_permission (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
helpviewer_keywords:
- revoke_permission stored procedure [Integration Services]
- catalog.revoke_permission stored procedure [Integration Services]
ms.assetid: 850b9c26-5c7c-47b9-a61c-5cf9bb5948cf
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: f058368bdd39b31a569d8810cccfc4d03d9f875e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogrevokepermission-ssisdb-database"></a>catalog.revoke_permission (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отзывает разрешение на защищаемый объект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.revoke_permission [ @object_type = ] object_type  
    , [ @object_id = ] object_id  
    , [ @principal_id = ] principal_id  
    , [ @permission_type = ] permission_type  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @object_type =] *object_type*  
 Тип защищаемого объекта. Типы защищаемых объектов включают папку (`1`), проект (`2`), среду (`3`) и операции (`4`). *Object_type* — **smallint***.*  
  
 [ @object_id =] *object_id*  
 Уникальный идентификатор защищаемого объекта. *Object_id* — **bigint**.  
  
 [ @principal_id =] *principal_id*  
 Идентификатор участника, у которого отзывается разрешение. *Principal_id* — **int**.  
  
 [ @permission_type =] *permission_type*  
 Тип разрешения. *Permission_type* — **smallint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение)  
  
 1 (object_class недопустимо)  
  
 2 (object_id не существует)  
  
 3 (участник не существует)  
  
 4 (разрешение не является допустимым)  
  
 5 (другая ошибка)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="remarks"></a>Замечания  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения ASSIGN_PERMISSIONS на объект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="remarks"></a>Замечания  
 Если указан permission_type, хранимая процедура удаляет разрешение, явно назначенные участнику на объект. Даже если таких экземпляров нет, процедура возвращает значение успешного выполнения (`0`). Если permission_type указан, хранимая процедура удаляет все разрешения участника для объекта.  
  
> [!NOTE]  
>  У участника может оставаться указанное разрешение на объект, если он является членом роли, имеющей это разрешение.  
  
 Хранимая процедура позволяет отзывать типа разрешений, указанные в следующей таблице:  
  
|Значение permission_type|Имя разрешения|Описание разрешения|Применимые типы объектов|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|Разрешает участнику читать сведения, рассматриваемые как часть объекта, например свойства. Тем самым участнику не разрешается перечислять или читать содержимое других объектов, содержащихся в этом объекте.|Папка, проект, среда, операция|  
|`2`|MODIFY|Разрешает участнику изменять сведения, рассматриваемые как часть объекта, например свойства. Тем самым участнику не разрешается изменять другие объекты, содержащиеся в этом объекте.|Папка, проект, среда, операция|  
|`3`|Выполните|Разрешает участнику выполнять все пакеты в проекте.|Проект|  
|`4`|MANAGE_PERMISSIONS|Разрешает участнику назначать разрешения на объекты.|Папка, проект, среда, операция|  
|`100`|CREATE_OBJECTS|Разрешает участнику создавать объекты в папке.|Папка|  
|`101`|READ_OBJECTS|Разрешает участнику читать все объекты в папке.|Папка|  
|`102`|MODIFY_OBJECTS|Разрешает участнику изменять все объекты в папке.|Папка|  
|`103`|EXECUTE_OBJECTS|Разрешает участнику выполнять все пакеты из всех проектов в папке.|Папка|  
|`104`|MANAGE_OBJECT_PERMISSIONS|Разрешает участнику управлять разрешениями на все объекты в папке.|Папка|  
  
  

