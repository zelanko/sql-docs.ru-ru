---
title: SQLSpecialColumns (драйвер ODBC для Visual FoxPro) | Документы Microsoft
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
ms.topic: article
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2d1b780f1fb217c7f20ee188aa8bd6ba713bd81
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Возвращает оптимальный набор столбцов, который уникально идентифицирует строки в таблице.  
  
 Драйвер ODBC для Visual FoxPro возвращает столбцы, составляющие первичный ключ в таблице FoxPro. (См. [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) При вызове с *fColType* SQL_ROWVER, не указаны столбцы не возвращаются. **SQLSpecialColumns** работает только для источников данных, которые являются [баз данных](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Дополнительные сведения см. в разделе [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) в *справочнике программиста ODBC*.
