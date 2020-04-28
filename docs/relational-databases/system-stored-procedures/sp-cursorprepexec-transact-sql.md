---
title: sp_cursorprepexec (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/20/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursorprepexec_TSQL
- sp_cursorprepexec
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorprepexec
ms.assetid: 8094fa90-35b5-4cf4-8012-0570cb2ba1e6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 660a75f1e6fea9b5a825372501c2e65f2dd3874b
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "69652439"
---
# <a name="sp_cursorprepexec-transact-sql"></a>sp_cursorprepexec (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md.md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Компилирует план для переданной инструкции или пакета курсора, после чего создает и заполняет курсор. sp_cursorprepexec объединяет функции sp_cursorprepare и sp_cursorexecute. Эта процедура вызывается путем указания ID = 5 в пакете потока табличных данных (TDS).  
  
 ![Значок ссылки](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursorprepexec prepared handle OUTPUT, cursor OUTPUT, params , statement , options  
    [ , scrollopt [ , ccopt [ , rowcount ] ] ]  
    [, '@parameter_name[,...n ]']
```  
  
## <a name="arguments"></a>Аргументы  
 *подготовленный обработчик*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Созданный идентификатор подготовленного *обработчика* . *подготовленный обработчик* является обязательным и возвращает значение **int**.  
  
 *курсор*  
 Идентификатор курсора, созданный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *курсор* — это обязательный параметр, который должен быть указан во всех последующих процедурах, действующих для данного курсора, например sp_cursorfetch.  
  
 *params*  
 Указывает параметризованные инструкции. Определение переменных *params* подставляется для маркеров параметров в инструкции. *params* — это обязательный параметр, который вызывает для входного значения **ntext**, **nchar**или **nvarchar** .  
  
> [!NOTE]  
>  Используйте строку **ntext** в качестве входного значения при параметризованной инструкции *stmt* и значения *scrollopt* PARAMETERIZED_STMT.  
  
 *баланс*  
 Определяет результирующий набор курсора. Параметр *инструкции* является обязательным и вызывает для входного значения **ntext**, **nchar**или **nvarchar** .  
  
> [!NOTE]  
>  Правила указания значения stmt те же, что и для sp_cursoropen, за исключением того, что строкой типа данных *stmt* должен быть **ntext**.  
  
 *options*  
 Необязательный параметр, возвращающий описание столбцов результирующего набора курсора. * для параметров требуется следующее входное значение **int** .  
  
|Значение|Описание|  
|-----------|-----------------|  
|0x0001|RETURN_METADATA|  
  
 *scrollopt*  
 Параметр прокрутки. *scrollopt* — это необязательный параметр, для которого требуется одно из следующих входных значений **int** .  
  
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
  
 Из-за вероятности того, что запрошенный параметр не подходит для курсора, определенного с помощью * \<stmt>*, этот параметр служит как входными, так и выходными. В таких случаях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначает соответствующий тип и изменяет это значение.  
  
 *ccopt*  
 Параметр управления параллелизмом. *ccopt* — это необязательный параметр, для которого требуется одно из следующих входных значений **int** .  
  
|Значение|Описание|  
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
  
 Как и *scrollpt*в случае [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с скроллпт, может присвоить значение, отличное от запрошенного.  
  
 *количества*  
 Необязательный параметр, который указывает число строк буфера выборки, которые будут использоваться с AUTO_FETCH. Значение по умолчанию составляет 20 строк. При назначении в качестве входного значения и возвращаемого значения *ROWCOUNT* ведет себя иначе.  
  
|Как входное значение|Как возвращаемое значение|  
|--------------------|---------------------|  
|При указании AUTO_FETCH с FAST_FORWARD курсоров *ROWCOUNT* представляет число строк, помещаемых в буфер выборки.|Представляет число строк в результирующем наборе. Если указано значение AUTO_FETCH *scrollopt* , функция *ROWCOUNT* возвращает количество строк, которые были получены в буфер выборки.|  

*parameter_name* Назначьте одно или несколько имен параметров, как определено в аргументе params.  Для каждого параметра, включаемого в параметры, должен быть указан параметр. Этот аргумент не является обязательным, если в инструкции Transact-SQL или в пакете params не определены параметры.
  
## <a name="return-code-values"></a>Значения кода возврата  
 Если params возвращает значение NULL, то оператор не является параметризованным.  
  
## <a name="see-also"></a>См. также:  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorexecute &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursorprepare &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorprepare-transact-sql.md)   
 [sp_cursorfetch &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
