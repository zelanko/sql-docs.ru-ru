---
title: Escape-последовательность скалярной функции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36e108fcc61b2390d5fd72ac4ad322778ccfb4b2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057075"
---
# <a name="scalar-function-escape-sequence"></a>Escape-последовательность скалярной функции
ODBC использует escape-последовательности для скалярных функций. Синтаксис escape-последовательность выглядит следующим образом:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Примечания  
 В форме Бэкуса-Наура синтаксис выглядит следующим образом:  
  
 *Скаляр функция — escape-последовательность ODBC* :: =  
  
 *ODBC-esc инициатор* fn *скалярная функция ODBC-esc-terminator*  
  
 *Скалярная функция* :: = *имя функции* (*список аргументов*)  
  
 (Определения Нетерминальные слова *имя функции* и *имя функции* (*список аргументов*) являются производными от список скалярных функций в [ Приложение д. Скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-esc-initiator* ::= {  
  
 *ODBC-esc-terminator* ::= }  
  
 Чтобы определить источник данных поддерживает процедуры и драйвер поддерживает синтаксис вызова процедуры ODBC, приложение может вызвать **SQLGetInfo**. Дополнительные сведения см. в разделе [приложении E: Скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
