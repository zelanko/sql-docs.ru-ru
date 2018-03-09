---
title: "sys.fn_get_sql (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fn_get_sql
- sys.fn_get_sql_TSQL
- fn_get_sql_TSQL
- sys.fn_get_sql
dev_langs:
- TSQL
helpviewer_keywords:
- fn_get_sql function
- text [SQL Server], SQL handles
- sys.fn_get_sql function
- valid SQL handles [SQL Server]
- SQL handles
ms.assetid: d5fe49b5-0813-48f2-9efb-9187716b2fd4
caps.latest.revision: 
author: rothja
ms.author: jroth
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 941417a97ce739173e2aba195d51ec845848186f
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/09/2018
---
# <a name="sysfngetsql-transact-sql"></a>sys.fn_get_sql (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает текст инструкции SQL для указанного дескриптора SQL.  
  
> [!IMPORTANT]  
>  В будущей версии Microsoft SQL Server этот компонент будет удален. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо нее используйте sys.dm_exec_sql_text. Дополнительные сведения см. в разделе [sys.dm_exec_sql_text &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md).  
  
 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_get_sql ( SqlHandle )  
```  
  
## <a name="arguments"></a>Аргументы  
 *SqlHandle*  
 Значение дескриптора. *SqlHandle* — **varbinary(64)** без значения по умолчанию.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|dbid|**smallint**|Идентификатор базы данных. Для нерегламентированных и подготовленных инструкций SQL это идентификатор базы данных, в которой происходила компиляция инструкции.|  
|objectid|**int**|Идентификатор объекта базы данных. Имеет значение NULL для нерегламентированных инструкций SQL.|  
|number|**smallint**|Указывает на номер группы, если процедуры сгруппированы.<br /><br /> 0 = записи не являются процедурами.<br /><br /> NULL = нерегламентированные инструкции SQL.|  
|encrypted|**бит**|Указывает, зашифрован ли объект.<br /><br /> 0 = не зашифрована<br /><br /> 1 = зашифрована|  
|text|**text**|Текст инструкции SQL. Имеет значение NULL для зашифрованных объектов.|  
  
## <a name="remarks"></a>Remarks  
 Допустимый дескриптор SQL можно получить из столбца sql_handle [sys.dm_exec_requests &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) динамическое административное представление.  
  
 Если передается дескриптор, больше не существует в кэше, функция fn_get_sq**l** возвращает пустой результирующий набор. Если передается недопустимый дескриптор, выполнение пакета прекращается и возвращается сообщение об ошибке.  
  
 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] При кэшировании некоторые [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции, такие как инструкции массового копирования и инструкции со строковыми литералами, размер которых превышает 8 КБ. Дескрипторы этих инструкций не могут быть извлечены при помощи функции fn_get_sql.  
  
 **Текст** столбца результирующего набора фильтруется по тексту, который может содержать пароли. Дополнительные сведения о безопасности, связанным хранимых процедур, которые не контролируются, см. [фильтра трассировки](../../relational-databases/sql-trace/filter-a-trace.md).  
  
 Функция fn_get_sql возвращает сведения об ошибке [DBCC INPUTBUFFER](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md) команды. Ниже приведены случаи, когда функцию fn_get_sql использовать можно, а команду DBCC INPUTBUFFER — нельзя:  
  
-   если событие содержит более чем 255 символов;  
  
-   если необходимо получить наивысший из текущих уровней вложенности хранимой процедуры. Например, есть две хранимые процедуры с именами sp_1 и sp_2. Если процедура sp_1 вызывает процедуру sp_2 и вы получаете дескриптор из динамического административного представления sys.dm_exec_requests во время выполнения процедуры sp_2, функция fn_get_sql возвращает сведения о процедуре sp_2. Кроме того, функция fn_get_sql возвращает полный текст хранимой процедуры на высшем текущем уровне вложенности.  
  
## <a name="permissions"></a>Разрешения  
 Пользователю необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="examples"></a>Примеры  
 Администраторы базы данных могут использовать функцию fn_get_sql, как показано в следующем примере, для облегчения диагностики проблемных процессов. После того как администратор находит проблемный идентификатор сеанса, он может получить дескриптор SQL для идентификатора сеанса, вызвать функцию n_get_sql, используя дескриптор, и после этого определить текст SQL проблемного идентификатора сеанса.  
  
```  
DECLARE @Handle varbinary(64);  
SELECT @Handle = sql_handle   
FROM sys.dm_exec_requests   
WHERE session_id = 52 and request_id = 0;  
SELECT * FROM sys.fn_get_sql(@Handle);  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Инструкция DBCC INPUTBUFFER &#40; Transact-SQL &#41;](../../t-sql/database-console-commands/dbcc-inputbuffer-transact-sql.md)   
 [sys.sysprocesses &#40; Transact-SQL &#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  
