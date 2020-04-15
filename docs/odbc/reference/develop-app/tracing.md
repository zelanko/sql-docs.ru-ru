---
title: Трассировка Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], about tracing
- driver manager [ODBC], tracing
ms.assetid: 77ed4c6c-d976-4eb2-8526-a12697b0ef83
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a08047409b203916fe5403cf28802d8570647cf
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298051"
---
# <a name="tracing"></a>Трассировка
Менеджер драйвера ODBC имеет механизм трассировки, который позволяет записывать и транскрибировать последовательность вызовов функций, сделанных приложением ODBC, и транскрибироваться в файл журнала. Отслеживание выполняется трассой DLL, которая фиксирует вызовы между приложением и менеджером драйвера, а также между менеджером водителя и водителем. Этот метод отслеживания заменяет трассировку, выполненную менеджером драйвера ODBC 2 *.x,* и трассировку, выполненную в ODBC 2 *.x* ODBC Spy.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Библиотека DLL трассировки](../../../odbc/reference/develop-app/trace-dll.md)  
  
-   [Файл трассировки](../../../odbc/reference/develop-app/trace-file.md)  
  
-   [Включение трассировки](../../../odbc/reference/develop-app/enabling-tracing.md)  
  
-   [Динамическая трассировка](../../../odbc/reference/develop-app/dynamic-tracing.md)
