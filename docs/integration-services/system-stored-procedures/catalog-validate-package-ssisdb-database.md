---
title: catalog.validate_package (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
helpviewer_keywords:
- validate_package stored procedure [Integration Services]
- catalog.validate_package stored procedure [Integration Services]
ms.assetid: 0dc03df1-b793-408f-af4c-c11188729abf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 5b1e9dccf528a06ae9f2dceb44ff0af65bc30e77
ms.sourcegitcommit: 7ccb8f28eafd79a1bddd523f71fe8b61c7634349
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/20/2019
ms.locfileid: "58280018"
---
# <a name="catalogvalidatepackage-ssisdb-database"></a>catalog.validate_package (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Асинхронно проверяет пакет в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql
catalog.validate_package [ @folder_name = ] folder_name  
    , [ @project_name = ] project_name  
    , [ @package_name = ] package_name  
    , [ @validation_id = ] validation_id OUTPUT  
 [  , [ @use32bitruntime = ] use32bitruntime ]  
 [  , [ @environment_scope = ] environment_scope ]  
 [  , [ @reference_id = ] reference_id ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @folder_name = ] *folder_name*  
 Имя папки, в которой содержится пакет. Параметр *folder_name* имеет тип **nvarchar(128)**.  
  
 [ @project_name = ] *project_name*  
 Имя проекта, в котором содержится пакет. Параметр *project_name* имеет тип **nvarchar(128)**.  
  
 [ @package_name = ] *package_name*  
 Имя пакета. Параметр *package_name* имеет тип **nvarchar(260)**.  
  
 [ @validation_id = ] *validation_id*  
 Возвращает уникальный идентификатор (ID) проверки. Параметр *validation_id* имеет тип **bigint**.  
  
 [ @use32bitruntime = ] *use32bitruntime*  
 Указывает, должна ли использоваться 32-разрядная среда выполнения для запуска этого пакета в 64-разрядной операционной системе. Используйте значение `1` для выполнения пакета в 32-разрядной среде выполнения при его запуске в 64-разрядной операционной системе. Используйте значение `0` для выполнения пакета в 64-разрядной среде выполнения при его запуске в 64-разрядной операционной системе. Этот параметр является необязательным. Параметр *use32bitruntime* имеет тип **bit**.  
  
 [ @environment_scope = ] *environment_scope*  
 Указывает ссылки на среду, которые учитываются при проверке. Если это значение равно `A`, то в проверку включены все ссылки на среду, связанные с проектом. Если это значение равно `S`, то включена лишь единственная ссылка на среду. Если это значение равно `D`, то никакие ссылки на среду не включены и каждый параметр, чтобы пройти проверку, должен иметь литеральное значение по умолчанию. Этот параметр является необязательным. По умолчанию используется знак `D`. Параметр *environment_scope* имеет тип **char(1)**.  
  
 [ @reference_id = ] *reference_id*  
 Уникальный идентификатор ссылки на среду. Этот параметр является обязательным, только если в проверку включена единственная ссылка на среду, при том что *environment_scope* имеет значение `S`. Параметр *reference_id* имеет тип **bigint**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ на проект, а также, если применимо, разрешения READ на среды, указанные в ссылках  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Имя проекта или имя пакета недопустимы  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Одна или несколько ссылочных сред, включенных в проверку, не содержат переменные, на которые имеется ссылка  
  
-   Пакет не прошел проверку  
  
-   Среда, на которую указывает ссылка, не существует.  
  
-   Не удается найти переменные, на которые имеется ссылка, в ссылочных средах, включенных в проверку  
  
-   Параметры пакета ссылаются на переменные, но в проверку не включены ссылочные среды  
  
## <a name="remarks"></a>Remarks  
 Проверка помогает выявить проблемы, которые могут помешать пакету правильно выполняться. Используйте представления [catalog.validations](../../integration-services/system-views/catalog-validations-ssisdb-database.md) или [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) для контроля состояния проверки.  
  
  
