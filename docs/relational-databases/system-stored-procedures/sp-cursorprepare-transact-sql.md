---
title: sp_cursorprepare (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepare_TSQL
- sp_cursor_prepare
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_prepare
ms.assetid: 6207e110-f4bf-4139-b3ec-b799c9cb3ad7
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: b616b58f13845c06dbc6510e2d4ca28dee744192
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33239844"
---
# <a name="spcursorprepare-transact-sql"></a>sp_cursorprepare (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Компилирует инструкцию или пакет курсора в план выполнения, но не создает курсор. Скомпилированная инструкция может позже использоваться процедурой sp_cursorexecute. Эта процедура в сочетании с sp_cursorexecute, делает то же самое, что процедура sp_cursoropen, но обработка разбита на два этапа. sp_cursorprepare вызывается указанием ID = 3 в пакете потока табличных данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursorprepare prepared_handle OUTPUT, params , stmt , options  
    [ , scrollopt[ , ccopt]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *prepared_handle*  
 Созданный системой SQL Server подготовленных *обработки* идентификатор, который возвращает целочисленное значение.  
  
> [!NOTE]  
>  *prepared_handle* затем передается процедуре sp_cursorexecute для открытия курсора. Когда дескриптор создан, он существует до выхода пользователя из системы или до тех пор, пока не будет явным образом удален с помощью процедуры sp_cursorunprepare.  
  
 *Params*  
 Указывает параметризованные инструкции. *Params* определение переменных подставляется вместо маркеров параметров в инструкции. *params* является обязательным параметром, который вызывает для **ntext**, **nchar**, или **nvarchar** входного значения. Если инструкция не параметризована, необходимо ввести значение NULL.  
  
> [!NOTE]  
>  Используйте **ntext** строку в качестве входных данных значения при *stmt* параметризован и *scrollopt* значение PARAMETERIZED_STMT имеет значение ON.  
  
 *инструкции*  
 Определяет результирующий набор курсора. *Stmt* параметр является обязательным и требует **ntext**, **nchar** или **nvarchar** входного значения.  
  
> [!NOTE]  
>  Правила для указания *stmt* значения, аналогичные действиям для sp_cursoropen, за исключением того, *stmt* строковый тип данных должен быть **ntext**.  
  
 *Параметры*  
 Необязательный параметр, возвращающий описание столбцов результирующего набора курсора. *Параметры* требуются следующие **int** входного значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 Параметр прокрутки. *scrollopt* является необязательным параметром требует одного из следующих **int** входных значений.  
  
|Значение|Описание|  
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
  
 Так как запрошенное значение не подходить для курсора определяется *stmt*, этот параметр используется как ввод и вывод. В таких случаях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] присваивает соответствующее значение.  
  
 *ccopt*  
 Параметр управления параллелизмом. *ccopt* является необязательным параметром требует одного из следующих **int** входных значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS (прежнее название — LOCKCC)|  
|0x0004|**ОПТИМИСТИЧЕСКИЙ** (прежнее название — OPTCC)|  
|0x0008|OPTIMISTIC (прежнее название — OPTCCVAL)|  
|0x2000|ALLOW_DIRECT|  
|0x4000|UPDT_IN_PLACE|  
|0x8000|CHECK_ACCEPTED_OPTS|  
|0x10000|READ_ONLY_ACCEPTABLE|  
|0x20000|SCROLL_LOCKS_ACCEPTABLE|  
|0x40000|OPTIMISTIC_ACCEPTABLE|  
|0x80000|OPTIMISTIC_ACCEPTABLE|  
  
 Как и в *scrollpt*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно назначить другое значение, которое запрашивалось.  
  
## <a name="remarks"></a>Замечания  
 Параметр состояния RPC может иметь следующие значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|0|Успешно|  
|0x0001|Failure|  
|1FF6|Невозможно вернуть метаданные.<br /><br /> Примечание: Это обусловлено тем, инструкция не создает результирующий набор; Например это инструкция INSERT или DDL.|  
  
## <a name="examples"></a>Примеры  
 Когда *stmt* параметризован и *scrollopt* значение PARAMETERIZED_STMT равно ON, имеет следующий формат строки:  
  
 {  *\<имя локальной переменной > **\<тип данных >* } [,... *n* ]  
  
## <a name="see-also"></a>См. также  
 [sp_cursorexecute &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorunprepare &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorunprepare-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
