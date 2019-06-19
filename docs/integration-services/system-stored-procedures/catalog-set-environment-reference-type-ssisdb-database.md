---
title: catalog.set_environment_reference_type (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: b79e3a06-22c0-40e5-8933-1b3414db3329
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 55dc0c5b3cbfb51e15cd0813c87c66e840e592a2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65715924"
---
# <a name="catalogsetenvironmentreferencetype-ssisdb-database"></a>catalog.set_environment_reference_type (база данных SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


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
 Указывает, может среда находиться в той же папке, что и проект (относительная ссылка), или в другой папке (абсолютная ссылка). Значение `R` указывает, что ссылка относительная. Значение `A` указывает, что ссылка абсолютная. Параметр *reference_type* имеет тип **char(1)** .  
  
 [ @environment_folder_name = ] *environment_folder_name*  
 Папка, в которой находится среда. Это значение требуется для абсолютных ссылок. Параметр *environment_folder_name* имеет тип **nvarchar(128)** .  
  
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
  
-   Недопустимое имя папки, имя среды или идентификатор ссылки.  
  
-   Пользователь не имеет соответствующих разрешений.  
  
-   Задана абсолютная ссылка с помощью символа `A` в параметре *reference_location*, но имя папки в параметре *environment_folder_name* не указано.  
  
## <a name="remarks"></a>Remarks  
 Проект может иметь относительные или абсолютные ссылки на среду. Относительные ссылки указывают среду по имени и требуют, чтобы она находилась в той же папке, что и проект. Абсолютные ссылки указывают среду с применением имени и папки и могут указывать среды, находящиеся в иной папке, чем проект. Проект может ссылаться на несколько сред.  
  
> [!IMPORTANT]  
>  Если указана относительная ссылка, значение параметра *environment_folder_name* не используется, а имени папки среды автоматически присваивается значение **NULL**. Если указана абсолютная ссылка, должно быть задано имя папки среды через параметр *environment_folder_name*.  
  
  
