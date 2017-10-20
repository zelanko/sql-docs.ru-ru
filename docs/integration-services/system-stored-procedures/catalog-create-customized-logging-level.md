---
title: "Catalog.create_customized_logging_level | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 20b3ba0a-126f-49bf-b70f-61b2a0fcb750
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 126fa0af811033bb0be035b1f4c550620c696bb3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreatecustomizedlogginglevel"></a>Catalog.create_customized_logging_level
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Создает новый пользовательский уровень ведения журнала. Дополнительные сведения о пользовательских уровней ведения журнала см. в разделе [службы Integration Services &#40; Службы SSIS &#41; Ведение журнала](../../integration-services/performance/integration-services-ssis-logging.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
catalog.create_customized_logging_level [ @level_name = ] level_name  
    , [ @level_description = ] level_description  
    , [ @profile_value = ] profile_value  
    , [ @event_value = ] event_value  
    , [ @level_id = ] level_id OUT   
```  
  
## <a name="arguments"></a>Аргументы  
 [ @level_name =] *level_name*  
 Имя для нового существующий пользовательский уровень ведения журнала.  
  
 *Level_name* — **nvarchar(128)**.  
  
 [ @level_description =] *level_description*  
 Описание для нового существующий пользовательский уровень ведения журнала.  
  
 *Level_description* — **nvarchar(1024)**.  
  
 [ @profile_value =] *profile_value*  
 Статистические данные, что требуется новый пользовательский уровень ведения журнала для входа.  
  
 Ниже представлены допустимые значения для статистики. Эти значения соответствуют значениям на **статистики** вкладке **настроить управление** диалоговое окно.  
  
-   Выполнение = 0  
  
-   Тома = 1  
  
-   Производительность = 2  
  
 *Profile_value* — **bigint**.  
  
 [ @event_value =] *event_value*  
 События, что требуется новый пользовательский уровень ведения журнала для входа.  
  
 Ниже представлены допустимые значения для события. Эти значения соответствуют значениям на **событий** вкладке **настроить управление** диалоговое окно.  
  
|События без контекста события|События с контекст событий|  
|----------------------------------|-------------------------------|  
|OnVariableValueChanged = 0<br /><br /> OnExecutionStatusChanged = 1<br /><br /> OnPreExecute = 2<br /><br /> OnPostExecute = 3<br /><br /> OnPreValidate = 4<br /><br /> OnPostValidate = 5<br /><br /> OnWarning = 6<br /><br /> OnInformation = 7<br /><br /> OnError = 8<br /><br /> OnTaskFailed = 9<br /><br /> OnProgress = 10<br /><br /> OnQueryCancel = 11<br /><br /> OnBreakpointHit = 12<br /><br /> OnCustomEvent = 13<br /><br /> Диагностические = 14<br /><br /> DiagnosticEx = 15<br /><br /> NonDiagnostic = 16|OnVariableValueChanged_IncludeContext = 32<br /><br /> OnExecutionStatusChanged_IncludeContext = 33<br /><br /> OnPreExecute_IncludeContext = 34<br /><br /> OnPostExecute_IncludeContext = 35<br /><br /> OnPreValidate_IncludeContext = 36<br /><br /> OnPostValidate_IncludeContext = 37<br /><br /> OnWarning_IncludeContext = 38<br /><br /> OnInformation_IncludeContext = 39<br /><br /> OnError_IncludeContext = 40<br /><br /> OnTaskFailed_IncludeContext = 41<br /><br /> OnProgress_IncludeContext = 42<br /><br /> OnQueryCancel_IncludeContext = 43<br /><br /> OnBreakpointHit_IncludeContext = 44<br /><br /> OnCustomEvent_IncludeContext = 45<br /><br /> Diagnostic_IncludeContext = 46<br /><br /> DiagnosticEx_IncludeContext = 47<br /><br /> NonDiagnostic_IncludeContext = 48|  
  
 *Event_value* — **bigint**.  
  
 [ @level_id =] *level_id* OUT  
 Идентификатор нового пользовательский уровень ведения журнала.  
  
 *Level_id* — **bigint**.  
  
## <a name="remarks"></a>Замечания  
 Объединение нескольких значений в Transact-SQL для *profile_value* или *event_value* аргумент, выполните в этом примере. Чтобы зафиксировать OnError (8) и события DiagnosticEx (15), формула для вычисления *event_value* — `2^8 + 2^15 = 33024`.  
  
## <a name="return-codes"></a>Коды возврата  
 0 (успешное завершение)  
  
 В случае отказа хранимой процедуры выдается ошибка.  
  
## <a name="result-set"></a>Результирующий набор  
 Нет  
  
## <a name="permissions"></a>Permissions  
 Эта хранимая процедура требует применения одного из следующих разрешений:  
  
-   Членство в роли базы данных **ssis_admin**  
  
-   Членство в роли сервера **sysadmin**  
  
## <a name="errors-and-warnings"></a>Ошибки и предупреждения  
 В следующем списке описываются условия, приводящие к сбою хранимой процедуры.  
  
-   Пользователь не имеет необходимых разрешений.  
  
  
