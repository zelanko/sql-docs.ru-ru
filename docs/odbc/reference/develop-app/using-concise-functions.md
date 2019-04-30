---
title: Использование сокращенных функций | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- concise functions [ODBC]
- functions [ODBC], concise functions
- descriptors [ODBC], concise functions
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d70d3ca60a046a355549260406edba261f805e4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63312483"
---
# <a name="using-concise-functions"></a>Использование сокращенных функций
Неявные доступа к дескрипторам некоторые функции ODBC. Программисты могут оказаться более удобным, чем вызов **SQLSetDescField** или **SQLGetDescField**. При вызове этих функций *краткими* функции, поскольку они выполняют ряд функций, включая задания или получения поля дескриптора. Некоторые сокращенных функций позволяют приложению задавать или получать несколько полей связанных дескриптор в одном вызове функции.  
  
 Сокращенных функций может вызываться не извлекая дескриптор для использования в качестве аргумента. Эти функции работают с дескриптор поля, связанные с дескриптором инструкции, которые они вызываются на.  
  
 Сокращенных функций **SQLBindCol** и **SQLBindParameter** выполнить привязку столбца или параметра, значение поля дескриптора, которые соответствуют их аргументов. Каждая из этих функций выполняет дополнительные задачи, чем просто дескрипторов. **SQLBindCol** и **SQLBindParameter** предоставляют полную спецификацию привязки данных столбца или динамических параметров. Приложение можно однако изменить индивидуальные сведения привязки путем вызова **SQLSetDescField** или **SQLSetDescRec** и полностью привязки можно принять несколько вызовов, подходящий для столбца или параметра Эти функции.  
  
 Сокращенных функций **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**, и  **SQLNumResultCols** извлечение значений в поля дескриптора.  
  
 **SQLSetDescRec** и **SQLGetDescRec** являются сокращенных функций, которые с помощью одного вызова, задать или получить несколько поля дескриптора, влияющих на тип данных и хранение данных столбца или параметра. **SQLSetDescRec** — эффективный способ изменить привязку столбца или параметра данных за один шаг.  
  
 **SQLSetStmtAttr** и **SQLGetStmtAttr** служить сокращенных функций в некоторых случаях. (См. в разделе [поля дескриптора](../../../odbc/reference/develop-app/descriptor-fields.md).)
