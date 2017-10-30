---
title: "Catalog.validate_project (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5270689a-46d4-4847-b41f-3bed1899e955
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 83439015694f4235af4a67e994e916651ec63cc1
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogvalidateproject-ssisdb-database"></a>catalog.validate_project (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Асинхронно проверяет проект в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.validate_project [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @validate_type = ] validate_type  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки, которая содержит проект. *Имя_папки* — **nvarchar(128)**.  
  
 [ @project_name =] *project_name*  
 Имя проекта. *Project_name* — **nvarchar(128)**.  
  
 [ @validate_type =] *validate_type*  
 Указывает тип выполняемой проверки. Используйте символ `F` для выполнения полной проверки. *Validate_type* — **char(1)**.  
  
 [ @validation_id =] *validation_id*  
 Возвращает уникальный идентификатор (ID) проверки. *Validation_id* — **bigint**.  
  
 [ @use32bitruntime =] *use32bitruntime*  
 Указывает, должна ли использоваться 32-разрядная среда выполнения для запуска этого пакета в 64-разрядной операционной системе. Используйте значение `1` для запуска пакета в 32-разрядной средой выполнения при запуске в 64-разрядной операционной системе. Используйте значение `0` для выполнения пакета в 64-разрядной среде выполнения при его запуске в 64-разрядной операционной системе. Этот параметр является необязательным. *Use32bitruntime* — **бит**.  
  
 [ @environment_scope =] *environment_scope*  
 Указывает ссылки на среду, которые учитываются при проверке. Если это значение равно `A`, то в проверку включены все ссылки на среду, связанные с проектом. Если это значение равно `S`, то включена лишь единственная ссылка на среду. Если это значение равно `D`, то никакие ссылки на среду не включены и каждый параметр, чтобы пройти проверку, должен иметь литеральное значение по умолчанию. Этот параметр является необязательным. По умолчанию будет использоваться символ `D`. *Environment_scope* — **Char(1)**.  
  
 [ @reference_id =] *reference_id*  
 Уникальный идентификатор ссылки на среду. Этот параметр является обязательным только в том случае, если включены единственная ссылка на среду в проверке, когда *environment_scope* — `S`. *Reference_id* — **bigint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Выходные данные шагов проверки возвращаются в различных разделах результирующего набора.  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ на проект, а также, если применимо, разрешения READ на среды, указанные в ссылках  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке приводятся некоторые условия, при которых может возникнуть ошибка или предупреждение.  
  
-   Происходит ошибка проверки одного или нескольких пакетов в проекте  
  
-   Проверка завершается неудачно, если одна или несколько сред, указанных в ссылках, включенных в проверку, не содержат переменных, на которые указывают ссылки  
  
-   Указанный тип проверки недействителен  
  
-   Имя проекта или идентификатор ссылки на среду недопустимы  
  
-   Пользователь не имеет соответствующих разрешений  
  
## <a name="remarks"></a>Замечания  
 Проверка помогает выявить проблемы, которые помешают пакету в проекте правильно выполняться. Используйте [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) или [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) представлений для контроля состояния проверки.  
  
 В проверке могут задействоваться только доступные пользователю среды. Выходные данные проверки отправляются клиенту в форме результирующего набора.  
  
 В этом выпуске проверка проектов не поддерживает проверку зависимостей.  
  
 При полной проверке подтверждается, что все переменные среды, на которые указывают ссылки, находятся во включенных в проверку средах, на которые указывают ссылки. В результатах полной проверки перечисляются недействительные ссылки на среды, а также переменные сред, на которые указывают ссылки, которые не удалось найти ни в одной из входящих в проверку сред, на которые указывают ссылки.  
  
  

