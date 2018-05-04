---
title: Обратная совместимость типов данных C | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], C data types
- compatibility [ODBC], C data types
- data types [ODBC], backward compatibility
- C data types [ODBC], backward compatibility
ms.assetid: b1453a65-ae03-4061-b0cf-a8434d8bc40b
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c2f14b9505b6908c4e560efda27c7e2a670e73e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="backward-compatibility-of-c-data-types"></a>Обратная совместимость типов данных C
SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT были заменены в ODBC знаковых и беззнаковых типов: SQL_C_SSHORT и SQL_C_USHORT, SQL_C_SLONG и SQL_C_ULONG и SQL_C_STINYINT и SQL_C_UTINYINT. ODBC 3 *.x* драйвер, который должен работать с ODBC 2. *x* приложения должны поддерживать SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT, так как при их вызове диспетчера драйверов передает их с помощью драйвера.
