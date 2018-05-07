---
title: sp_cursorprepexec (Transact-SQL) | Документы Microsoft
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
- sp_cursorprepexec_TSQL
- sp_cursorprepexec
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursorprepexec
ms.assetid: 8094fa90-35b5-4cf4-8012-0570cb2ba1e6
caps.latest.revision: 9
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 378a389780e8af6ed966c4e0757352b16fbc0dd1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="spcursorprepexec-transact-sql"></a>sp_cursorprepexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Компилирует план для переданной инструкции или пакета курсора, после чего создает и заполняет курсор. sp_cursorprepexec сочетает функции sp_cursorprepare и sp_cursorexecute. Для вызова этой процедуры необходимо задать ID = 5 в пакете потока табличных данных (TDS).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursorprepexec prepared handle OUTPUT, cursor OUTPUT, params , statement , options  
    [ , scrollopt [ , ccopt [ , rowcount ] ] ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *подготовленный дескриптор*  
 — [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Созданный подготовленных *обработки* идентификатор. *подготовленный дескриптор* является обязательным и возвращает **int**.  
  
 *курсор*  
 Идентификатор курсора, созданный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *курсор* является обязательным параметром, который должен указываться во всех последующих процедур, работающих с этим курсором, например sp_cursorfetch.  
  
 *Params*  
 Указывает параметризованные инструкции. *Params* определение переменных подставляется вместо маркеров параметров в инструкции. *params* является обязательным параметром, который вызывает для **ntext**, **nchar**, или **nvarchar** входного значения.  
  
> [!NOTE]  
>  Используйте **ntext** строку в качестве входных данных значения при *stmt* параметризован и *scrollopt* значение PARAMETERIZED_STMT имеет значение ON.  
  
 *инструкция*  
 Определяет результирующий набор курсора. *Инструкции* параметр является обязательным и требует **ntext**, **nchar** или **nvarchar** входного значения.  
  
> [!NOTE]  
>  Указании значения stmt действуют правила идентичны таковым для sp_cursoropen, за исключением того, *stmt* строковый тип данных должен быть **ntext**.  
  
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
  
 Поскольку существует возможность, что запрошенный параметр не будет соответствовать курсору, заданному по  *\<stmt >*, этот параметр используется как ввод и вывод. В таких случаях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначает соответствующий тип и изменяет это значение.  
  
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
  
 Как и в *scrollpt*, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно назначить значение, отличное от запрошенного.  
  
 *количество строк*  
 Необязательный параметр, который указывает число строк буфера выборки, которые будут использоваться с AUTO_FETCH. Значение по умолчанию составляет 20 строк. *количество строк* ведет себя по-разному, при назначении как входное или как возвращаемое значение.  
  
|Как входное значение|Как возвращаемое значение|  
|--------------------|---------------------|  
|При указании AUTO_FETCH с курсорами FAST_FORWARD *rowcount* представляет число строк для помещения в буфер выборки.|Представляет число строк в результирующем наборе. Когда *scrollopt* задано значение AUTO_FETCH, *rowcount* возвращает число строк, выбранных в буфер выборки.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Если *params* возвращает значение NULL, то инструкция не параметризована.  
  
## <a name="see-also"></a>См. также  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorexecute &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorexecute-transact-sql.md)   
 [sp_cursorprepare &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorprepare-transact-sql.md)   
 [Хранимая процедура sp_cursorfetch &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
