---
title: Обратная совместимость типов данных C | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], C data types
- compatibility [ODBC], C data types
- data types [ODBC], backward compatibility
- C data types [ODBC], backward compatibility
ms.assetid: b1453a65-ae03-4061-b0cf-a8434d8bc40b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dcfc4dd2ef1bee2783f073fbb85c0d911f84305a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037802"
---
# <a name="backward-compatibility-of-c-data-types"></a>Обратная совместимость типов данных C
SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT были заменены в ODBC с помощью подписанных и неподписанных типов: SQL_C_SSHORT и SQL_C_USHORT, SQL_C_SLONG и SQL_C_ULONG, а SQL_C_STINYINT и SQL_C_UTINYINT. Драйвер ODBC *3. x* , который должен работать с приложениями ODBC *2. x* , должен поддерживать SQL_C_SHORT, SQL_C_LONG и SQL_C_TINYINT, поскольку при их вызове диспетчер драйверов передает их в драйвер.
