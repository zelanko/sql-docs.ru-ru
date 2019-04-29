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
manager: craigg
ms.openlocfilehash: f1105f3adc3762e01c601d9c882bfbf0f05b9bad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026652"
---
# <a name="backward-compatibility-of-c-data-types"></a>Обратная совместимость типов данных C
SQL_C_SHORT SQL_C_LONG и SQL_C_TINYINT были заменены в ODBC типы со знаком и без знака: SQL_C_SSHORT и SQL_C_USHORT, SQL_C_SLONG и SQL_C_ULONG и SQL_C_STINYINT и SQL_C_UTINYINT. ODBC 3 *.x* драйвер, должны работать с ODBC 2. *x* приложения должны поддерживать SQL_C_SHORT SQL_C_LONG и SQL_C_TINYINT, так как при вызове, диспетчер драйверов передает их через драйвер.
