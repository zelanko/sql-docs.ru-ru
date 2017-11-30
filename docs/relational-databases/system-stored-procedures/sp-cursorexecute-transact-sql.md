---
title: "sp_cursorexecute (Transact-SQL) | Документы Microsoft"
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
- sp_cursorexecute
- sp_cursorexecute_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_cursor_execute
ms.assetid: 6a204229-0a53-4617-a57e-93d4afbb71ac
caps.latest.revision: "7"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6dc0a358e0d62fa8a0319ab6d2ad586315f30e24
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spcursorexecute-transact-sql"></a>sp_cursorexecute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает и заполняет курсор на основе плана выполнения, который был создан процедурой sp_cursorprepare. Эта процедура в сочетании с sp_cursorprepare, делает то же самое, что процедура sp_cursoropen, но обработка разбита на два этапа. sp_cursorexecute вызывается указанием ID = 4 в пакете потока табличных данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursorexecute prepared_handle, cursor  
    [ , scrollopt[ OUTPUT ]  
    [ , ccopt[ OUTPUT ]  
    [ ,rowcount OUTPUT [ ,bound param][,...n]]]]]  
```  
  
## <a name="arguments"></a>Аргументы  
 *prepared_handle*  
 Подготовленной *обработки* значение, возвращаемое процедурой sp_cursorprepare. *prepared_handle* является обязательным параметром, который вызывает для **int** входного значения.  
  
 *курсор*  
 Идентификатор курсора, созданный SQL Server. *курсор* является обязательным параметром, который должен указываться во всех последующих процедур, работающих с курсором, например sp_cursorfetch  
  
 *scrollopt*  
 Параметр прокрутки. *scrollopt* является необязательным параметром, который требует **int** входного значения. Sp_cursorexecute*scrollopt* параметр имеет такие же варианты значений, что и для sp_cursoropen.  
  
> [!NOTE]  
>  Значение PARAMETERIZED_STMT не поддерживается.  
  
> [!IMPORTANT]  
>  Если *scrollopt* значение не указано, значение по умолчанию — KEYSET независимо от значения *scrollopt* значения, указанного в процедуре sp_cursorprepare.  
  
 *ccopt*  
 Параметр управления параллелизмом. *ccopt* является необязательным параметром, который требует **int** входного значения. Sp_cursorexecute*ccopt* параметр имеет такие же варианты значений, что и для sp_cursoropen.  
  
> [!IMPORTANT]  
>  Если *ccopt* значение не указано, значение по умолчанию — OPTIMISTIC независимо от значения *ccopt* значения, указанного в процедуре sp_cursorprepare.  
  
 *количество строк*  
 Необязательный параметр, который указывает число строк буфера выборки, которые будут использоваться с AUTO_FETCH. Значение по умолчанию составляет 20 строк. *количество строк* ведет себя по-разному, при назначении как входное или как возвращаемое значение.  
  
|Как входное значение|Как возвращаемое значение|  
|--------------------|---------------------|  
|При указании AUTO_FETCH с курсорами FAST_FORWARD *rowcount* представляет число строк для помещения в буфер выборки.|Представляет число строк в результирующем наборе. Когда *scrollopt* задано значение AUTO_FETCH, *rowcount* возвращает число строк, выбранных в буфер выборки.|  
  
 *bound_param*  
 Означает необязательное использование дополнительных параметров.  
  
> [!NOTE]  
>  Все параметры после пятого передаются в план инструкции как входные.  
  
## <a name="code-return-value"></a>Значение кодов возврата  
 *количество строк* может возвращать следующие значения.  
  
|Значение|Description|  
|-----------|-----------------|  
|-1|Число строк неизвестно.|  
|-n|Действует асинхронное заполнение.|  
  
## <a name="remarks"></a>Замечания  
  
## <a name="scrollopt-and-ccopt-parameters"></a>Параметры scrollopt и ccopt  
 *scrollopt* и *ccopt* полезны, если кэшированные планы вытесняются в серверный кэш. Это означает, что подготовленный дескриптор, идентифицирующий инструкцию перекомпилируется. *Scrollopt* и *ccopt* значения параметров должны совпадать со значениями, переданными в исходном запросе в процедуру sp_cursorprepare.  
  
> [!NOTE]  
>  PARAMETERIZED_STMT не должны быть назначены *scrollopt*.  
  
 При невозможности найти совпадающие значения будет проведена повторная компиляция планов, отрицающая операции подготовки и выполнения.  
  
## <a name="rpc-and-tds-considerations"></a>Замечания по RPC и TDS  
 Входной флажок RPC RETURN_METADATA может быть установлен в значение 1, чтобы в потоке TDS возвращались метаданные списка выбора курсора.  
  
## <a name="see-also"></a>См. также:  
 [sp_cursoropen &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Хранимая процедура sp_cursorfetch &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
