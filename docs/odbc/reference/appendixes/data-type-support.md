---
title: Поддержка типа данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3abfe85ee32fb9ff4a8499c9949c0685563fec70
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284431"
---
# <a name="data-type-support"></a>Поддержка типов данных
Водители ODBC должны поддерживать по крайней мере один из SQL_CHAR и SQL_VARCHAR. Поддержка других типов данных определяется уровнем соответствия драйвера или источника данных S'L-92. Для определения типов данных, поддерживаемых драйвером, приложение должно позвонить в **s'LGetTypeInfo.**  
  
 Для получения дополнительной информации [Appendix D: Data Types](../../../odbc/reference/appendixes/appendix-d-data-types.md)о типах данных см.
