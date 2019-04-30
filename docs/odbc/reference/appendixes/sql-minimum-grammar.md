---
title: Минимальная Грамматика SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 4f36d785-104f-4fec-93be-f201203bc7c7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 26cf76200010edae7f85993ec33eb3722f35e94e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63270500"
---
# <a name="sql-minimum-grammar"></a>Минимальная грамматика SQL
В этом разделе описывается минимальный синтаксис SQL, драйвер ODBC должен поддерживать. Синтаксис, описанный в этом разделе — это подмножество запись уровня синтаксиса SQL-92.  
  
 Приложение можно использовать любой из синтаксис в этом разделе и быть уверенным, что все совместимые с ODBC драйвер будет поддерживать этот синтаксис. Чтобы определить, поддерживается ли дополнительные возможности SQL-92 не в этом разделе, приложение должно вызвать **SQLGetInfo** с типом SQL_SQL_CONFORMANCE сведения. Даже если драйвер не соответствует любой уровень соответствия SQL-92, приложение по-прежнему можно использовать синтаксис, описанный в этом разделе. Если драйвер соответствует до уровня SQL-92, с другой стороны, он поддерживает все синтаксические конструкции, включенных на данном уровне. Сюда входят синтаксис в этом разделе, так как минимальная Грамматика, описанные здесь является подмножеством чисто самый низкий уровень соответствия SQL-92. Как только приложение знает, уровень SQL-92, поддерживаемый, определяется ли функция более высокого уровня поддерживается (если таковые имеются), вызвав **SQLGetInfo** с сведения о каждом тип, соответствующий этой функции.  
  
 Драйверы, которые работают только с источниками данных только для чтения могут не поддерживать те части грамматики этого раздела, которые имеют дело с изменением данных. Приложение можно определить, является ли источник данных только для чтения, вызвав **SQLGetInfo** с типом SQL_DATA_SOURCE_READ_ONLY сведения.  
  
## <a name="statement"></a>.  
 *create-table-statement* ::=  
  
 CREATE TABLE *base-table-name*  
  
 (*идентификатор столбца типа данных* [*, тип данных столбца идентификаторов*]...)  
  
> [!IMPORTANT]  
>  Как *тип данных* в *-инструкция create table*, приложения должны использовать тип данных результирующего набора, возвращаемого в столбце TYPE_NAME **SQLGetTypeInfo**.  
  
 *delete-statement-searched* ::=  
  
 УДАЛИТЬ из *имя таблицы* [ГДЕ *условие поиска*]  
  
 *drop-table-statement* ::=  
  
 DROP TABLE *base-table-name*  
  
 *insert-statement* ::=  
  
 INSERT INTO *имя таблицы* [( *идентификатор столбца* [, *идентификатор столбца*]...)]      ЗНАЧЕНИЯ (*вставки значение*[, *вставки значение*]...)  
  
 *select-statement* ::=  
  
 ВЫБЕРИТЕ [все &#124; DISTINCT] *список выбора*  
  
 ИЗ *таблицы список ссылок*  
  
 [ГДЕ *условие поиска*]  
  
 [*предложение order by*]  
  
 *statement* ::= *create-table-statement*  
  
 &#124; *delete-statement-searched*  
  
 &#124; *drop-table-statement*  
  
 &#124; *insert-statement*  
  
 &#124; *select-statement*  
  
 &#124; *update-statement-searched*  
  
 *Поиск обновления оператор*  
  
 ОБНОВЛЕНИЕ *имя таблицы*  
  
 ЗАДАЙТЕ *идентификатор столбца* = {*выражение* &#124; NULL}  
  
 [, *column-identifier* = {*expression* &#124; NULL}]...  
  
 [ГДЕ *условие поиска*]  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Элементы, используемые в инструкциях SQL](../../../odbc/reference/appendixes/elements-used-in-sql-statements.md)  
  
-   [Поддержка типов данных](../../../odbc/reference/appendixes/data-type-support.md)  
  
-   [Типы данных параметров](../../../odbc/reference/appendixes/parameter-data-types.md)  
  
-   [Маркеры параметров](../../../odbc/reference/appendixes/parameter-markers.md)
