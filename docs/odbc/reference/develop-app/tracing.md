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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a08047409b203916fe5403cf28802d8570647cf
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298051"
---
# <a name="tracing"></a>Трассировка
Диспетчер драйверов ODBC имеет средство трассировки, которое позволяет записывать и расшифрованной в файл журнала последовательность вызовов функций, выполняемых приложением ODBC. Трассировка выполняется библиотекой DLL трассировки, которая фиксирует вызовы между приложением и диспетчером драйверов, а также между диспетчером драйверов и драйвером. Этот метод трассировки заменяет трассировку, выполняемую диспетчером драйверов ODBC 2 *. x* , и трассировку, выполненную в ODBC 2 *. x* с помощью ODBC Spy.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Библиотека DLL трассировки](../../../odbc/reference/develop-app/trace-dll.md)  
  
-   [Файл трассировки](../../../odbc/reference/develop-app/trace-file.md)  
  
-   [Включение трассировки](../../../odbc/reference/develop-app/enabling-tracing.md)  
  
-   [Динамическая трассировка](../../../odbc/reference/develop-app/dynamic-tracing.md)
