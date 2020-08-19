---
description: SQLSpecialColumns (драйвер ODBC для Visual FoxPro)
title: SQLSpecialColumns (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e83568c8370b56decb7c3f7c90cda443b88a72a7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421608"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API ODBC: уровень 1  
  
 Извлекает оптимальный набор столбцов, уникально идентифицирующих строку в таблице.  
  
 Драйвер ODBC для Visual FoxPro возвращает столбцы, которые составляют первичный ключ в таблице FoxPro. (См. [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md).) Если вызывается с *фколтипе* , для которого задано значение SQL_ROWVER, столбцы не возвращаются. **SQLSpecialColumns** работает только для источников данных, являющихся [базами](../../odbc/microsoft/visual-foxpro-terminology.md)данных.  
  
 Дополнительные сведения см. в разделе [SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md) в *справочнике программиста по ODBC*.
