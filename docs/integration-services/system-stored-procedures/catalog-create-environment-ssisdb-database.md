---
title: catalog.create_environment (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 66367092-9f6e-40e6-90bd-81efb078ab70
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2d7d856d9a90e86c4e1fe188a7526312500b4e3d
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/22/2020
ms.locfileid: "86917178"
---
# <a name="catalogcreate_environment-ssisdb-database"></a>catalog.create_environment (база данных SSISDB)

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Создает среду в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_environment [ @folder_name = ] folder_name  
     , [ @environment_name = ] environment_name  
  [  , [ @environment_description = ] environment_description ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [@folder_name =] *folder_name*  
 Имя папки, которая будет содержать среду. Параметр *folder_name* имеет тип **nvarchar(128)** .  
  
 [@environment_name =] *environment_name*  
 Имя среды. Параметр *environment_name* имеет тип **nvarchar(128)** .  
  
 [@environment_description=] *environment_description*  
 Необязательное описание среды. Параметр *environment_description* имеет тип **nvarchar(1024)** .  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на папку  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   роль базы данных;  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Имя папки не обнаружено  
  
-   Среда с таким именем уже существует в указанной папке  
  
## <a name="remarks"></a>Remarks  
 Имя среды должно быть уникальным в пределах папки.  
  
  
