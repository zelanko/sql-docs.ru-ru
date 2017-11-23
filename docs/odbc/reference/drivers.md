---
title: "Драйверы | Документы Microsoft"
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 709bb1e5f7ac9aefa740897d517c48dc1525cdbb
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="drivers"></a>Драйверы
*Драйверы* , библиотеки, которые реализуют функции API-интерфейса ODBC. Каждый относится к определенной СУБД; Например драйвер для Oracle не может напрямую обращаться к данных в СУБД с Informix. Драйверы доступ к функциям базовой СУБД; они не требуются для реализации возможностей, не поддерживаемых в СУБД. Например если базовой СУБД не поддерживает внешние соединения, то не следует драйвер. Только основные исключением является то, что драйверы для СУБД, у которых нет автономного СУБД, такие как Xbase, необходимо реализовать компонента database engine, по крайней мере поддерживает минимальный объем SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Задачи драйвера](../../odbc/reference/driver-tasks.md)  
  
-   [Архитектура драйвера](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>См. также:  
 [Драйверы ODBC, предоставляемые корпорацией Майкрософт](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
