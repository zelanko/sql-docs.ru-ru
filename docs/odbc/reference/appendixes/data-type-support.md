---
title: Поддержка типов данных | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81284431"
---
# <a name="data-type-support"></a>Поддержка типов данных
Драйверы ODBC должны поддерживать хотя бы один SQL_CHAR и SQL_VARCHAR. Поддержка других типов данных определяется уровнем соответствия SQL-92 источника данных или драйвера. Приложение должно вызывать **SQLGetTypeInfo** для определения типов данных, поддерживаемых драйвером.  
  
 Дополнительные сведения о типах данных см. в разделе [Приложение D. типы данных](../../../odbc/reference/appendixes/appendix-d-data-types.md).
