---
title: sp_sequence_get_range (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 08/08/2015
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_sequence_get_range
- sp_sequence_get_range_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, sp_sequence_get_range procedure
- sp_sequence_get_range
ms.assetid: 8ca6b0c6-8d9c-4eee-b02f-51ddffab4492
caps.latest.revision: 19
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: ad7851a091b531c0f13980023e22f4f2d545163b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="spsequencegetrange-transact-sql"></a>sp_sequence_get_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-asdw-xxx-md.md)]

  Возвращает диапазон значений последовательности из объекта последовательности. Объект последовательности создает и выдает запрошенное количество значений, а также предоставляет приложению метаданные, связанные с диапазоном.  
  
 Дополнительные сведения о порядковых номерах см. в разделе [порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_sequence_get_range [ @sequence_name = ] N'<sequence>'   
     , [ @range_size = ] range_size  
     , [ @range_first_value = ] range_first_value OUTPUT   
    [, [ @range_last_value = ] range_last_value OUTPUT ]  
    [, [ @range_cycle_count = ] range_cycle_count OUTPUT ]  
    [, [ @sequence_increment = ] sequence_increment OUTPUT ]  
    [, [ @sequence_min_value = ] sequence_min_value OUTPUT ]  
    [, [ @sequence_max_value = ] sequence_max_value OUTPUT ]  
    [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@sequence_name** =] **N**"*последовательность*"  
 Имя объекта последовательности. Схема является необязательной. *sequence_name* — **nvarchar(776)**.  
  
 [ **@range_size** =] *range_size*  
 Количество получаемых из последовательности значений. **@range_size** — **bigint**.  
  
 [ **@range_first_value** =] *range_first_value*  
 Выходной параметр возвращает первое (минимальное или максимальное) значение объекта последовательности, используемое для вычисления запрошенного диапазона. **@range_first_value** — **sql_variant** с тем же базовым типом, что и объект последовательности, которая используется в запросе.  
  
 [ **@range_last_value** = ] *range_last_value*  
 Необязательный выходной параметр возвращает последнее значение запрашиваемого диапазона. **@range_last_value** — **sql_variant** с тем же базовым типом, что и объект последовательности, которая используется в запросе.  
  
 [ **@range_cycle_count** =] range_cycle_count  
 Необязательный выходной параметр возвращает количество циклов объекта последовательности, которое потребовалось для возврата запрошенного диапазона. **@range_cycle_count** — **int**.  
  
 [ **@sequence_increment** =] *sequence_increment*  
 Необязательный выходной параметр возвращает приращение объекта последовательности, которое использовалось для вычисления запрошенного диапазона. **@sequence_increment** — **sql_variant** с тем же базовым типом, что и объект последовательности, которая используется в запросе.  
  
 [ **@sequence_min_value** =] *sequence_min_value*  
 Необязательный выходной параметр возвращает минимальное значение объекта последовательности. **@sequence_min_value** — **sql_variant** с тем же базовым типом, что и объект последовательности, которая используется в запросе.  
  
 [ **@sequence_max_value** =] *sequence_max_value*  
 Необязательный выходной параметр возвращает максимальное значение объекта последовательности. **@sequence_max_value** — **sql_variant** с тем же базовым типом, что и объект последовательности, которая используется в запросе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 sp_sequence_get_rangeis в sys. Схема и можно обращаться как sys.sp_sequence_get_range.  
  
### <a name="cycling-sequences"></a>Циклические последовательности  
 При необходимости объект последовательности может выполняться циклически требуемое число раз для обработки запрошенного диапазона. Количество циклов возвращается вызывающему методу через параметр `@range_cycle_count`.  
  
> [!NOTE]  
>  При циклическом выполнении объект последовательности перезапускается с минимального значения в возрастающей последовательности и с максимального в убывающей, а не с начального значения объекта последовательности.  
  
### <a name="non-cycling-sequences"></a>Нециклические последовательности  
 Если количество значений в запрашиваемом диапазоне больше остающегося количества доступных значений в объекте последовательности, то запрашиваемый диапазон не вычитается из объекта последовательности и возвращается следующее сообщение об ошибке 11732:  
  
 `The requested range for sequence object '%.*ls' exceeds the maximum or minimum limit. Retry with a smaller range.`  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение UPDATE для объекта последовательности или его схемы.  
  
## <a name="examples"></a>Примеры  
 В следующих примерах используется объект последовательности с именем Test.RangeSeq. Используйте следующую инструкцию для создания последовательности Test.RangeSeq.  
  
```  
CREATE SCHEMA Test ;  
GO  
  
CREATE SEQUENCE Test.RangeSeq  
    AS int   
    START WITH 1  
    INCREMENT BY 1  
    MINVALUE 1  
    MAXVALUE 25  
    CYCLE  
    CACHE 10  
;  
```  
  
### <a name="a-retrieving-a-range-of-sequence-values"></a>A. Получение диапазона значений последовательности  
 Следующая инструкция получает четыре порядковых номера из объекта Test.RangeSeq последовательности и возвращает первое из чисел пользователю.  
  
```  
DECLARE @range_first_value sql_variant ,   
        @range_first_value_output sql_variant ;  
  
EXEC sp_sequence_get_range  
@sequence_name = N'Test.RangeSeq'  
, @range_size = 4  
, @range_first_value = @range_first_value_output OUTPUT ;  
  
SELECT @range_first_value_output AS FirstNumber ;  
  
```  
  
### <a name="b-returning-all-output-parameters"></a>Б. Возврат всех выходных параметров  
 В следующем примере возвращается выходные значения из процедуры sp_sequence_get_range.  
  
```  
DECLARE    
  @FirstSeqNum sql_variant  
, @LastSeqNum sql_variant  
, @CycleCount int  
, @SeqIncr sql_variant  
, @SeqMinVal sql_variant  
, @SeqMaxVal sql_variant ;  
  
EXEC sys.sp_sequence_get_range  
@sequence_name = N'Test.RangeSeq'  
, @range_size = 5  
, @range_first_value = @FirstSeqNum OUTPUT   
, @range_last_value = @LastSeqNum OUTPUT   
, @range_cycle_count = @CycleCount OUTPUT  
, @sequence_increment = @SeqIncr OUTPUT  
, @sequence_min_value = @SeqMinVal OUTPUT  
, @sequence_max_value = @SeqMaxVal OUTPUT ;  
  
-- The following statement returns the output values  
SELECT  
  @FirstSeqNum AS FirstVal  
, @LastSeqNum AS LastVal  
, @CycleCount AS CycleCount  
, @SeqIncr AS SeqIncrement  
, @SeqMinVal AS MinSeq  
, @SeqMaxVal AS MaxSeq ;  
  
```  
  
 Если увеличить значение аргумента `@range_size`, например, до 75, то объект последовательности будет выполняться циклически. Проверьте по аргументу `@range_cycle_count`, выполнялся ли объект циклически и, если это так, сколько раз.  
  
### <a name="c-example-using-adonet"></a>В. Пример использования ADO.NET  
 Следующий пример возвращает диапазон из Test.RangeSeq с использованием ADO.NET.  
  
```  
SqlCommand cmd = new SqlCommand();  
cmd.Connection = conn;  
cmd.CommandType = CommandType.StoredProcedure;  
cmd.CommandText = "sys.sp_sequence_get_range";  
cmd.Parameters.AddWithValue("@sequence_name", "Test.RangeSeq");  
cmd.Parameters.AddWithValue("@range_size", 10);  
  
// Specify an output parameter to retreive the first value of the generated range.  
SqlParameter firstValueInRange = new SqlParameter("@range_first_value", SqlDbType.Variant);  
firstValueInRange.Direction = ParameterDirection.Output;  
cmd.Parameters.Add(firstValueInRange);  
  
conn.Open();  
cmd.ExecuteNonQuery();  
  
// Output the first value of the generated range.  
Console.WriteLine(firstValueInRange.Value);  
  
```  
  
## <a name="see-also"></a>См. также  
 [CREATE SEQUENCE (Transact-SQL)](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE (Transact-SQL)](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE (Transact-SQL)](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [NEXT VALUE FOR (Transact-SQL)](../../t-sql/functions/next-value-for-transact-sql.md)   
 [Порядковые номера](../../relational-databases/sequence-numbers/sequence-numbers.md)  
  
  
