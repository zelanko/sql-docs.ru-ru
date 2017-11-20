---
title: "Статический SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1675f70b67f5c600aada546f8caf8eb8b99df99a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="static-sql"></a>Статический SQL
Embedded SQL, показанные в [пример Embedded SQL](../../odbc/reference/embedded-sql-example.md) известен как статический SQL. Поскольку являются статическими; инструкций SQL в программе вызывается статический SQL то есть они не изменяют при каждом запуске программы. Как описано в предыдущем разделе, эти инструкции, компилируются при компиляции остальные части программы.  
  
 Статический SQL работает также во многих случаях и может использоваться в любом приложении, для которого доступ к данным можно определить во время разработки программы. Например программа ввода заказа всегда используется той же инструкции вставить новый заказ, и системе бронирования авиабилетов всегда использует той же инструкции, чтобы изменить состояние рабочее место для зарезервированных. Каждая из этих инструкций будет обобщить с помощью переменных узла. разные значения могут быть вставлены в заказе на продажу и различных рабочих мест может быть зарезервирована. Поскольку такие инструкции могут быть жестко запрограммированы в программе, такие программы имеют преимущество инструкций необходимо проанализировать, проверки и оптимизации только один раз во время компиляции. Это приводит к появлению кода относительно быстро.

