---
title: sys. fn_trace_gettable (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 4d1bc18704b4f2b239fe590184d58289d66b35fc
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898285"
---
# <a name="sysfn_trace_gettable-transact-sql"></a>sys.fn_trace_gettable (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Возвращает содержимое одного или нескольких файлов трассировки в табличном формате.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Вместо этого используйте расширенные события.  
   
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_trace_gettable ( 'filename' , number_files )  
```  
  
## <a name="arguments"></a>Аргументы  
 "*ИмяФайла*"  
 Указывает первый считываемый файл трассировки. *filename* имеет тип **nvarchar (256)** и не имеет значения по умолчанию.  
  
 *number_files*  
 Указывает число считываемых файлов продолжения. Это число включает исходный файл, указанный в поле *filename*. *number_files* является типом **int**.  
  
## <a name="remarks"></a>Комментарии  
 Если *number_files* указан в качестве **значения по умолчанию**, **fn_trace_gettable** считывает все файлы продолжения, пока не достигнет конца трассировки. **fn_trace_gettable** возвращает таблицу со всеми столбцами, допустимыми для указанной трассировки. Дополнительные сведения см. в разделе [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md).  
  
 Имейте в виду, что функция fn_trace_gettable не будет загружать файлы продолжения (если этот параметр указан с помощью аргумента *number_files* ), где исходное имя файла трассировки заканчивается символом подчеркивания и числовым значением. (Это не относится к символам подчеркивания и номеру, которые автоматически добавляются при пересчете файла.) В качестве обходного решения можно переименовать файлы трассировки, чтобы удалить символы подчеркивания в исходном имени файла. Например, если исходный файл называется **Trace_Oct_5. trc** , а файл продолжения имеет имя **Trace_Oct_5_1. trc**, можно переименовать файлы в **TraceOct5. trc** и **TraceOct5_1. trc**.  
  
 Эта функция может считывать трассировку, которая еще активна на экземпляре, на котором она выполняется.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER TRACE на сервере.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-fn_trace_gettable-to-import-rows-from-a-trace-file"></a>A. Применение функции fn_trace_gettable для импорта строк из файла трассировки  
 В следующем примере функция `fn_trace_gettable` вызывается в предложении `FROM` инструкции `SELECT...INTO`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
### <a name="b-using-fn_trace_gettable-to-return-a-table-with-an-identity-column-that-can-be-loaded-into-a-sql-server-table"></a>Б. Получение с помощью функции fn_trace_gettable таблицы со столбцом IDENTITY, которая может быть загружена в таблицу SQL Server  
 Следующий пример вызывает функцию из инструкции `SELECT...INTO` и возвращает таблицу со столбцом `IDENTITY`, которая может быть загружена в таблицу `temp_trc`.  
  
```  
USE AdventureWorks2012;  
GO  
SELECT IDENTITY(int, 1, 1) AS RowNumber, * INTO temp_trc  
FROM fn_trace_gettable('c:\temp\mytrace.trc', default);  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [Хранимая процедура sp_trace_setstatus (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)  
  
  
