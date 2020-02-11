---
title: Трассировка | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1a00861365df27357099176151bcd681e15e585e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67985123"
---
# <a name="tracing"></a>Трассировка
Диспетчер драйверов ODBC имеет средство трассировки, которое позволяет записывать и расшифрованной в файл журнала последовательность вызовов функций, выполняемых приложением ODBC. Трассировка выполняется библиотекой DLL трассировки, которая фиксирует вызовы между приложением и диспетчером драйверов, а также между диспетчером драйверов и драйвером. Этот метод трассировки заменяет трассировку, выполняемую диспетчером драйверов ODBC 2 *. x* , и трассировку, выполненную в ODBC 2 *. x* с помощью ODBC Spy.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Библиотека DLL трассировки](../../../odbc/reference/develop-app/trace-dll.md)  
  
-   [Файл трассировки](../../../odbc/reference/develop-app/trace-file.md)  
  
-   [Включение трассировки](../../../odbc/reference/develop-app/enabling-tracing.md)  
  
-   [Динамическая трассировка](../../../odbc/reference/develop-app/dynamic-tracing.md)
