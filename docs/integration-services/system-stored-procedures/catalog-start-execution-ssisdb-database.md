---
title: "Catalog.start_execution (база данных SSISDB) | Документы Microsoft"
ms.custom: 
ms.date: 12/16/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: f8663ff3-aa98-4dd8-b850-b21efada0b87
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 70359d539bc7b4fc6dd70de8bbb7e16be5d71208
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogstartexecution-ssisdb-database"></a>catalog.start_execution (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Запускает экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```tsql  
start_execution [ @execution_id = ] execution_id [, [@retry_count = ] retry_count]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @execution_id =] *execution_id*  
 Уникальный идентификатор для экземпляра выполнения. *Execution_id* — **bigint**.
 
 [ @retry_count =] *число_повторов*  
 Число повторных попыток в случае, если происходит сбой выполнения. Она вступает в силу только при выполнении в масштабное развертывание. Этот параметр является необязательным. Оно присвоено значение 0, если не указано. *Число_повторов* — **int**.
  
## <a name="remarks"></a>Замечания  
 Выполнение применяется для задания значений параметров, которые будут использоваться пакетом в течение одного экземпляра выполнения пакета. После создания экземпляра исполнения и до его начала соответствующий проект должен быть повторно развернут. В этом случае экземпляр исполнения будет ссылаться на устаревший проект. Из-за этого хранимая процедура завершится с ошибкой.  
  
> [!NOTE]  
>  Исполнения можно начинать только один раз. Запустить экземпляр выполнения, он должен быть создан (значение `1` в **состояние** столбец [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md) представления).  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется вызов catalog.create_execution для создания экземпляра выполнения пакета Child1.dtsx. Проект Project1 служб Integration Services содержит пакет. В этом примере выполняется вызов catalog.set_execution_parameter_value для задания значений для параметров Parameter1, Parameter2 и LOGGING_LEVEL. В этом примере выполняется вызов catalog.start_execution для запуска экземпляра выполнения.  
  
```  
Declare @execution_id bigint  
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'Child1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'TestDeply4', @project_name=N'Integration Services Project1', @use32bitruntime=False, @reference_id=Null  
Select @execution_id  
DECLARE @var0 sql_variant = N'Child1.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter1', @parameter_value=@var0  
DECLARE @var1 sql_variant = N'Child2.dtsx'  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=20, @parameter_name=N'Parameter2', @parameter_value=@var1  
DECLARE @var2 smallint = 1  
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id, @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var2  
EXEC [SSISDB].[catalog].[start_execution] @execution_id  
GO  
  
```  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на экземпляр выполнения, разрешения READ и EXECUTE на проект и, при необходимости, разрешения READ на среду, указанную в ссылке  
  
-   Членство в **ssis_admin** роли базы данных  
  
-   Членство в **sysadmin** роли сервера  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Недопустимый идентификатор выполнения  
  
-   Исполнение уже началось или уже завершилось; исполнения могут начаться только один раз  
  
-   Связанная с проектом ссылка на среду недействительна  
  
-   Требуемые значения параметра не заданы  
  
-   Версия проекта, связанная с экземпляром исполнения, устарела; может быть исполнена только последняя версия проекта  
  
  

