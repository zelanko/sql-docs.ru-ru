---
title: "sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- sp_estimated_rowsize_reduction_for_vardecimal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_estimated_rowsize_reduction_for_vardecimal
- decimal data type, compressing
- numeric data type, compressing
- estimate decimal compression
- table compression [SQL Server]
ms.assetid: 0fe45983-f9f2-4c7f-938a-0fd96e1cbe8d
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bd67eb412ba93dd19a828963f2f10d0589d1987c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spestimatedrowsizereductionforvardecimal-transact-sql"></a>sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вычисляет уменьшение среднего размера строк, если в таблице включен формат хранения vardecimal. С помощью этого числа можно вычислить общее уменьшение размера таблицы. Поскольку для вычисления среднего уменьшения размера строки используется статистическая выборка, это значение следует рассматривать только как приблизительное. В редких случаях размер строки может увеличиваться после включения формата хранения vardecimal.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Пользуйтесь вместо этого сжатием ROW и PAGE. Дополнительные сведения см. в разделе [Data Compression](../../relational-databases/data-compression/data-compression.md). Сжатие влияет на размер таблиц и индексов, в разделе [sp_estimate_data_compression_savings &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_estimated_rowsize_reduction_for_vardecimal [ [ @table_name = ] 'table'] [;]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table=** ] **"***таблицы***"**  
 Трехкомпонентное имя таблицы, для которой изменяется формат хранения. *Таблица* — **nvarchar(776)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Приведенный ниже результирующий набор содержит сведения о текущем и вычисленном размере таблицы.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**avg_rowlen_fixed_format**|**Decimal (12, 2)**|Представляет длину строки в формате хранения fixed decimal.|  
|**avg_rowlen_vardecimal_format**|**Decimal (12, 2)**|Представляет средний размер строки при использовании формата хранения vardecimal.|  
|**row_count**|**int**|Количество строк в таблице.|  
  
## <a name="remarks"></a>Замечания  
 Используйте **sp_estimated_rowsize_reduction_for_vardecimal** можно вычислить экономию, которую дает Включение формата хранения vardecimal в таблице. Например, если средний размер строки можно уменьшить на 40%, то размер самой таблицы также можно потенциально уменьшить на 40%. Наличие экономии места зависит от коэффициента заполнения и размера строки. Например, если длина строки, составляющая 8 000 байт, уменьшается на 40%, то на странице данных все равно помещается только одна строка, что в результате не дает никакой экономии.  
  
 Если результаты **sp_estimated_rowsize_reduction_for_vardecimal** показывают, что размер таблицы будет увеличиваться, это означает, что множество строк в таблице используется почти полная точность типов данных decimal и Добавление небольшой объем затрат, необходимый для хранения vardecimal больше, чем экономия места от формата хранения vardecimal. В этом редком случае формат хранения vardecimal включать не следует.  
  
 Если таблицы включен формат хранения vardecimal, используйте **sp_estimated_rowsize_reduction_for_vardecimal** Чтобы вычислить Средний размер строки при отключении этого формата хранения vardecimal.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL на таблицу.  
  
## <a name="examples"></a>Примеры  
 В следующем примере вычисляется уменьшение размера строк при сжатии таблицы `Production.WorkOrderRouting` в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimated_rowsize_reduction_for_vardecimal 'Production.WorkOrderRouting' ;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_db_vardecimal_storage_format &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)   
 [sp_tableoption &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
