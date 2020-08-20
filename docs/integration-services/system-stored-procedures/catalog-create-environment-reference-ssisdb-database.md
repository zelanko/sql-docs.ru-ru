---
description: catalog.create_environment_reference (база данных SSISDB)
title: catalog.create_environment_reference (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 48069bea-31cb-4a0e-9849-a07edc94088f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dcca4fd25fd201c9b278107dce188b6cab12d866
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88477141"
---
# <a name="catalogcreate_environment_reference-ssisdb-database"></a>catalog.create_environment_reference (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Создает ссылку на среду для проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_environment_reference [ @folder_name = ] folder_name  
     , [ @project_name = ] project_name  
     , [ @environment_name = ] environment_name  
     , [ @reference_type = ] reference_type  
  [  , [ @environment_folder_name = ] environment_folder_name ]  
  [  , [ @reference_id = ] reference_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки проекта, которая ссылается на среду. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [ @project_name = ] *project_name*  
 Имя проекта, ссылающегося на среду. Параметр *project_name* имеет тип **nvarchar(128)** .  
  
 [ @environment_name = ] *environment_name*  
 Имя среды, на которую указывает ссылка. Параметр *environment_name* имеет тип **nvarchar(128)** .  
  
 [ @reference_type = ] *reference_type*  
 Указывает, может среда находиться в той же папке, что и проект (относительная ссылка), или в другой папке (абсолютная ссылка). Значение `R` указывает, что ссылка относительная. Значение `A` указывает, что ссылка абсолютная. Параметр *reference_type* имеет тип **char(1)** .  
  
 [ @environment_folder_name = ] *environment_folder_name*  
 Имя папки, в которой находится среда, на которую указывает ссылка. Это значение требуется для абсолютных ссылок. Параметр *environment_folder_name* имеет тип **nvarchar(128)** .  
  
 [ @reference_id = ] *reference_id*  
 Возвращает уникальный идентификатор для новой ссылки. Это необязательный параметр. Параметр *reference_id* имеет тип **bigint**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
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
  
## <a name="remarks"></a>Remarks  
 Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени и требуют, чтобы она находилась в той же папке, что и проект. Абсолютные ссылки указывают среду с применением имени и папки и могут указывать среды, находящиеся в иной папке, чем проект. Проект может ссылаться на несколько сред.  
  
  
