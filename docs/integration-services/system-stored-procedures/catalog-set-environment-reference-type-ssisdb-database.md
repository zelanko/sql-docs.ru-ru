---
title: "Catalog.set_environment_reference_type (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b79e3a06-22c0-40e5-8933-1b3414db3329
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e83d9979ee4736528efb4851848ea3eac717fab8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogsetenvironmentreferencetype-ssisdb-database"></a>catalog.set_environment_reference_type (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задает ссылочный тип и имя среды, связанные с существующей ссылкой на среду для проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_environment_reference_location [ @reference_id = reference_id  
    , [ @reference_type = ] reference_type  
 [  , [ @environment_folder_name = ] environment_folder_name ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @reference_id =] *reference_id*  
 Уникальный идентификатор обновляемой ссылки на среду. *Reference_id* — **bigint**.  
  
 [ @reference_type =] *reference_type*  
 Указывает, может среда находиться в той же папке, что и проект (относительная ссылка), или в другой папке (абсолютная ссылка). Значение `R` указывает, что ссылка относительная. Значение `A` указывает, что ссылка абсолютная. *Reference_type* — **char(1)**.  
  
 [ @environment_folder_name =] *environment_folder_name*  
 Папка, в которой находится среда. Это значение требуется для абсолютных ссылок. *Environment_folder_name* — **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проект и разрешение READ на среду  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Недопустимое имя папки, имя среды или идентификатор ссылки.  
  
-   Пользователь не имеет соответствующих разрешений.  
  
-   Абсолютная ссылка задается с помощью `A` знаку в *reference_location* параметра, но имя папки не указан с *environment_folder_name* параметр.  
  
## <a name="remarks"></a>Замечания  
 Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени и требуют, чтобы она находилась в той же папке, что и проект. Абсолютные ссылки указывают среду с применением имени и папки и могут указывать среды, находящиеся в иной папке, чем проект. Проект может ссылаться на несколько сред.  
  
> [!IMPORTANT]  
>  Если задан относительная ссылка, *environment_folder_name* значение параметра не используется, и имя папки среды автоматически устанавливается значение **NULL**. Если указано абсолютная ссылка в необходимо указать имя папки среды *environment_folder_name* параметра.  
  
  

