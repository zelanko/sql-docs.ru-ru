---
title: "Юникод | Документы Microsoft"
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
- Unicode [ODBC]
- Unicode [ODBC], about Unicode
ms.assetid: 113e1c9a-8333-4805-86f2-e4b57ab816a5
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e14c37b8246b3ffa541325f079b035424d2ff68
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="unicode"></a>Юникод
Юникод определяет кодировку для символов на различных языках.  
  
 Дополнительные сведения о стандарте Юникод см. в разделе [Unicode Consortium](http://www.unicode.org).  
  
 В Юникоде определяются универсального набора знаков. Кодовая страница Windows ANSI определяет набор символов, обычно содержащий знаков для одного языка. Он может быть труднее написать приложение, которое требуется использовать разные кодовые страницы.  
  
 Юникод не требуется кодовая страница. Каждая точка кода сопоставляется с одного символа в какой-либо язык.  
  
 В настоящее время только Юникод, кодировка, ODBC поддерживает — UCS-2, который использует 16-разрядное целое (фиксированной длины) для представления символа. Юникод позволяет приложениям работать на разных языках.  
  
 Диспетчер драйверов ODBC 3.5 (или более поздней версии) поддерживает Юникод. Это влияет на две основные области: вызовами функции и строковые типы данных. Диспетчер драйверов maps строка аргументы функций и строковые данные, требуемые для приложений и драйверов, из которых может быть поддержкой ANSI или Юникод. Эти две области подробно описываются в разделах, [аргументы функции Юникода](../../../odbc/reference/develop-app/unicode-function-arguments.md) и [данных в Юникоде](../../../odbc/reference/develop-app/unicode-data.md).  
  
 Диспетчер драйверов ODBC 3.5 (или более поздней версии) поддерживает использование драйвера Юникода с помощью приложения с поддержкой Юникода и приложение ANSI. Оно также поддерживает использование драйвера ANSI с приложением ANSI. Диспетчер драйверов предоставляет ограниченный сопоставление Unicode-ANSI для приложения с поддержкой Юникода, работе с драйвером ANSI.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Аргументы функции Юникода](../../../odbc/reference/develop-app/unicode-function-arguments.md)  
  
-   [Данные в Юникоде](../../../odbc/reference/develop-app/unicode-data.md)
