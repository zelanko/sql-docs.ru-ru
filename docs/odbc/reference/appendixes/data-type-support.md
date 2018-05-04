---
title: Поддержка типов данных | Документы Microsoft
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d58bae6de18ca4d7f67258e8d3a859d3ce0a6aa1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="data-type-support"></a>Поддержка типов данных
Драйверы ODBC должны поддерживать хотя бы один из SQL_CHAR и SQL_VARCHAR. Поддержка других типов данных определяется уровень соответствия SQL-92 источника драйвера или данных. Приложение должно вызывать **SQLGetTypeInfo** для определения типов данных, поддерживаемых драйвером.  
  
 Дополнительные сведения о типах данных см. в разделе [типы данных приложение D:](../../../odbc/reference/appendixes/appendix-d-data-types.md).
