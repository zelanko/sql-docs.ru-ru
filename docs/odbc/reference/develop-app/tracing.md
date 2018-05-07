---
title: Трассировка | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], about tracing
- driver manager [ODBC], tracing
ms.assetid: 77ed4c6c-d976-4eb2-8526-a12697b0ef83
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ff139b0074a22adc14903174ec031cd4176dca6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="tracing"></a>Трассировка
Диспетчер драйверов ODBC имеет трассировки средство, позволяющее последовательность вызовов функций, произведенным приложением ODBC, записывать и transcribed в файл журнала. Трассировка выполняется библиотекой DLL, который фиксирует вызовы между приложением и диспетчера драйверов, а также между диспетчером драйверов и драйвер трассировки. Этот метод трассировки заменяет трассировки, выполненных в ODBC 2 *.x* диспетчера драйверов и трассировки, выполняемые в ODBC 2 *.x* по ODBC Spy.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Библиотека DLL трассировки](../../../odbc/reference/develop-app/trace-dll.md)  
  
-   [Файл трассировки](../../../odbc/reference/develop-app/trace-file.md)  
  
-   [Включение трассировки](../../../odbc/reference/develop-app/enabling-tracing.md)  
  
-   [Динамическая трассировка](../../../odbc/reference/develop-app/dynamic-tracing.md)
