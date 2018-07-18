---
title: Драйверы | Документы Microsoft
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1906e61847537d3c89a5f2c3529172a9634713c0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32915199"
---
# <a name="drivers"></a>Драйверы
*Драйверы* , библиотеки, которые реализуют функции API-интерфейса ODBC. Каждый относится к определенной СУБД; Например драйвер для Oracle не может напрямую обращаться к данных в СУБД с Informix. Драйверы доступ к функциям базовой СУБД; они не требуются для реализации возможностей, не поддерживаемых в СУБД. Например если базовой СУБД не поддерживает внешние соединения, то не следует драйвер. Только основные исключением является то, что драйверы для СУБД, у которых нет автономного СУБД, такие как Xbase, необходимо реализовать компонента database engine, по крайней мере поддерживает минимальный объем SQL.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Задачи драйвера](../../odbc/reference/driver-tasks.md)  
  
-   [Архитектура драйвера](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>См. также  
 [Драйверы ODBC, предоставляемые корпорацией Майкрософт](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)
