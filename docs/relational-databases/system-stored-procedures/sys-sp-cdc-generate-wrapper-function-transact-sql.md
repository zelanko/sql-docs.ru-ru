---
description: sys.sp_cdc_generate_wrapper_function (Transact-SQL)
title: sys. sp_cdc_generate_wrapper_function (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cdc_generate_wrapper_function_TSQL
- sp_cdc_generate_wrapper_function
- sys.sp_cdc_generate_wrapper_function_TSQL
- sys.sp_cdc_generate_wrapper_function
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_cdc_generate_wrapper_function
- sp_cdc_generate_wrapper_function
ms.assetid: 85bc086d-8a4e-4949-a23b-bf53044b925c
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7f54e99cd49c487dba0f008661da8a01d4efb837
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473445"
---
# <a name="syssp_cdc_generate_wrapper_function-transact-sql"></a>sys.sp_cdc_generate_wrapper_function (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Формирует скрипты для создания функций-оболочек для функций запроса к системе отслеживания измененных данных, имеющихся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. API-интерфейс, который поддерживается в формируемых оболочках, позволяет указать интервал запроса как интервал datetime. Поэтому такую функцию полезно использовать во многих приложениях хранилищ данных, включая разработанные создателями пакета служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], использовавшими технологию системы отслеживания измененных данных для определения добавочной нагрузки.  
  
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
 [ @capture_instance =] "*capture_instance*"  
 Экземпляр отслеживания, для которого будут формироваться скрипты. *capture_instance* имеет тип **sysname** и имеет значение по умолчанию NULL. Если его значение пропущено либо явно определено как NULL, скрипты оболочки формируются для всех экземпляров отслеживания.  
  
 [ @closed_high_end_point =] *high_end_pt_flag*  
 Битовый флаг, указывающий, подлежат ли изменения, зафиксированные в момент времени, совпадающий с верхней конечной точкой, включению сформированной процедурой в интервал извлечения. *high_end_pt_flag* имеет **бит** и имеет значение по умолчанию 1, которое указывает, что конечная точка должна быть включена. Значение 0 указывает на то, что все значения времени фиксации должны быть строго меньше верхней конечной точки.  
  
 [ @column_list =] "*column_list*"  
 Список отслеживаемых столбцов, подлежащих включению в результирующий набор, возвращаемый функцией-оболочкой. *column_list* имеет тип **nvarchar (max)** и имеет значение по умолчанию NULL. При значении NULL включаются все отслеживаемые столбцы.  
  
 [ @update_flag_list =] "*update_flag_list*"  
 Список включаемых столбцов, флаг обновления для которых включается в результирующий набор, возвращаемый функцией-оболочкой. *update_flag_list* имеет тип **nvarchar (max)** и имеет значение по умолчанию NULL. При значении NULL флаги обновления не включаются.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип столбца|Описание|  
|-----------------|-----------------|-----------------|  
|**function_name**|**nvarchar (145)**|Имя формируемой функции.|  
|**create_script**|**nvarchar(max)**|Скрипт, создающий функцию-оболочку экземпляра отслеживания.|  
  
## <a name="remarks"></a>Комментарии  
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
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры системы отслеживания измененных данных (Transact-SQL)](../../relational-databases/system-stored-procedures/change-data-capture-stored-procedures-transact-sql.md)   
 [Система отслеживания измененных данных &#40;служб SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md)  
  
  
