---
title: "Catalog.deny_permission (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: de310bac-2ddc-4ef9-8783-43dcb02a94f1
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 689a59e92286881fa3be7ee3754a786ccb54ae6c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogdenypermission-ssisdb-database"></a>catalog.deny_permission (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Отменяет разрешение на защищаемый объект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
deny_permission [ @object_type = ] object_type  
    , [ @object_id = ] object_id  
    , [ @principal_id = ] principal_id  
    , [ @permission_type = ] permission_type  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @object_type =] *object_type*  
 Тип защищаемого объекта. Типы защищаемых объектов включают папку (`1`), проект (`2`), среду (`3`) и операции (`4`). *Object_type* — **smallint***.*  
  
 [ @object_id =] *object_id*  
 Уникальный идентификатор (ID) первичного ключа защищаемого объекта. *Object_id* — **bigint**.  
  
 [ @principal_id =] *principal_id*  
 Идентификатор участника, которому должно быть отказано в доступе. *Principal_id* — **int**.  
  
 [ @permission_type =] *permission_type*  
 Тип разрешения, которое должно быть отклонено. *Permission_type* — **smallint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение)  
  
 1 (object_class недопустимо)  
  
 2 (object_id не существует)  
  
 3 (участник не существует)  
  
 4 (разрешение не является допустимым)  
  
 5 (другая ошибка)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешение MANAGE_PERMISSIONS на объект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="remarks"></a>Замечания  
 В следующей таблице описаны хранимые процедуры, используемые для отклонения типов разрешений.  
  
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
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Если permission_type указан, процедура отклонит указанное разрешение, явно назначенные указанного участника для указанного объекта. Даже если таких экземпляров нет, процедура все равно возвратит значение кода успешного завершения (`0`).  
  
-   Если permission_type указан, процедура отклонит все разрешения для указанного участника на указанный объект.  
  
  
