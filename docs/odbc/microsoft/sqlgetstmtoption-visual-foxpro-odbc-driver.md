---
description: SQLGetStmtOption (драйвер ODBC для Visual FoxPro)
title: SQLGetStmtOption (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e57456ca05e39c12b83da80cd19c34f482c3d8df
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340090"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу ODBC для Visual FoxPro. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полная  
  
 Соответствие API-интерфейса ODBC: уровень один  
  
 Возвращает текущее значение параметра инструкции.  
  
|*Параметром fOption*|Возвращаемое значение|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-разрядное целочисленное значение, которое является закладкой для номера текущей записи|  
|SQL_ROW_NUMBER|32-разрядное целое число, указывающее расположение текущей строки в результирующем наборе|  
|SQL_TRANSLATE_DLL|Ошибка: "драйвер не поддерживается"|  
  
 Драйвер ODBC для Visual FoxPro не имеет библиотек DLL для перевода.  
  
 Дополнительные сведения см. в разделе [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) в *справочнике программиста по ODBC*.
