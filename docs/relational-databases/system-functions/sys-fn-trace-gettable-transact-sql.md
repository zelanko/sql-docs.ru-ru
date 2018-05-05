---
title: sys.fn_trace_gettable (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-functions
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- fn_trace_gettable
- fn_trace_gettable_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_trace_gettable function
- sys.fn_trace_gettable function
ms.assetid: c2590159-6ec5-4510-81ab-e935cc4216cd
caps.latest.revision: 35
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 54430ef6f0ecfd665069b4e7406a04d94ce39a05
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sysfntracegettable-transact-sql"></a>sys.fn_trace_gettable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает содержимое одного или нескольких файлов трассировки в табличном формате.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте расширенные события.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_trace_gettable ( 'filename' , number_files )  
```  
  
## <a name="arguments"></a>Аргументы  
 "*filename*"  
 Указывает первый считываемый файл трассировки. *Имя файла* — **nvarchar(256)**, не имеет значения по умолчанию.  
  
 *number_files*  
 Указывает число считываемых файлов продолжения. Это число включает и файл, указанный в *filename*. *number_files* — **int**.  
  
## <a name="remarks"></a>Замечания  
 Если *number_files* указывается как **по умолчанию**, **fn_trace_gettable** считывает файлы продолжения, пока не достигнет конца трассировки. **fn_trace_gettable** возвращает таблицу, содержащую все столбцы, допустимые для указанной трассировки. Дополнительные сведения см. в разделе [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md).  
  
 Имейте в виду, что функция fn_trace_gettable не будет загружать файлы продолжения (Если этот параметр указан с помощью *number_files* аргумент) которых имя исходного файла трассировки завершается подчеркиванием и числовым значением. (Это не относится к подчеркиваниям и числам, которые автоматически добавляются, когда выполняется переключение на файл продолжения.) В качестве временного решения можно переименовать файлы трассировки, исключив подчеркивания из имени исходного файла. Например, если исходный файл имеет имя **Trace_Oct_5.trc** и файл продолжения имеет имя **Trace_Oct_5_1.trc**, можно переименовать файлы **TraceOct5.trc** и  **TraceOct5_1.trc**.  
  
 Эта функция может считывать трассировку, которая еще активна на экземпляре, на котором она выполняется.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER TRACE на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-fntracegettable-to-import-rows-from-a-trace-file"></a>A. Применение функции fn_trace_gettable для импорта строк из файла трассировки  
 В следующем примере функция `fn_trace_gettable` вызывается в предложении `FROM` инструкции `SELECT...INTO`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
### <a name="b-using-fntracegettable-to-return-a-table-with-an-identity-column-that-can-be-loaded-into-a-sql-server-table"></a>Б. Получение с помощью функции fn_trace_gettable таблицы со столбцом IDENTITY, которая может быть загружена в таблицу SQL Server  
 Следующий пример вызывает функцию из инструкции `SELECT...INTO` и возвращает таблицу со столбцом `IDENTITY`, которая может быть загружена в таблицу `temp_trc`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENTITY(int, 1, 1) AS RowNumber, * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимая процедура sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [Хранимая процедура sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
