---
title: sp_cursorprepare (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_prepare
ms.assetid: 6207e110-f4bf-4139-b3ec-b799c9cb3ad7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2719e330ec2fde61b91ca11ef93784983c6c418c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74165909"
---
# <a name="sp_cursorprepare-transact-sql"></a>sp_cursorprepare (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Компилирует инструкцию или пакет курсора в план выполнения, но не создает курсор. Скомпилированная инструкция может позже использоваться процедурой sp_cursorexecute. Эта процедура в сочетании с sp_cursorexecute имеет ту же функцию, что и sp_cursoropen, но разбивается на две фазы. sp_cursorprepare вызывается путем указания ID = 3 в пакете потока табличных данных (TDS).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursorprepare prepared_handle OUTPUT, params , stmt , options  
    [ , scrollopt[ , ccopt]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *prepared_handle*  
 Созданный SQL Server подготовленный идентификатор *обработчика* , который возвращает целочисленное значение.  
  
> [!NOTE]  
>  для открытия курсора *prepared_handle* впоследствии предоставляется процедура sp_cursorexecute. Когда дескриптор создан, он существует до выхода пользователя из системы или до тех пор, пока не будет явным образом удален с помощью процедуры sp_cursorunprepare.  
  
 *params*  
 Указывает параметризованные инструкции. Определение переменных *params* подставляется для маркеров параметров в инструкции. *params* — это обязательный параметр, который вызывает для входного значения **ntext**, **nchar**или **nvarchar** . Если инструкция не параметризована, необходимо ввести значение NULL.  
  
> [!NOTE]  
>  Используйте строку **ntext** в качестве входного значения при параметризованной инструкции *stmt* и значения *scrollopt* PARAMETERIZED_STMT.  
  
 *stmt*  
 Определяет результирующий набор курсора. Параметр *stmt* является обязательным и вызывает для входного значения **ntext**, **nchar** или **nvarchar** .  
  
> [!NOTE]  
>  Правила указания значения *stmt* те же, что и для sp_cursoropen, за исключением того, что строкой типа данных *stmt* должен быть **ntext**.  
  
 *Параметры*  
 Необязательный параметр, возвращающий описание столбцов результирующего набора курсора. для *параметров* требуется следующее входное значение **int** .  
  
|Значение|Description|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 Параметр прокрутки. *scrollopt* — это необязательный параметр, для которого требуется одно из следующих входных значений **int** .  
  
|Значение|Description|  
|-----------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
|0x10|FAST_FORWARD|  
|0x1000|PARAMETERIZED_STMT|  
|0x2000|AUTO_FETCH|  
|0x4000|AUTO_CLOSE|  
|0x8000|CHECK_ACCEPTED_TYPES|  
|0x10000|KEYSET_ACCEPTABLE|  
|0x20000|DYNAMIC_ACCEPTABLE|  
|0x40000|FORWARD_ONLY_ACCEPTABLE|  
|0x80000|STATIC_ACCEPTABLE|  
|0x100000|FAST_FORWARD_ACCEPTABLE|  
  
 Так как запрошенное значение может не подойти для курсора, определенного аргументом *stmt*, этот параметр выступает в качестве входных и выходных данных. В таких случаях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присваивает соответствующее значение.  
  
 *ccopt*  
 Параметр управления параллелизмом. *ccopt* — это необязательный параметр, для которого требуется одно из следующих входных значений **int** .  
  
|Значение|Description|  
|-----------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS (прежнее название — LOCKCC)|  
|0x0004|**Оптимистичный** (ранее известный как опткк)|  
|0x0008|OPTIMISTIC (прежнее название — OPTCCVAL)|  
|0x2000|ALLOW_DIRECT|  
|0x4000|UPDT_IN_PLACE|  
|0x8000|CHECK_ACCEPTED_OPTS|  
|0x10000|READ_ONLY_ACCEPTABLE|  
|0x20000|SCROLL_LOCKS_ACCEPTABLE|  
|0x40000|OPTIMISTIC_ACCEPTABLE|  
|0x80000|OPTIMISTIC_ACCEPTABLE|  
  
 Как и ** в случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с скроллпт, может назначить другое значение из запрошенного.  
  
## <a name="remarks"></a>Remarks  
 Параметр состояния RPC может иметь следующие значения.  
  
|Значение|Description|  
|-----------|-----------------|  
|0|Успех|  
|0x0001|Отказ|  
|1FF6|Невозможно вернуть метаданные.<br /><br /> Примечание. Причина в том, что инструкция не создает результирующий набор; Например, это инструкция INSERT или DDL.|  
  
## <a name="examples"></a>Примеры  
  Ниже приведен пример использования sp_cursorprepare и sp_cursorexecute

```sql
declare @handle int , @p5 int, @p6 int
exec sp_cursorprepare @handle OUTPUT, 
    N'@dbid int', 
    N'select * from sys.databases where database_id < @dbid',
    1,
    @p5 output,
    @p6 output


declare @p1 int  
set @P1 = @handle 
declare @p2 int   
declare @p3 int  
declare @p4 int  
set @P6 = 4 
exec sp_cursorexecute @p1, @p2 OUTPUT, @p3 output , @p4 output, @p5 OUTPUT, @p6

exec sp_cursorfetch @P2

exec sp_cursorunprepare @handle
exec sp_cursorclose @p2
```
 
 Если параметр *stmt* является параметризованным, а PARAMETERIZED_STMT *SCROLLOPT* имеет значение ON, формат строки выглядит следующим образом:  
  
 { * \<имя локальной переменной> * *\<тип данных>* } [ ,... *n* ]  
  
## <a name="see-also"></a>См. также:  
 [sp_cursorexecute &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorunprepare &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorunprepare-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
