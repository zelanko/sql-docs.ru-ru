---
title: Поддержка SQLGetInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLGetInfo
- backward compatibility [ODBC], SQLGetInfo
- SQLGetInfo function [ODBC], support
ms.assetid: 57326f57-daba-46b6-b0be-6c97213b9ef1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0f40299dccc0313f662aeadfcb26b71326cdc6d8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68073905"
---
# <a name="sqlgetinfo-support"></a>Поддержка SQLGetInfo
Когда ODBC 2. *x* приложение вызывает **SQLGetInfo** ODBC 3 *.x* драйвера, *InfoType* должен поддерживаться аргументы в следующей таблице.  
  
|*Свойство*|Возвращает|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0) **Примечание:**  Этот тип не устарел. устарели и битовой маски, в столбце справа.|Битовая маска SQLINTEGER перечисление предложения в **ALTER TABLE** инструкции, поддерживаемых источником данных.<br /><br /> Следующие битовые маски используются для определения, какие предложения поддерживаются:<br /><br /> SQL_AT_DROP_COLUMN = поддерживается возможность перетаскивания столбцов. Это приводит к cascade ли ограничить поведение, определяемым драйвером. (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN = возможность добавления поддерживается несколько столбцов в одной инструкции ALTER TABLE. Этот бит не объединяются с другими SQL_AT_ADD_COLUMN_XXX bits или SQL_AT_CONSTRAINT_XXX bits. (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> Тип данных был введен в ODBC 1.0; Каждая маска помечается версии, в котором он был представлен.|Битовая маска SQLINTEGER, перечисление параметров направления поддерживаемых fetch.<br /><br /> Следующие битовые маски используются в сочетании с флагом, чтобы определить, какие параметры поддерживаются:<br /><br /> SQL_FD_FETCH_BOOKMARK SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_RELATIVE (ODBC 1.0) ДЛЯ SQL_FD_FETCH_FIRST (ODBC 1.0) (ODBC 1.0) SQL_FD_FETCH_LAST SQL_FD_FETCH_NEXT (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|Типы SQLINTEGER битовой маски, перечисления поддерживаемых блокировки для *fLock* аргумента в **SQLSetPos**.<br /><br /> Следующие битовые маски используются вместе с флагом, чтобы определить, какие типы блокировок поддерживаются:<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|SQLSMALLINT, указывающее уровень соответствия ODBC.<br /><br /> SQL_OAC_NONE = нет<br /><br /> SQL_OAC_LEVEL1 = поддерживается уровня 1<br /><br /> SQL_OAC_LEVEL2 = поддерживается уровня 2|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|SQLSMALLINT, обозначающее грамматику SQL, поддерживаемых драйвером. См. в разделе [приложение c. Грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) определение уровни соответствия SQL.<br /><br /> SQL_OSC_MINIMUM = Минимальная Грамматика поддерживается<br /><br /> SQL_OSC_CORE = грамматику ядра поддерживается<br /><br /> SQL_OSC_EXTENDED = расширенная Грамматика поддерживается|  
|SQL_POS_OPERATIONS (ODBC 2.0)|Битовая маска SQLINTEGER перечисляет поддерживаемые операции в **SQLSetPos**.<br /><br /> Чтобы определить, какие параметры поддерживаются следующие битовые маски используются для вместе с флагом:<br /><br /> SQL_POS_POSITION (ODBC 2.0) (ODBC 2.0) SQL_POS_REFRESH SQL_POS_UPDATE (ODBC 2.0) (ODBC 2.0) SQL_POS_DELETE SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|Битовая маска SQLINTEGER перечисление поддерживаемых позиционированных инструкций SQL.<br /><br /> Следующие битовые маски используются для определения, какие инструкции поддерживаются:<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|Битовая маска SQLINTEGER, перечисление параметров управления параллелизмом, поддерживаемых для курсора.<br /><br /> Следующие битовые маски используются для определения, какие параметры поддерживаются:<br /><br /> SQL_SCCO_READ_ONLY = курсор доступен только для чтения. Обновления не разрешены.<br /><br /> SQL_SCCO_LOCK = курсор использует самый низкий уровень блокировки достаточно, чтобы убедиться, что строки могут обновляться.<br /><br /> SQL_SCCO_OPT_ROWVER = курсор использует управление оптимистичным параллелизмом, сравнение версий строк, например программа ROWID или метки времени Sybase.<br /><br /> SQL_SCCO_OPT_VALUES = курсор использует управление оптимистичным параллелизмом, сравнение значений.|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|SQLINTEGER битовую маску перечисления ли внесены изменения, приложением для статических и управляемых набором ключей курсора через **SQLSetPos** или позиционированного обновления или инструкций delete могут определяться с помощью этого приложения.<br /><br /> SQL_SS_ADDITIONS = Added строк являются видимыми для курсора; курсор можно перейти к эти строки. Когда эти строки добавляются к курсору зависит от драйвера.<br /><br /> SQL_SS_DELETIONS = удаленные строки больше не доступны на курсор и не оставляйте «путь» в результирующем наборе; после курсора прокручивает из удаленной строки, он не может возвращать для этой строки.<br /><br /> SQL_SS_UPDATES = обновления строк являются видимыми для курсора; Если курсор прокручивается и возвращает обновленную строку, данные, возвращенные курсором, обновленные данные, а не исходные данные. Этот параметр применяется только к статические курсоры или обновления на курсоры, которые не обновить ключ. Этот параметр не применяется к динамическому курсору, или в случае, в котором ключ изменяется в смешанной курсора.<br /><br /> Ли приложение может обнаружить изменения, внесенные в результирующий набор другими пользователями, включая другие курсоры в одном приложении, зависит от типа курсора.|  
  
 ODBC 3 *.x* приложение, которое работает с ODBC 3 *.x* драйвер не следует вызывать **SQLGetInfo** с *InfoType* аргументы описано в разделе предыдущей таблице, но следует использовать ODBC 3 *.x* *InfoType* аргументы, перечисленные в следующем абзаце. Нет однозначного соответствия между *InfoType* аргументы, используемые в ODBC 2. *x* и тех, которые используются в ODBC 3 *.x*. ODBC 3 *.x* приложение, которое работает с ODBC 2. *x* драйвера, с другой стороны, следует использовать *InfoType* аргументы, описанные ранее.  
  
 Некоторые типы сведений в предыдущей таблице устарели и были заменены типах сведений атрибуты курсора. Эти устаревшие сведения типы: SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY и SQL_STATIC_SENSITIVITY. Новые типы атрибуты курсора, SQL_XXX_CURSOR_ATTRIBUTES2 SQL_XXX_CURSOR_ATTRIBUTES1and, где XXX равно DYNAMIC, FORWARD_ONLY, KEYSET_DRIVEN или STATIC. Каждое из новых типов означает возможности драйверов для типа одного курсора. Дополнительные сведения об этих параметрах см. в разделе [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) описание функции.
