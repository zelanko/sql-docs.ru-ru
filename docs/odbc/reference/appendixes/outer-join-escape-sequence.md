---
title: Escape-последовательность внешнего соединения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- outer join escape sequence [ODBC]
- escape sequences [ODBC], outer join
- ODBC escape sequences [ODBC], outer join
ms.assetid: 2cfd1525-6677-4d36-9b9e-730496853750
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 576fe7268ccf71a8c926f6b1124ebbf8a8c711b0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100642"
---
# <a name="outer-join-escape-sequence"></a>Escape-последовательность внешнего соединения
ODBC использует escape-последовательности для внешних соединений. Синтаксис escape-последовательность выглядит следующим образом:  
  
```  
{oj outer-join}  
```  
  
## <a name="remarks"></a>Примечания  
 В форме Бэкуса-Наура синтаксис выглядит следующим образом:  
  
 *ODBC-outer-join-escape* ::=  
  
 *ODBC-esc инициатор* oj *внешнего соединения, ODBC-esc-признак конца*  
  
 *внешнее соединение* :: = *имя таблицы* [*корреляционное имя*] {СЛЕВА &#124; СПРАВА &#124; полный}  
  
 ВНЕШНЕЕ соединение {*имя таблицы* [*корреляционное имя*] &#124; *внешнего соединения*} ON  
  
 *Поиск-*  
  
 *условие*  
  
 *correlation-name* ::= *user-defined-name*  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC-esc-terminator* ::= }  
  
 Чтобы определить, какие части Эта инструкция поддерживаются, приложение вызывает **SQLGetInfo** с типом SQL_OJ_CAPABILITIES сведения. Для внешних соединений *условие поиска* должен содержать только условия соединения между указанными *имена таблиц*.
