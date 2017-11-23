---
title: "Использование функций четкими | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- concise functions [ODBC]
- functions [ODBC], concise functions
- descriptors [ODBC], concise functions
ms.assetid: 31ac070f-8c59-4fd5-bd5a-466bb27dbca0
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f58efc6ca7f6587ce7d7070bc02ad935efe06bff
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="using-concise-functions"></a>С помощью краткого функций
Некоторые функции ODBC получают неявный доступ к дескрипторам. Авторы приложений может оказаться более удобным, чем вызов **SQLSetDescField** или **SQLGetDescField**. Эти функции вызываются *четкими* функции, так как они выполняют ряд функций, включая задания или получения поля дескриптора. Некоторые функции четкими позволяют приложению задавать или извлекать несколько связанных дескриптора полей в одном вызове функции.  
  
 Краткие функции могут вызываться не извлекая дескриптора для использования в качестве аргумента. Эти функции работают с поля дескриптора, связанные с дескриптором инструкции, их вызове.  
  
 Краткие функции **SQLBindCol** и **SQLBindParameter** связать столбец или параметр, указав поля дескриптора, которые соответствуют их аргументы. Каждая из этих функций выполняет дополнительные задачи, чем просто задание дескрипторов. **SQLBindCol** и **SQLBindParameter** обеспечивают полную спецификацию привязки данных столбца или динамических параметров. Приложение может Однако изменять индивидуальные сведения привязки путем вызова **SQLSetDescField** или **SQLSetDescRec** и полностью может привязать столбец или параметр посредством серии подходящий вызовов Эти функции.  
  
 Краткие функции **SQLColAttribute**, **SQLDescribeCol**, **SQLDescribeParam**, **SQLNumParams**, и  **SQLNumResultCols** получать значения в поля дескриптора.  
  
 **SQLSetDescRec** и **SQLGetDescRec** — это краткие функции, устанавливающие или получающие несколько поля дескриптора, которые влияют на тип данных и хранения данных столбца или параметра с помощью одного вызова. **SQLSetDescRec** — это эффективный способ, чтобы изменить привязку данных столбца или параметра в один шаг.  
  
 **SQLSetStmtAttr** и **SQLGetStmtAttr** служат в качестве краткого функции в некоторых случаях. (См. [поля дескриптора](../../../odbc/reference/develop-app/descriptor-fields.md).)
