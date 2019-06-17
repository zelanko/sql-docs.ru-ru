---
title: Элементы, используемые в инструкциях SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], elements supported
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
ms.assetid: 85777525-1555-4731-8309-63a464c6b43a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9e33beff29463172a26d53953dd5f563fe1f3f5c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63240955"
---
# <a name="elements-used-in-sql-statements"></a>Элементы, используемые в инструкциях SQL
Следующие элементы используются в инструкциях SQL, перечисленных выше.  
  
## <a name="element"></a>Элемент  
 *base-table-identifier* ::= *user-defined-name*  
  
 *base-table-name* ::= *base-table-identifier*  
  
 *Логическое значение коэффициента* :: = [NOT] *основной логическое значение*  
  
 *boolean-primary* ::= comparison *-predicate* &#124; ( *search-condition* )  
  
 *boolean-term* ::= *boolean-factor* [AND *boolean-term*]  
  
 *character-string-literal* ::= ''{*character*}...'' (*символ* — это любой символ в кодировке источника данных или драйвера. Чтобы включить символ одинарной кавычки литерала ("") в символьный литерал строки, используйте два символа кавычки литерала [""].)  
  
 *column-identifier* ::= *user-defined-name*  
  
 *column-name* ::= [*table-name*.]*column-identifier*  
  
 *comparison-operator* ::= < &#124; > &#124; \<= &#124; >= &#124; = &#124; <>  
  
 *comparison-predicate* ::= *expression* comparison-operator expression  
  
 *Тип данных* :: = *тип строки символов* (*тип строки символов* — это любой тип данных, для которого столбец ««DATA_TYPE»» в результирующем наборе, возвращенные SQLGetTypeInfo является либо SQL_CHAR или SQL_VARCHAR.)  
  
 *digit* ::= 0 &#124; 1 &#124; 2 &#124; 3 &#124; 4 &#124; 5 &#124; 6 &#124; 7 &#124; 8 &#124; 9  
  
 *dynamic-parameter* ::= ?  
  
 *expression* ::= term &#124; expression {+&#124;-} term  
  
 *factor* ::= [ *+* &#124; *-* ]*primary*  
  
 *insert-value* ::=  
  
 *динамический параметр*  
  
 &#124; *literal*  
  
 &AMP;#124;ЗНАЧЕНИЕ NULL  
  
 &#124; USER  
  
 *letter* ::= *lower-case-letter &#124; upper-case-letter*  
  
 *literal* ::= *character-string-literal*  
  
 *буква нижнем case* :: = &#124; b &#124; c &#124; d &#124; e &#124; f &#124; g &#124; h &#124; я &#124; j &#124; k &#124; l &#124; m &#124; n &#124; o &#124; p &#124; q &#124; r &#124; s &#124; t &#124; u &#124; v &#124; w &#124; x &#124; y &#124; z  
  
 *предложение ORDER by* :: = ORDER BY *спецификацией сортировки* [, *спецификацией сортировки*]...  
  
 *primary* ::= *column-name*  
  
 &#124;*динамический параметр*  
  
 &#124; *literal*  
  
 &#124; ( *expression* )  
  
 *условие поиска* :: = *логическое значение термина* [или *условие поиска*]  
  
 *select-list* ::= \* &#124; *select-sublist* [, *select-sublist*]...  (*select-list* cannot contain parameters.)  
  
 *select-sublist* ::= *expression*  
  
 *спецификации сортировки* :: = {*unsigned integer &#124; имя_столбца*} [*ASC &#124; DESC*]  
  
 *table-identifier* ::= *user-defined-name*  
  
 *table-name* ::= *table-identifier*  
  
 *table-reference* ::= *table-name*  
  
 *table-reference-list* ::= *table-reference* [,*table-reference*]...  
  
 *term* ::= *factor* &#124; *term* {\*&#124; */* } *factor*  
  
 *unsigned-integer* ::= {*digit*}  
  
 *верхний регистр букв* :: = *объект &#124; B &#124; C &#124; D &#124; E &#124; F &#124; G &#124; H &#124; я &#124; J &#124; K &#124; L &#124; M &#124; N &#124; O &#124; P &#124;Q &#124; R &#124; S &#124; T &#124; U &#124; V &#124; W &#124; X &#124; Y &#124; Z*  
  
 *user-defined-name* ::= *letter*[*digit* &#124; *letter* &#124; *_* ]...
