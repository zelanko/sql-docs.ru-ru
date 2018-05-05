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
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 172d309a30312763bbef3605b2d88d265f0e3c6c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: 1 уровень  
  
 Возвращает оптимальный набор столбцов, который уникально идентифицирует строки в таблице.  
  
 Драйвер ODBC для Visual FoxPro возвращает столбцы, составляющие первичный ключ в таблице FoxPro. (См. [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) При вызове с *fColType* SQL_ROWVER, не указаны столбцы не возвращаются. **SQLSpecialColumns** работает только для источников данных, которые являются [баз данных](../../odbc/microsoft/visual-foxpro-terminology.md).  
  
 Дополнительные сведения см. в разделе [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) в *справочнике программиста ODBC*.
