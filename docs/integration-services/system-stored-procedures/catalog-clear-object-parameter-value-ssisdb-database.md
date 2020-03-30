---
title: catalog.clear_object_parameter_value (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: dcbbb714-a051-4805-9e2b-2c2fb647c890
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2ad9b1900c3933b2756d376f152ac714af91cc3d
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2020
ms.locfileid: "71281067"
---
# <a name="catalogclear_object_parameter_value-ssisdb-database"></a>catalog.clear_object_parameter_value (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Очищает значение параметра для существующего проекта или пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], который хранится на сервере.  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.clear_object_parameter [ @folder_name = ] folder_name   
    , [ @project_name = ] project_name   
    , [ @object_type = ] object_type   
    , [ @object_name = ] object_name   
    , [ @parameter_ name = ] parameter_name  
```  
  
## <a name="arguments"></a>Аргументы  
 [ \@folder_name = ] *folder_name*  
 Имя папки, которая содержит проект. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [ \@project_name = ] *project_name*  
 Имя проекта. Параметр *project_name* имеет тип **nvarchar(128)** .  
  
 [ \@object_type = ] *object_type*  
 Тип объекта. Для проекта допустимо, в частности, значение `20`, а для пакета — значение `30`. Параметр *object_type* имеет тип **smallInt**.  
  
 [ \@ object _name = ] *object _name*  
 Имя пакета. Параметр *object _name* имеет тип **nvarchar(260)** .  
  
 [ \@parameter_ name = ] *parameter_name*  
 Имя параметра. Параметр *parameter_ name* имеет тип **nvarchar(128)** .  
  
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
 В следующем списке перечислены некоторые условия, при которых хранимая процедура clear_object_parameter может вызвать ошибку:  
  
-   Указан недопустимый тип объекта, или имя объекта в проекте отсутствует.  
  
-   Проект не существует, недоступен или имеет недопустимое имя.  
  
-   Указано недопустимое имя параметра.  
  
-   Пользователь не имеет соответствующих разрешений.  
  
  
