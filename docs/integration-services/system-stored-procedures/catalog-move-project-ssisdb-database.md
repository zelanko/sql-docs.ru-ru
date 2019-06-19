---
title: catalog.move_project (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: ef3b0325-d8e9-472b-bf11-7d3efa6312ff
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c79df90c6093ed93668e504e574c712a2ba2146a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65716017"
---
# <a name="catalogmoveproject---ssisdb-database"></a>catalog.move_project — база данных SSISDB

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Перемещает проект из одной папки в другую в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.move_project [ @source_folder = ] source_folder  
    , [ @project_name = ] project_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @source_folder = ] *source_folder*  
 Имя исходной папки, в которой проект хранится до перемещения. Параметр *source_folder* имеет тип **nvarchar(128)** .  
  
 [ @project_name = ] *project_name*  
 Имя перемещаемого проекта. Параметр *project_name* имеет тип **nvarchar(128)** .  
  
 [ @destination_folder = ] *destination_folder*  
 Имя целевой папки, в которой проект хранится после перемещения. Параметр *destination_folder* имеет тип **nvarchar(128)** .  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на перемещаемый проект и разрешение CREATE_OBJECTS на целевую папку.  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке приведено описание некоторых условий, при которых эта хранимая процедура может вызывать ошибки.  
  
-   Проект не существует  
  
-   Исходная папка не существует  
  
-   Целевая папка не существует или уже содержит объект с таким же именем  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Remarks  
 При перемещении проекта из исходной папки в целевую этот проект и все соответствующие ссылки на среду удаляются из исходной папки. В целевой папке создается аналогичные проект и ссылки на среду. Относительные ссылки на среду после перемещения будут указывать на другую папку. Абсолютные ссылки на среду после перемещения будут указывать на ту же папку.  
  
> [!NOTE]  
>  Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени, для использования этих ссылок среда должна находиться в той же папке, что и проект. Абсолютные ссылки указывают среду по имени и папке, они могут ссылаться на среду, расположенную в другой папке, отличной от папки, в которой находится проект.  
  
  
