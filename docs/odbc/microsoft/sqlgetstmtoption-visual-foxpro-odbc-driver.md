---
title: СЗЛГетСтмтOption (Визуальный водитель FoxPro ODBC) Документы Майкрософт
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
ms.openlocfilehash: 2624783f7bd55903f5741c62190626e455a9096d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295144"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Полная  
  
 Соответствие ODBC API: Первый уровень  
  
 Возвращает текущий параметр опции оператора.  
  
|*FOption*|Результаты|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-битное значение целых, что является закладкой для текущего рекордного числа|  
|SQL_ROW_NUMBER|32-битный ряд с указанием положения текущего ряда в наборе результатов|  
|SQL_TRANSLATE_DLL|Ошибка: "Водитель не способен"|  
  
 Визуальный Драйвер FoxPro ODBC не имеет dLLs перевода.  
  
 Для получения более подробной информации, *ODBC Programmer's Reference* [см.](../../odbc/reference/syntax/sqlgetstmtoption-function.md)
