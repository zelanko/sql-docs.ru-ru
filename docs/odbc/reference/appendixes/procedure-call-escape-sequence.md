---
title: Escape-последовательность вызова процедуры | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aa936eb9f8ef3328945d4ece63fb36432a5fd618
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100590"
---
# <a name="procedure-call-escape-sequence"></a>Escape-последовательность вызова процедуры
ODBC использует escape-последовательности для вызовов процедур. Синтаксис escape-последовательность выглядит следующим образом:  
  
 **{** [? =]**вызвать** *имя процедуры*[ **(** [*параметр*] [, [*параметр*]]... **)** ] **}**  
  
 В форме Бэкуса-Наура синтаксис выглядит следующим образом:  
  
 *ODBC-procedure-escape* ::=  
  
 &#124;*ODBC-esc инициатор* [? =] вызовите *процедуры ODBC esc признак конца.*  
  
 *procedure* ::= *procedure-name* &#124; *procedure-name* (*procedure-parameter-list*)  
  
 *procedure-identifier* ::= *user-defined-name*  
  
 *Имя процедуры* :: = *идентификатор процедуры*  
  
 &#124;*имя владельца*. *Идентификатор процедуры*  
  
 &#124;*разделитель каталога имя каталога* *идентификатор процедуры*  
  
 &#124;*разделитель каталога имя каталога* [*имя владельца*]. *Идентификатор процедуры*  
  
 (Третий синтаксис верен, только в том случае, если источник данных не поддерживает владельцев).  
  
 *owner-name* ::= *user-defined-name*  
  
 *catalog-name* ::= *user-defined-name*  
  
 *catalog-separator* ::= {*implementation-defined*}  
  
 (Разделитель каталогов, который возвращается через **SQLGetInfo** с параметром сведения SQL_CATALOG_NAME_SEPARATOR.)  
  
 *procedure-parameter-list* ::= *procedure-parameter*  
  
 &#124;*параметр процедуры*, *список параметров процедуры*  
  
 *procedure-parameter* ::= *dynamic-parameter* &#124; *literal* &#124; *empty-string*  
  
 *empty-string* ::=  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC-esc-terminator* ::= }  
  
 (Если параметр процедуры является пустой строкой, в процедуре используется значение по умолчанию для этого параметра.)  
  
 Чтобы определить источник данных поддерживает процедуры и драйвер поддерживает синтаксис вызова процедуры ODBC, приложение может вызвать **SQLGetInfo** с типом SQL_PROCEDURES сведения.
