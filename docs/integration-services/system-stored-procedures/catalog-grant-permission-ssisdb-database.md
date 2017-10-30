---
title: "Catalog.grant_permission (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- grant_permission stored procedure [Integration Services]
- catalog.grant_permission stored procedure [Integration Services]
ms.assetid: e72cfd52-de66-45e9-98b9-b8580ac7b956
caps.latest.revision: 25
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 71ca2fac0a6b9f087f9d434c5a701f5656889b9e
ms.openlocfilehash: 5f9bb38521631bcc60d39fba747f17b86183545d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/13/2017

---
# <a name="cataloggrantpermission-ssisdb-database"></a>catalog.grant_permission (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Предоставляет разрешение на защищаемый объект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.grant_permission [ @object_type = ] object_type  
    , [ @object_id = ] object_id  
    , [ @principal_id = ] principal_id  
    , [ @permission_type = ] permission_type  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @object_type =] *object_type*  
 Тип защищаемого объекта. Типы защищаемых объектов включают папку (`1`), проект (`2`), среду (`3`) и операции (`4`). *Object_type* — **smallint***.*  
  
 [ @object_id =] *object_id*  
 Уникальный идентификатор (ID) защищаемого объекта. *Object_id* — **bigint**.  
  
 [ @principal_id =] *principal_id*  
 Идентификатор участника, которому должно быть предоставлено разрешение. *Principal_id* — **int**.  
  
 [ @permission_type =] *permission_type*  
 Тип предоставляемого разрешения. *Permission_type* — **smallint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение)  
  
 1 (object_class недопустимое)  
  
 2 (object_id не существует)  
  
 3 (участник не существует)  
  
 4 (разрешение недопустимое)  
  
 5 (другая ошибка)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения ASSIGN_PERMISSIONS на объект  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  

Эта процедура может вызываться из имен входа, которые прошли проверку подлинности в SQL Server. Он не может быть вызван имени входа sa.
  
## <a name="remarks"></a>Замечания  
 В следующей таблице описаны хранимые процедуры, используемые для предоставления типов разрешений.  
  
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
 Информацию по наиболее значимым ошибкам и сообщениям см. в разделе «Значения кодов возврата».  
  
  

