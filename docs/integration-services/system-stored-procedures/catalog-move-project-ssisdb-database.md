---
title: "Catalog.move_project (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: ef3b0325-d8e9-472b-bf11-7d3efa6312ff
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5b091ccea1f733ebbf6e52308d17c7bdb7449cbe
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogmoveproject---ssisdb-database"></a>Catalog.move_project - база данных SSISDB
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Перемещает проект из одной папки в другую в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
move_project [ @source_folder = ] source_folder  
    , [ @project_name = ] project_name  
    , [ @destination_folder = ] destination_folder  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @source_folder =] *source_folder*  
 Имя исходной папки, в которой проект хранится до перемещения. *Source_folder* — **nvarchar(128)**.  
  
 [ @project_name =] *project_name*  
 Имя перемещаемого проекта. *Project_name* — **nvarchar(128)**.  
  
 [ @destination_folder =] *destination_folder*  
 Имя целевой папки, в которой проект хранится после перемещения. *Destination_folder* — **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на перемещаемый проект и разрешение CREATE_OBJECTS на целевую папку.  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке приведено описание некоторых условий, при которых эта хранимая процедура может вызывать ошибки.  
  
-   Проект не существует  
  
-   Исходная папка не существует  
  
-   Целевая папка не существует или уже содержит объект с таким же именем  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Замечания  
 При перемещении проекта из исходной папки в целевую этот проект и все соответствующие ссылки на среду удаляются из исходной папки. В целевой папке создается аналогичные проект и ссылки на среду. Относительные ссылки на среду после перемещения будут указывать на другую папку. Абсолютные ссылки на среду после перемещения будут указывать на ту же папку.  
  
> [!NOTE]  
>  Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени, для использования этих ссылок среда должна находиться в той же папке, что и проект. Абсолютные ссылки указывают среду по имени и папке, они могут ссылаться на среду, расположенную в другой папке, отличной от папки, в которой находится проект.  
  
  
