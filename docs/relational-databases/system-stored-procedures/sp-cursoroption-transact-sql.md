---
title: sp_cursoroption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursoroption_TSQL
- sp_cursoroption
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cursoroption
ms.assetid: 88fc1dba-f4cb-47c0-92c2-bf398f4a382e
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 581a154dfefa7823e9a1c0cefa53518352c66d55
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85869106"
---
# <a name="sp_cursoroption-transact-sql"></a>sp_cursoroption (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Задает параметры курсора или возвращает сведения о курсоре, созданные хранимой процедурой sp_cursoropen. sp_cursoroption вызывается путем указания ID = 8 в пакете потока табличных данных (TDS).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_cursoroption cursor, code, value  
```  
  
## <a name="arguments"></a>Аргументы  
 *курсор*  
 Значение *обработчика* , создаваемое [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и возвращаемое хранимой процедурой sp_cursoropen. для выполнения *курсора* требуется входное значение **int** .  
  
 *code*  
 Служит для указания различных коэффициентов возвращаемых значений курсора. для *кода* требуется одно из следующих входных значений **int** :  
  
|Значение|Имя|Описание|  
|-----------|----------|-----------------|  
|0x0001|TEXTPTR_ONLY|Возвращает не фактические данные, а текстовый указатель для определенных назначенных столбцов типа text или image.<br /><br /> TEXTPTR_ONLY позволяет использовать текстовые указатели в качестве *дескрипторов* объектов BLOB, которые впоследствии могут быть выборочно извлечены или обновлены с помощью [!INCLUDE[tsql](../../includes/tsql-md.md)] или DBLIB средств (например, [!INCLUDE[tsql](../../includes/tsql-md.md)] READTEXT или DBLIB DBWRITETEXT).<br /><br /> Если присвоено значение «0», то все столбцы типа text или image из выбранного списка будут возвращать вместо данных текстовые указатели.|  
|0x0002|CURSOR_NAME|Присваивает имя, указанное в поле *значение* , курсору. Это, в свою очередь, позволяет ODBC использовать [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции позиционированного обновления или удаления для курсоров, открытых с помощью sp_cursoropen.<br /><br /> Строка может иметь любой символьный тип данных или UNICODE.<br /><br /> Так как [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции позиционированного обновления и удаления работают по умолчанию в первой строке курсора FAT, SP_CURSOR SETPOSITION следует использовать для позиционирования курсора перед выполнением инструкции позиционированного обновления и удаления.|  
|0x0003|TEXTDATA|Возвращает фактические данные, а не текстовый указатель для определенных столбцов типа text или image при последующей выборке (т. е. отменяет действие TEXTPTR_ONLY).<br /><br /> Если для определенного столбца включен режим TEXTDATA, то выполняется повторная выборка или обновление строки, и после этого можно опять присвоить значение TEXTPTR_ONLY. Как и в случае с TEXTPTR_ONLY, целочисленный параметр значения задает номер столбца. Нулевое значение возвращает все текстовые столбцы или столбцы изображений.|  
|0x0004|SCROLLOPT|Параметр прокрутки. Дополнительные сведения см. ниже в разделе «Значения кодов возврата».|  
|0x0005|CCOPT|Параметр управления параллелизмом. Дополнительные сведения см. ниже в разделе «Значения кодов возврата».|  
|0x0006|ROWCOUNT|Количество строк, находящихся в результирующем наборе.<br /><br /> Примечание. возможно, количество строк изменилось со времени, возвращенного sp_cursoropen, если используется асинхронное заполнение. Значение-1 возвращается, если число строк неизвестно.|  
  
 *value*  
 Определяет значение, возвращаемое *кодом*. *value* — это обязательный параметр, который вызывает для входного значения 0x0001, 0x0002 или 0x0003 *Code* .  
  
> [!NOTE]  
>  Значение *кода* , равное 2, является строковым типом данных. Любое другое значение *кода* , вводимое или возвращаемое *значением* , является целым числом.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Параметр *value* может возвращать одно из следующих значений *кода* .  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0x0004|SCROLLOPT|  
|0X0005|CCOPT|  
|0X0006|ROWCOUNT|  
  
 Параметр *value* возвращает одно из следующих значений SCROLLOPT.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0x0001|KEYSET|  
|0x0002|DYNAMIC|  
|0x0004|FORWARD_ONLY|  
|0x0008|STATIC|  
  
 Параметр *value* возвращает одно из следующих значений ccopt.  
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0x0001|READ_ONLY|  
|0x0002|SCROLL_LOCKS|  
|0x0004 или 0x0008|OPTIMISTIC|  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_cursor &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursor-transact-sql.md)   
 [sp_cursoropen &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cursoropen-transact-sql.md)  
  
  
