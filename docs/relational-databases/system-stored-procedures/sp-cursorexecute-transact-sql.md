---
description: sp_cursorexecute (Transact-SQL)
title: sp_cursorexecute (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursorexecute
- sp_cursorexecute_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursor_execute
ms.assetid: 6a204229-0a53-4617-a57e-93d4afbb71ac
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 07795588a4c1d6df43a7041f9254a661e527be14
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89543604"
---
# <a name="sp_cursorexecute-transact-sql"></a>sp_cursorexecute (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Создает и заполняет курсор на основе плана выполнения, который был создан процедурой sp_cursorprepare. Эта процедура в сочетании с sp_cursorprepare имеет ту же функцию, что и sp_cursoropen, но разбивается на две фазы. sp_cursorexecute вызывается путем указания ID = 4 в пакете потока табличных данных (TDS).  
  
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
 Значение *обработчика* подготовленной инструкции, возвращаемое sp_cursorprepare. *prepared_handle* является обязательным параметром, который вызывает входное значение **int** .  
  
 *курсор*  
 Идентификатор курсора, созданный SQL Server. *курсор* — это обязательный параметр, который должен быть указан во всех последующих процедурах, действующих для курсора, например sp_cursorfetch  
  
 *scrollopt*  
 Параметр прокрутки. *scrollopt* — это необязательный параметр, требующий входного значения **int** . Параметр sp_cursorexecute*scrollopt* имеет те же параметры, что и для sp_cursoropen.  
  
> [!NOTE]  
>  Значение PARAMETERIZED_STMT не поддерживается.  
  
> [!IMPORTANT]  
>  Если значение *scrollopt* не указано, значение по умолчанию — KEYSET, независимо от значения *scrollopt* , указанного в sp_cursorprepare.  
  
 *ccopt*  
 Параметр управления параллелизмом. *ccopt* — это необязательный параметр, требующий входного значения **int** . Параметр sp_cursorexecute*ccopt* имеет те же параметры, что и для sp_cursoropen.  
  
> [!IMPORTANT]  
>  Если значение *ccopt* не указано, значение по умолчанию — оптимистичный, независимо от значения *ccopt* , указанного в sp_cursorprepare.  
  
 *количества*  
 Необязательный параметр, который указывает число строк буфера выборки, которые будут использоваться с AUTO_FETCH. Значение по умолчанию составляет 20 строк. При назначении в качестве входного значения и возвращаемого значения *ROWCOUNT* ведет себя иначе.  
  
|Как входное значение|Как возвращаемое значение|  
|--------------------|---------------------|  
|При указании AUTO_FETCH с FAST_FORWARD курсоров *ROWCOUNT* представляет число строк, помещаемых в буфер выборки.|Представляет число строк в результирующем наборе. Если указано значение AUTO_FETCH *scrollopt* , функция *ROWCOUNT* возвращает количество строк, которые были получены в буфер выборки.|  
  
 *bound_param*  
 Означает необязательное использование дополнительных параметров.  
  
> [!NOTE]  
>  Все параметры после пятого передаются в план инструкции как входные.  
  
## <a name="code-return-value"></a>Значение кодов возврата  
 *ROWCOUNT* может возвращать следующие значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|-1|Число строк неизвестно.|  
|-n|Действует асинхронное заполнение.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="scrollopt-and-ccopt-parameters"></a>Параметры scrollopt и ccopt  
 *scrollopt* и *ccopt* полезны при прерывании кэшированных планов для кэша сервера, что означает, что подготовленный описатель, идентифицирующий инструкцию, должен быть перекомпилирован. Значения параметров *scrollopt* и *ccopt* должны совпадать со значениями, отправленными в исходном запросе, в sp_cursorprepare.  
  
> [!NOTE]  
>  PARAMETERIZED_STMT не следует назначать *scrollopt*.  
  
 При невозможности найти совпадающие значения будет проведена повторная компиляция планов, отрицающая операции подготовки и выполнения.  
  
## <a name="rpc-and-tds-considerations"></a>Замечания по RPC и TDS  
 Входной флажок RPC RETURN_METADATA может быть установлен в значение 1, чтобы в потоке TDS возвращались метаданные списка выбора курсора.  
  
## <a name="see-also"></a>См. также:  
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)   
 [sp_cursorfetch &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursorfetch-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
