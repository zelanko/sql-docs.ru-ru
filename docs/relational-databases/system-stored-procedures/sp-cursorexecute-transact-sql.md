---
title: sp_cursorexecute (Transact-SQL) | Документация Майкрософт
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
- sp_cursorexecute
- sp_cursorexecute_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_execute
ms.assetid: 6a204229-0a53-4617-a57e-93d4afbb71ac
caps.latest.revision: 7
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 47c6f3a1c0356f00843ba086d1d7994071c24ba6
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43029875"
---
# <a name="spcursorexecute-transact-sql"></a>sp_cursorexecute (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает и заполняет курсор на основе плана выполнения, который был создан процедурой sp_cursorprepare. Эта процедура в сочетании с sp_cursorprepare, то же самое, что процедура sp_cursoropen, но разбивается на два этапа. sp_cursorexecute вызывается указанием ID = 4 в пакете потока табличных данных.  
  
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
 Подготовленной *обрабатывать* значение, возвращаемое процедурой sp_cursorprepare. *prepared_handle* является обязательным параметром, который вызывает для **int** входного значения.  
  
 *курсор*  
 Идентификатор курсора, созданный SQL Server. *курсор* является обязательным параметром, который должен указываться во всех последующих процедур, работающих с этим курсором, например sp_cursorfetch  
  
 *scrollopt*  
 Параметр прокрутки. *scrollopt* — это необязательный параметр, который требует **int** входного значения. Sp_cursorexecute*scrollopt* параметр имеет те же параметры значение, что и для sp_cursoropen.  
  
> [!NOTE]  
>  Значение PARAMETERIZED_STMT не поддерживается.  
  
> [!IMPORTANT]  
>  Если *scrollopt* значение не указано, значение по умолчанию — KEYSET независимо от *scrollopt* значение, указанное в процедуре sp_cursorprepare.  
  
 *ccopt*  
 Параметр управления параллелизмом. *ccopt* — это необязательный параметр, который требует **int** входного значения. Sp_cursorexecute*ccopt* параметр имеет те же параметры значение, что и для sp_cursoropen.  
  
> [!IMPORTANT]  
>  Если *ccopt* значение не указано, значение по умолчанию — OPTIMISTIC независимо от *ccopt* значение, указанное в процедуре sp_cursorprepare.  
  
 *количество строк*  
 Необязательный параметр, который указывает число строк буфера выборки, которые будут использоваться с AUTO_FETCH. Значение по умолчанию составляет 20 строк. *количество строк* ведет себя по-разному, при назначении значение как входное или как возвращаемое.  
  
|Как входное значение|Как возвращаемое значение|  
|--------------------|---------------------|  
|При указании AUTO_FETCH с курсорами FAST_FORWARD *rowcount* представляет число строк, чтобы поместить в буфер выборки.|Представляет число строк в результирующем наборе. Когда *scrollopt* указано значение AUTO_FETCH, *rowcount* возвращает количество строк, выбранных в буфер выборки.|  
  
 *bound_param*  
 Означает необязательное использование дополнительных параметров.  
  
> [!NOTE]  
>  Все параметры после пятого передаются в план инструкции как входные.  
  
## <a name="code-return-value"></a>Значение кодов возврата  
 *количество строк* может возвращать следующие значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|-1|Число строк неизвестно.|  
|-n|Действует асинхронное заполнение.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="scrollopt-and-ccopt-parameters"></a>Параметры scrollopt и ccopt  
 *scrollopt* и *ccopt* полезны, если кэшированные планы вытесняются в серверный кэш, это означает, что подготовленный дескриптор, идентифицирующий инструкцию, должен быть перекомпилирован. *Scrollopt* и *ccopt* значения параметров должны совпадать со значениями, переданными в исходном запросе в процедуру sp_cursorprepare.  
  
> [!NOTE]  
>  PARAMETERIZED_STMT не должен быть назначен *scrollopt*.  
  
 При невозможности найти совпадающие значения будет проведена повторная компиляция планов, отрицающая операции подготовки и выполнения.  
  
## <a name="rpc-and-tds-considerations"></a>Замечания по RPC и TDS  
 Входной флажок RPC RETURN_METADATA может быть установлен в значение 1, чтобы в потоке TDS возвращались метаданные списка выбора курсора.  
  
## <a name="see-also"></a>См. также  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [Хранимая процедура sp_cursorfetch &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
