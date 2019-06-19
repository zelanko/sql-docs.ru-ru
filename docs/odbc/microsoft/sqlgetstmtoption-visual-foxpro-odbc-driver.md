---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 373f5e13712ef7b0864401ea3d2c204cb03ebb09
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63240256"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения Visual FoxPro ODBC-драйвером. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: Полное  
  
 Соответствие API ODBC: Один уровень  
  
 Возвращает текущее значение параметра инструкции.  
  
|*fOption*|Возвращает|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-разрядное целочисленное значение, — это закладка для номер текущей записи|  
|SQL_ROW_NUMBER|установите 32-разрядное целое число, задают позицию получаемого текущей строки в результат|  
|SQL_TRANSLATE_DLL|Ошибка: «Драйвер не поддерживает»|  
  
 Драйвер ODBC для Visual FoxPro имеет без преобразования библиотек DLL.  
  
 Дополнительные сведения см. в разделе [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) в *Справочник по программированию ODBC*.
