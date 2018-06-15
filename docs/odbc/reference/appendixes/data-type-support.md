---
title: Поддержка типов данных | Документы Microsoft
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
- minimum SQL syntax supported [ODBC]
- ODBC drivers [ODBC], minimum SQL syntax supported
- data types [ODBC], ODBC drivers
- ODBC drivers [ODBC], data types
ms.assetid: 782b4490-372b-4366-aad7-a486fb8a07c8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 820e48a17e397bc9046c8ca431677074e69b8cb2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32905839"
---
# <a name="data-type-support"></a>Поддержка типов данных
Драйверы ODBC должны поддерживать хотя бы один из SQL_CHAR и SQL_VARCHAR. Поддержка других типов данных определяется уровень соответствия SQL-92 источника драйвера или данных. Приложение должно вызывать **SQLGetTypeInfo** для определения типов данных, поддерживаемых драйвером.  
  
 Дополнительные сведения о типах данных см. в разделе [типы данных приложение D:](../../../odbc/reference/appendixes/appendix-d-data-types.md).
