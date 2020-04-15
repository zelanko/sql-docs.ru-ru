---
title: Поддержка S'LGetInfo (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a21c035a14814f51d4344894ef253b2cc844f4c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307805"
---
# <a name="sqlgetinfo-support"></a>Поддержка SQLGetInfo
Когда ODBC 2. *приложение x* вызывает **s'LGetInfo** к драйверу ODBC 3 *.x,* аргументы *InfoType* в следующей таблице должны быть поддержаны.  
  
|*InfoType*|Результаты|  
|----------------|-------------|  
|SQL_ALTER_TABLE (ODBC 2.0) **Примечание:** Этот тип информации не амортизирован; бит-маски в колонке справа обезвращены.|Битовая маска S'LINTEGER, перечисляющая положения в заявлении **ALTER TABLE,** поддерживаемом источником данных.<br /><br /> Для определения того, какие положения поддерживаются, используются следующие бит-маски:<br /><br /> SQL_AT_DROP_COLUMN : Поддерживается возможность отсутсвия столбцов. Определяется ли это каскадом или ограничивает поведение. (ODBC 2.0)<br /><br /> SQL_AT_ADD_COLUMN поддерживается возможность добавления нескольких столбцов в одну выписку ALTER TABLE. Этот бит не сочетается с другими SQL_AT_ADD_COLUMN_XXX битами или SQL_AT_CONSTRAINT_XXX битами. (ODBC 2.0)|  
|SQL_FETCH_DIRECTION (ODBC 1.0)<br /><br /> Информационный тип был введен в ODBC 1.0; каждая битовая маска помечена версией, в которой она была введена.|Битовая маска S'LINTEGER, перечисляющая поддерживаемые варианты направления получения.<br /><br /> Следующие битмаски используются в сочетании с флагом, чтобы определить, какие варианты поддерживаются:<br /><br /> SQL_FD_FETCH_NEXT (ODBC 1.0) SQL_FD_FETCH_FIRST (ODBC 1.0) SQL_FD_FETCH_LAST (ODBC 1.0) SQL_FD_FETCH_PRIOR (ODBC 1.0) SQL_FD_FETCH_ABSOLUTE (ODBC 1.0) SQL_FD_FETCH_RELATIVE (ODBC 1.0) SQL_FD_FETCH_BOOKMARK (ODBC 2.0)|  
|SQL_LOCK_TYPES (ODBC 2.0)|Битовая маска S'LINTEGER, перечисляющая поддерживаемые типы блокировки для аргумента *fLock* в **S'LSetPos.**<br /><br /> Следующие битмаски используются в сочетании с флагом, чтобы определить, какие типы блокировки поддерживаются:<br /><br /> SQL_LCK_NO_CHANGE SQL_LCK_EXCLUSIVE SQL_LCK_UNLOCK|  
|SQL_ODBC_API_CONFORMANCE (ODBC 1.0)|Значение S'LSMALLINT, указывающее на уровень соответствия ODBC.<br /><br /> SQL_OAC_NONE - Нет<br /><br /> SQL_OAC_LEVEL1 и поддерживается уровень 1<br /><br /> SQL_OAC_LEVEL2 - поддерживаемый уровень 2|  
|SQL_ODBC_SQL_CONFORMANCE (ODBC 1.0)|Значение S'LSMALLINT, указывающее грамматику S'L, поддерживаемое драйвером. [См. Приложение C: Грамматика S'L](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md) для определения уровней соответствия СЗЛ.<br /><br /> SQL_OSC_MINIMUM - Минимальная грамматика поддерживается<br /><br /> SQL_OSC_CORE - поддерживаемая основная грамматика<br /><br /> SQL_OSC_EXTENDED - Расширенная грамматика поддерживается|  
|SQL_POS_OPERATIONS (ODBC 2.0)|Битовая маска S'LINTEGER, перечисляющая поддерживаемые операции в **S'LSetPos.**<br /><br /> Следующие бит-маски используются в сочетании с флагом, чтобы определить, какие варианты поддерживаются:<br /><br /> SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)|  
|SQL_POSITIONED_STATEMENTS (ODBC 2.0)|Битовая маска S'LINTEGER, перечисляющая поддерживаемые позиционированные операторы S'L.<br /><br /> Для определения того, какие операторы поддерживаются, используются следующие бит-маски:<br /><br /> SQL_PS_POSITIONED_DELETE SQL_PS_POSITIONED_UPDATE SQL_PS_SELECT_FOR_UPDATE|  
|SQL_SCROLL_CONCURRENCY (ODBC 1.0)|Битовая маска S'LINTEGER, перечисляющая параметры управления параллелизмом, поддерживаемые курсора.<br /><br /> Для определения того, какие параметры поддерживаются, используются следующие битмаски:<br /><br /> SQL_SCCO_READ_ONLY и Курсор читается только по чтению. Обновления не допускаются.<br /><br /> SQL_SCCO_LOCK - Cursor использует самый низкий уровень блокировки, достаточный для обновления строки.<br /><br /> SQL_SCCO_OPT_ROWVER - Cursor использует оптимистичный контроль параллелизма, сравнивая строки версий, таких как S'LBase ROWID или Sybase TIMESTAMP.<br /><br /> SQL_SCCO_OPT_VALUES и Cursor использует оптимистичный параллелический контроль, сравнивая значения.|  
|SQL_STATIC_SENSITIVITY (ODBC 2.0)|Битовая маска S'LINTEGER, перечисляющая, могут ли это приложение обнаружить изменения, внесенные приложением в статический курсор, управляемый ключом, через **S'LSetPos** или позиционированные операторы обновления или удаления.<br /><br /> SQL_SS_ADDITIONS - Добавленные строки видны курсору; курсор может прокрутить к этим строкам. Где эти строки добавляются в курсор зависит от драйвера.<br /><br /> SQL_SS_DELETIONS - Удаленные строки больше не доступны курсору и не оставляют "дыру" в наборе результатов; после того, как курсор прокрутки из удаленного ряда, он не может вернуться в эту строку.<br /><br /> SQL_SS_UPDATES - Обновления строк видны курсору; если курсор прокручивается из обновленной строки и возвращается, данные, возвращенные курсором, являются обновленными данными, а не исходными данными. Эта опция применяется только к статическим курсорам или обновлениям на курсорах, управляемых ключами, которые не обновляют ключ. Эта опция не применяется для динамического курсора или в случае изменения ключа в смешанном курсоре.<br /><br /> Может ли приложение обнаружить изменения, внесенные в результат, установленный другими пользователями, включая другие курсоры в том же приложении, зависит от типа курсора.|  
  
 Приложение ODBC 3 *.x,* работающее с драйвером ODBC 3 *.x,* не должно вызывать **s'LGetInfo** с аргументами *InfoType,* описанными в предыдущей таблице, но следует использовать аргументы ODBC 3 *.x* *InfoType,* перечисленные в следующем пункте. Существует не один-к-одному корреспонденции между *InfoType* аргументы, используемые в ODBC 2. *x* и те, которые используются в ODBC 3 *.x*. Приложение ODBC 3 *.x,* работая с ODBC 2. *x* драйвер, с другой стороны, должен использовать аргументы *InfoType,* описанные ранее.  
  
 Некоторые типы информации в предыдущей таблице унижаются в пользу типов атрибутов курсора. Эти разогнанные типы информации являются SQL_FETCH_DIRECTION, SQL_LOCK_TYPES, SQL_POS_OPERATIONS, SQL_POSITIONED_STATEMENTS, SQL_SCROLL_CONCURRENCY и SQL_STATIC_SENSITIVITY. Новые типы атрибутов курсора являются SQL_XXX_CURSOR_ATTRIBUTES1and SQL_XXX_CURSOR_ATTRIBUTES2, где XXX равен DYNAMIC, FORWARD_ONLY, KEYSET_DRIVEN или STATIC. Каждый из новых типов указывает возможности драйвера для одного типа курсора. Для получения более подробной [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) информации об этих опциях, см.
