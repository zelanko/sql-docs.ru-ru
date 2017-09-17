---
title: "Драйверы | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f25be027774c83a31077953eaf51ea8f643bf5e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="drivers"></a>Драйверы
*Драйверы* , библиотеки, которые реализуют функции API-интерфейса ODBC. Каждый относится к определенной СУБД; Например драйвер для Oracle не может напрямую обращаться к данных в СУБД с Informix. Драйверы доступ к функциям базовой СУБД; они не требуются для реализации возможностей, не поддерживаемых в СУБД. Например если базовой СУБД не поддерживает внешние соединения, то не следует драйвер. Только основные исключением является то, что драйверы для СУБД, у которых нет автономного СУБД, такие как Xbase, необходимо реализовать компонента database engine, по крайней мере поддерживает минимальный объем SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Драйвер задачи](../../odbc/reference/driver-tasks.md)  
  
-   [Архитектура драйвера](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>См. также:  
 [Драйверы ODBC, предоставляемые корпорацией Майкрософт](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
