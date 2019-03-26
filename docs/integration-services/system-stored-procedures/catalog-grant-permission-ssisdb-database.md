---
title: catalog.grant_permission (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- grant_permission stored procedure [Integration Services]
- catalog.grant_permission stored procedure [Integration Services]
ms.assetid: e72cfd52-de66-45e9-98b9-b8580ac7b956
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0e129306c256106da59c890d32a96c9b1d81abd
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58290190"
---
# <a name="cataloggrantpermission-ssisdb-database"></a>catalog.grant_permission (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Предоставляет разрешение на защищаемый объект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.grant_permission [ @object_type = ] object_type  
    , [ @object_id = ] object_id  
    , [ @principal_id = ] principal_id  
    , [ @permission_type = ] permission_type  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @object_type = ] *object_type*  
 Тип защищаемого объекта. Типы защищаемых объектов включают папку (`1`), проект (`2`), среду (`3`) и операцию (`4`). Параметр *object_type* имеет тип **smallint**_._  
  
 [ @object_id = ] *object_id*  
 Уникальный идентификатор (ID) защищаемого объекта. Параметр *object_id* имеет тип **bigint**.  
  
 [ @principal_id = ] *principal_id*  
 Идентификатор участника, которому должно быть предоставлено разрешение. Параметр *principal_id* имеет тип **int**.  
  
 [ @permission_type = ] *permission_type*  
 Тип предоставляемого разрешения. Параметр *permission_type* имеет тип **smallint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение)  
  
 1 (object_class недопустим)  
  
 2 (object_id не существует)  
  
 3 (субъект не существует)  
  
 4 (недопустимое разрешение)  
  
 5 (другая ошибка)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения ASSIGN_PERMISSIONS на объект  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  

Эту процедуру не могут вызывать имена входа, которые прошли проверку подлинности в SQL Server. Ее невозможно вызвать с помощью имени входа SA.
  
## <a name="remarks"></a>Remarks  
 В следующей таблице описаны хранимые процедуры, используемые для предоставления типов разрешений.  
  
|Значение permission_type|Имя разрешения|Описание разрешения|Применимые типы объектов|  
|----------------------------|---------------------|----------------------------|-----------------------------|  
|`1`|READ|Разрешает участнику читать сведения, рассматриваемые как часть объекта, например свойства. Тем самым участнику не разрешается перечислять или читать содержимое других объектов, содержащихся в этом объекте.|Папка, проект, среда, операция|  
|`2`|MODIFY|Разрешает участнику изменять сведения, рассматриваемые как часть объекта, например свойства. Тем самым участнику не разрешается изменять другие объекты, содержащиеся в этом объекте.|Папка, проект, среда, операция|  
|`3`|EXECUTE|Разрешает участнику выполнять все пакеты в проекте.|Проект|  
|`4`|MANAGE_PERMISSIONS|Разрешает участнику назначать разрешения на объекты.|Папка, проект, среда, операция|  
|`100`|CREATE_OBJECTS|Разрешает участнику создавать объекты в папке.|Папка|  
|`101`|READ_OBJECTS|Разрешает участнику читать все объекты в папке.|Папка|  
|`102`|MODIFY_OBJECTS|Разрешает участнику изменять все объекты в папке.|Папка|  
|`103`|EXECUTE_OBJECTS|Разрешает участнику выполнять все пакеты из всех проектов в папке.|Папка|  
|`104`|MANAGE_OBJECT_PERMISSIONS|Разрешает участнику управлять разрешениями на все объекты в папке.|Папка|  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Информацию по наиболее значимым ошибкам и сообщениям см. в разделе «Значения кодов возврата».  
  
  
