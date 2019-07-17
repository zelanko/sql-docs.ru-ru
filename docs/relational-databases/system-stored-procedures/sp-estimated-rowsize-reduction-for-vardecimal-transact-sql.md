---
title: sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90de7b95febdf2f1a25a5e584b2ca77bb67f93d4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124514"
---
# <a name="spestimatedrowsizereductionforvardecimal-transact-sql"></a>sp_estimated_rowsize_reduction_for_vardecimal (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Вычисляет уменьшение среднего размера строк, если в таблице включен формат хранения vardecimal. С помощью этого числа можно вычислить общее уменьшение размера таблицы. Поскольку для вычисления среднего уменьшения размера строки используется статистическая выборка, это значение следует рассматривать только как приблизительное. В редких случаях размер строки может увеличиваться после включения формата хранения vardecimal.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Пользуйтесь вместо этого сжатием ROW и PAGE. Дополнительные сведения см. в разделе [Data Compression](../../relational-databases/data-compression/data-compression.md). Сжатие влияет на размер таблиц и индексов, см. в разделе [sp_estimate_data_compression_savings &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-estimate-data-compression-savings-transact-sql.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_estimated_rowsize_reduction_for_vardecimal [ [ @table_name = ] 'table'] [;]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @table = ] 'table'` Является трехкомпонентное имя таблицы, для которого необходимо изменить формат хранения. *Таблица* — **nvarchar(776)** .  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
 Приведенный ниже результирующий набор содержит сведения о текущем и вычисленном размере таблицы.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**avg_rowlen_fixed_format**|**Decimal ("12", "2")**|Представляет длину строки в формате хранения fixed decimal.|  
|**avg_rowlen_vardecimal_format**|**Decimal ("12", "2")**|Представляет средний размер строки при использовании формата хранения vardecimal.|  
|**row_count**|**int**|Количество строк в таблице.|  
  
## <a name="remarks"></a>Примечания  
 Используйте **sp_estimated_rowsize_reduction_for_vardecimal** оценить экономию, которую при включении таблицы формат хранения vardecimal. Например, если средний размер строки можно уменьшить на 40%, то размер самой таблицы также можно потенциально уменьшить на 40%. Наличие экономии места зависит от коэффициента заполнения и размера строки. Например, если длина строки, составляющая 8 000 байт, уменьшается на 40%, то на странице данных все равно помещается только одна строка, что в результате не дает никакой экономии.  
  
 Если результаты **sp_estimated_rowsize_reduction_for_vardecimal** показывают, что размер таблицы будет увеличиваться, это означает, что множество строк в таблице использовать почти полная точность типов данных decimal и Добавление небольшой объем затрат, необходимый для формата хранения vardecimal больше, чем экономия места от формата хранения vardecimal. В этом редком случае формат хранения vardecimal включать не следует.  
  
 Если таблицы включен формат хранения vardecimal, используйте **sp_estimated_rowsize_reduction_for_vardecimal** позволяет оценить Средний размер строки формата хранения vardecimal отключено.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL на таблицу.  
  
## <a name="examples"></a>Примеры  
 В следующем примере вычисляется уменьшение размера строк при сжатии таблицы `Production.WorkOrderRouting` в базе данных `AdventureWorks2012`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_estimated_rowsize_reduction_for_vardecimal 'Production.WorkOrderRouting' ;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_db_vardecimal_storage_format &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-db-vardecimal-storage-format-transact-sql.md)   
 [sp_tableoption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-tableoption-transact-sql.md)  
  
  
