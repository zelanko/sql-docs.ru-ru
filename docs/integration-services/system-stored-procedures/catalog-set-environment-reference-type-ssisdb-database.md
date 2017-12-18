---
title: "catalog.set_environment_reference_type (база данных SSISDB) | Документы Майкрософт"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: b79e3a06-22c0-40e5-8933-1b3414db3329
caps.latest.revision: "15"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 31a6d4310ad32f2517c8779172b0d539803e9f15
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="catalogsetenvironmentreferencetype-ssisdb-database"></a>catalog.set_environment_reference_type (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Задает ссылочный тип и имя среды, связанные с существующей ссылкой на среду для проекта в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.set_environment_reference_location [ @reference_id = reference_id  
    , [ @reference_type = ] reference_type  
 [  , [ @environment_folder_name = ] environment_folder_name ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @reference_id = ] *reference_id*  
 Уникальный идентификатор обновляемой ссылки на среду. Параметр *reference_id* имеет тип **bigint**.  
  
 [ @reference_type = ] *reference_type*  
 Указывает, может среда находиться в той же папке, что и проект (относительная ссылка), или в другой папке (абсолютная ссылка). Значение `R` указывает, что ссылка относительная. Значение `A` указывает, что ссылка абсолютная. Параметр *reference_type* имеет тип **char(1)**.  
  
 [ @environment_folder_name = ] *environment_folder_name*  
 Папка, в которой находится среда. Это значение требуется для абсолютных ссылок. Параметр *environment_folder_name* имеет тип **nvarchar(128)**.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на проект и разрешение READ на среду  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Недопустимое имя папки, имя среды или идентификатор ссылки.  
  
-   Пользователь не имеет соответствующих разрешений.  
  
-   Задана абсолютная ссылка с помощью символа `A` в параметре *reference_location*, но имя папки в параметре *environment_folder_name* не указано.  
  
## <a name="remarks"></a>Замечания  
 Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени и требуют, чтобы она находилась в той же папке, что и проект. Абсолютные ссылки указывают среду с применением имени и папки и могут указывать среды, находящиеся в иной папке, чем проект. Проект может ссылаться на несколько сред.  
  
> [!IMPORTANT]  
>  Если указана относительная ссылка, значение параметра *environment_folder_name* не используется, а имени папки среды автоматически присваивается значение **NULL**. Если указана абсолютная ссылка, должно быть задано имя папки среды через параметр *environment_folder_name*.  
  
  
