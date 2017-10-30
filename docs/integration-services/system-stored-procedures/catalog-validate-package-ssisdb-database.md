---
title: "Catalog.validate_package (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- validate_package stored procedure [Integration Services]
- catalog.validate_package stored procedure [Integration Services]
ms.assetid: 0dc03df1-b793-408f-af4c-c11188729abf
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: e20b96e38f798c19a74d5f3a32a25e429dc8ebeb
ms.openlocfilehash: 869b758e3ac922762c293eb8aa9a9537a4397bd6
ms.contentlocale: ru-ru
ms.lasthandoff: 10/20/2017

---
# <a name="catalogvalidatepackage-ssisdb-database"></a>catalog.validate_package (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Асинхронно проверяет пакет в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.validate_package [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @package_name = ] package_name  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @target_environment = ] target_environment ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name =] *имя_папки*  
 Имя папки, в которой содержится пакет. *Имя_папки* — **nvarchar(128)**.  
  
 [ @project_name =] *project_name*  
 Имя проекта, в котором содержится пакет. *Project_name* — **nvarchar(128)**.  
  
 [ @package_name =] *имя_пакета*  
 Имя пакета. *Имя_пакета* — **nvarchar(260)**.  
  
 [ @validation_id =] *validation_id*  
 Возвращает уникальный идентификатор (ID) проверки. *Validation_id* — **bigint**.  
  
 [ @use32bitruntime =] *use32bitruntime*  
 Указывает, должна ли использоваться 32-разрядная среда выполнения для запуска этого пакета в 64-разрядной операционной системе. Используйте значение `1` для запуска пакета в 32-разрядной средой выполнения при запуске в 64-разрядной операционной системе. Используйте значение `0` для выполнения пакета в 64-разрядной среде выполнения при его запуске в 64-разрядной операционной системе. Этот параметр является необязательным. *Use32bitruntime* — **бит**.  
  
 [ @environment_scope =] *environment_scope*  
 Указывает ссылки на среду, которые учитываются при проверке. Если это значение равно `A`, то в проверку включены все ссылки на среду, связанные с проектом. Если это значение равно `S`, то включена лишь единственная ссылка на среду. Если это значение равно `D`, то никакие ссылки на среду не включены и каждый параметр, чтобы пройти проверку, должен иметь литеральное значение по умолчанию. Этот параметр является необязательным. Символ `D` используется по умолчанию. *Environment_scope* — **Char(1)**.  
  
 [ @reference_id =] *reference_id*  
 Уникальный идентификатор ссылки на среду. Этот параметр является обязательным только в том случае, если включены единственная ссылка на среду в проверке, когда *environment_scope* — `S`. *Reference_id* — **bigint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ на проект, а также, если применимо, разрешения READ на среды, указанные в ссылках  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Имя проекта или имя пакета недопустимы  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Одна или несколько ссылочных сред, включенных в проверку, не содержат переменные, на которые имеется ссылка  
  
-   Пакет не прошел проверку  
  
-   Среда, на которую указывает ссылка, не существует.  
  
-   Не удается найти переменные, на которые имеется ссылка, в ссылочных средах, включенных в проверку  
  
-   Параметры пакета ссылаются на переменные, но в проверку не включены ссылочные среды  
  
## <a name="remarks"></a>Замечания  
 Проверка помогает выявить проблемы, которые могут мешать успешному выполнению пакета. Используйте [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) или [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) представлений для контроля состояния проверки.  
  
  

