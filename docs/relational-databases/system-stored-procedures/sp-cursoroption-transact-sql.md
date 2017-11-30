---
title: "sp_cursoroption (Transact-SQL) | Документы Microsoft"
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
- sp_cursoroption_TSQL
- sp_cursoroption
dev_langs: TSQL
helpviewer_keywords: sp_cursoroption
ms.assetid: 88fc1dba-f4cb-47c0-92c2-bf398f4a382e
caps.latest.revision: "8"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b0fcd7b9c009d0af70e48982f9630f783bce057d
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/27/2017
---
# <a name="spcursoroption-transact-sql"></a>sp_cursoroption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Устанавливает параметры курсора или возвращает сведения о курсорах, созданных sp_cursoropen хранимой процедурой. sp_cursoroption вызывается указанием ID = 8 в пакете потока табличных данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursoroption cursor, code, value  
```  
  
## <a name="arguments"></a>Аргументы  
 *курсор*  
 — *Обработки* значения, создаваемые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и возвращаемый процедурой sp_cursoropen хранятся. *курсор* требует **int** входного значения.  
  
 *код*  
 Служит для указания различных коэффициентов возвращаемых значений курсора. *код* требуется один из следующих **int** входных значений:  
  
|Значение|Имя|Description|  
|-----------|----------|-----------------|  
|0x0001|TEXTPTR_ONLY|Возвращает не фактические данные, а текстовый указатель для определенных назначенных столбцов типа text или image.<br /><br /> TEXTPTR_ONLY позволяет текстовые указатели для использования в качестве *дескрипторы* для объектов blob, которые можно позже можно выборочно получить или обновить с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или DBLib (например) [!INCLUDE[tsql](../../includes/tsql-md.md)]READTEXT или DBLIB DBWRITETEXT).<br /><br /> Если присвоено значение «0», то все столбцы типа text или image из выбранного списка будут возвращать вместо данных текстовые указатели.|  
|0x0002|CURSOR_NAME|Назначает имя, указанное в *значение* до текущей позиции курсора. Это, в свою очередь позволяет интерфейсу ODBC применять [!INCLUDE[tsql](../../includes/tsql-md.md)] позиционированных инструкций UPDATE и DELETE к курсорам, открываемым процедурой sp_cursoropen.<br /><br /> Строка может иметь любой символьный тип данных или UNICODE.<br /><br /> Поскольку [!INCLUDE[tsql](../../includes/tsql-md.md)] позиционированные инструкции UPDATE и DELETE работают по умолчанию с первой строкой в крупном курсоре, sp_cursor SETPOSITION следует использовать для позиционирования курсора перед выдачей позиционированной инструкции UPDATE или DELETE.|  
|0x0003|TEXTDATA|Возвращает фактические данные, а не текстовый указатель для определенных столбцов типа text или image при последующей выборке (т. е. отменяет действие TEXTPTR_ONLY).<br /><br /> Если для определенного столбца включен режим TEXTDATA, то выполняется повторная выборка или обновление строки, и после этого можно опять присвоить значение TEXTPTR_ONLY. Как и в случае с TEXTPTR_ONLY, целочисленный параметр значения задает номер столбца. Нулевое значение возвращает все текстовые столбцы или столбцы изображений.|  
|0x0004|SCROLLOPT|Параметр прокрутки. Дополнительные сведения см. ниже в разделе «Значения кодов возврата».|  
|0x0005|CCOPT|Параметр управления параллелизмом. Дополнительные сведения см. ниже в разделе «Значения кодов возврата».|  
|0x0006|ROWCOUNT|Количество строк, находящихся в результирующем наборе.<br /><br /> Примечание: ROWCOUNT мог измениться с момента значение, возвращаемое процедурой sp_cursoropen, если используется асинхронное заполнение. Значение -1 возвращается в том случае, если число строк неизвестно.|  
  
 *value*  
 Задает значение, возвращаемое *кода*. *значение* является обязательным параметром, 0x0001, 0x0002 или 0x0003 *кода* входного значения.  
  
> [!NOTE]  
>  Объект *код* значение 2 является строковым типом данных. Любой другой *кода* значение введенное или возвращенное *значение* должно быть целым числом.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 *Значение* может возвращать одно из следующих *кода* значения.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0x0004|SCROLLOPT|  
|0X0005|CCOPT|  
|0X0006|ROWCOUNT|  
  
 *Значение* возвращает одно из следующих значений SCROLLOPT.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
  
 *Значение* возвращает одно из следующих значений CCOPT.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS|  
|0x0004 или 0x0008|OPTIMISTIC|  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cursor &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cursor-transact-sql.md)   
 [sp_cursoropen &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)  
  
  
