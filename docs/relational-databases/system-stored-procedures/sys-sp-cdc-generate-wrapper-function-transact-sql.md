---
title: "sys.sp_cdc_generate_wrapper_function (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_cdc_generate_wrapper_function_TSQL
- sp_cdc_generate_wrapper_function
- sys.sp_cdc_generate_wrapper_function_TSQL
- sys.sp_cdc_generate_wrapper_function
dev_langs: TSQL
helpviewer_keywords:
- sys.sp_cdc_generate_wrapper_function
- sp_cdc_generate_wrapper_function
ms.assetid: 85bc086d-8a4e-4949-a23b-bf53044b925c
caps.latest.revision: "11"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bbadba2128bad803f56d3b1665332c48eb999beb
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="sysspcdcgeneratewrapperfunction-transact-sql"></a>sys.sp_cdc_generate_wrapper_function (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Формирует скрипты для создания функций-оболочек для функций запроса к системе отслеживания измененных данных, имеющихся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. API-интерфейс, который поддерживается в формируемых оболочках, позволяет указать интервал запроса как интервал datetime. Поэтому такую функцию полезно использовать во многих приложениях хранилищ данных, включая разработанные создателями пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], использовавшими технологию системы отслеживания измененных данных для определения добавочной нагрузки.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.sp_cdc_generate_wrapper_function  
    [ [ @capture_instance sysname = ] 'capture_instance'  
    [ , [ @closed_high_end_point = ] closed_high_end_pt  
    [ , [ @column_list = ] 'column_list'  
```  
  
```  
  
[ , [ @update_flag_list = ] 'update_flag_list'  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @capture_instance=] '*capture_instance*"  
 Экземпляр отслеживания, для которого будут формироваться скрипты. *capture_instance* — **sysname** и имеет значение по умолчанию NULL. Если его значение пропущено либо явно определено как NULL, скрипты оболочки формируются для всех экземпляров отслеживания.  
  
 [ @closed_high_end_point=] *high_end_pt_flag*  
 Битовый флаг, указывающий, подлежат ли изменения, зафиксированные в момент времени, совпадающий с верхней конечной точкой, включению сформированной процедурой в интервал извлечения. *high_end_pt_flag* — **бит** и имеет значение по умолчанию 1, означающее, что конечная точка должны быть включены. Значение 0 указывает на то, что все значения времени фиксации должны быть строго меньше верхней конечной точки.  
  
 [ @column_list=] '*column_list*"  
 Список отслеживаемых столбцов, подлежащих включению в результирующий набор, возвращаемый функцией-оболочкой. *column_list* — **nvarchar(max)** и имеет значение по умолчанию NULL. При значении NULL включаются все отслеживаемые столбцы.  
  
 [ @update_flag_list=] '*update_flag_list*"  
 Список включаемых столбцов, флаг обновления для которых включается в результирующий набор, возвращаемый функцией-оболочкой. *update_flag_list* — **nvarchar(max)** и имеет значение по умолчанию NULL. При значении NULL флаги обновления не включаются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип столбца|Description|  
|-----------------|-----------------|-----------------|  
|**имя функции**|**nvarchar(145)**|Имя формируемой функции.|  
|**create_script**|**nvarchar(max)**|Скрипт, создающий функцию-оболочку экземпляра отслеживания.|  
  
## <a name="remarks"></a>Замечания  
 Скрипт, создающий функцию-оболочку для запроса всех изменений на экземпляре отслеживания, формируется обязательно. Если экземпляр отслеживания поддерживает запросы сетевых изменений, также формируется скрипт создания оболочки для такого запроса.  
  
## <a name="examples"></a>Примеры  
 В следующем примере показано, как использовать системную хранимую процедуру `sys.sp_cdc_generate_wrapper_function` для создания оболочек для всех функций системы отслеживания измененных данных.  
  
```  
DECLARE @wrapper_functions TABLE (  
    function_name sysname,  
    create_script nvarchar(max));  
  
INSERT INTO @wrapper_functions  
EXEC sys.sp_cdc_generate_wrapper_function;  
  
DECLARE @create_script nvarchar(max);  
DECLARE #hfunctions CURSOR LOCAL fast_forward  
FOR   
    SELECT create_script FROM @wrapper_functions;  
  
OPEN #hfunctions;  
FETCH #hfunctions INTO @create_script;  
WHILE (@@fetch_status <> -1)  
BEGIN  
    EXEC sp_executesql @create_script  
    FETCH #hfunctions INTO @create_script  
END;  
  
CLOSE #hfunctions;  
DEALLOCATE #hfunctions;  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры системы отслеживания измененных данных (Transact-SQL)](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [Отслеживание изменений в данных &#40; Службы SSIS &#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md)  
  
  
