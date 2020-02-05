---
title: catalog.move_environment (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: b3fb5242-3c4c-4a87-b3e5-beb22fbab053
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bc0bc77fda49e715879dceec60d616143952c265
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71296838"
---
# <a name="catalogmove_environment-ssisdb-database"></a>catalog.move_environment (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Перемещает среду из одной папки в другую в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.move_environment [ @source_folder = ] source_folder  
    , [ @environment_name = ] environment_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @source_folder = ] *source_folder*  
 Имя исходной папки, в которой среда хранится до перемещения. Параметр *source_folder* имеет тип **nvarchar(128)** .  
  
 [ @environment_name = ] *environment_name*  
 Имя перемещаемой среды. Параметр *environment_name* имеет тип **nvarchar(128)** .  
  
 [ @destination_folder = ] *destination_folder*  
 Имя целевой папки, в которой среда хранится после перемещения. Параметр *destination_folder* имеет тип **nvarchar(128)** .  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY для среды  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   В исходной папке среда отсутствует  
  
-   В указанной папке уже существует среда с тем же именем  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Remarks  
 Ссылки из проектов на среду не изменяются с учетом перемещения. Ссылки на среду должны обновляться соответствующим образом. Хранимая процедура будет выполнена успешно, даже если вследствие перемещения среды ссылки на нее оказались недействительными. Ссылки на среду должны обновляться после завершения этой хранимой процедуры.  
  
> [!NOTE]  
>  Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени, для использования этих ссылок среда должна находиться в той же папке, что и проект. Абсолютные ссылки указывают среду по имени и папке, они могут ссылаться на среду, расположенную в другой папке, отличной от папки, в которой находится проект.  
  
  
