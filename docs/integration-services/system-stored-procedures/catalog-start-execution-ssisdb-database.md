---
title: catalog.start_execution (база данных SSISDB) | Документы Майкрософт
ms.custom: ''
ms.date: 12/16/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: ''
ms.topic: language-reference
ms.assetid: f8663ff3-aa98-4dd8-b850-b21efada0b87
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7ffacadf9ed93c4af75f1ba70aa7e37591604a5d
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35406966"
---
# <a name="catalogstartexecution-ssisdb-database"></a>catalog.start_execution (база данных SSISDB)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Запускает экземпляр выполнения в каталоге служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.start_execution [@execution_id =] execution_id [, [@retry_count =] retry_count]  
```  
  
## <a name="arguments"></a>Аргументы  
 [@execution_id =] *execution_id*  
 Уникальный идентификатор для экземпляра выполнения. Параметр *execution_id* имеет тип **bigint**.
 
 [@retry_count =] *retry_count*  
 Число повторных попыток при сбое выполнения. Применяется только при выполнении в Scale Out. Этот параметр является необязательным. Если параметр не задан, используется значение 0. Параметр *retry_count* имеет тип **int**.
  
## <a name="remarks"></a>Remarks  
 Выполнение применяется для задания значений параметров, которые используются пакетом в течение одного экземпляра выполнения пакета. После создания экземпляра исполнения и до его начала соответствующий проект должен быть повторно развернут. В этом случае экземпляр исполнения ссылается на устаревший проект. Эта недопустимая ссылка приводит к сбою хранимой процедуры.  
  
> [!NOTE]  
>  Исполнения можно начинать только один раз. Чтобы запустить экземпляр выполнения, он должен быть создан (значение `1` в столбце **status** представления [catalog.operations](../../integration-services/system-views/catalog-operations-ssisdb-database.md)).  
  
## <a name="example"></a>Пример  
 В следующем примере выполняется вызов catalog.create_execution для создания экземпляра выполнения пакета Child1.dtsx. Проект Project1 служб Integration Services содержит пакет. В этом примере выполняется вызов catalog.set_execution_parameter_value для задания значений для параметров Parameter1, Parameter2 и LOGGING_LEVEL. В этом примере выполняется вызов catalog.start_execution для запуска экземпляра выполнения.  
  
```sql
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
 None  
  
## <a name="permissions"></a>Разрешения  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Разрешения READ и MODIFY на экземпляр выполнения, разрешения READ и EXECUTE на проект и, при необходимости, разрешения READ на среду, указанную в ссылке  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 Следующий список содержит описания некоторых условий, которые могут вызвать ошибку или предупреждение.  
  
-   Пользователь не имеет соответствующих разрешений  
  
-   Недопустимый идентификатор выполнения  
  
-   Исполнение уже началось или уже завершилось; исполнения могут начаться только один раз  
  
-   Связанная с проектом ссылка на среду недействительна  
  
-   Требуемые значения параметра не заданы  
  
-   Версия проекта, связанная с экземпляром исполнения, устарела; может быть исполнена только последняя версия проекта  
  
  
