---
title: SLSetScrollOptions (Визуальный драйвер FoxPro ODBC) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 693e6e28-a845-41b1-9622-5058b0d87229
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19051fc83466bc40d72c029089cfe6ec45c20a08
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299424"
---
# <a name="sqlsetscrolloptions-visual-foxpro-odbc-driver"></a>SQLSetScrollOptions (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Эта тема содержит Visual FoxPro ODBC Драйвер-специфической информации. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 Поддержка: Частичная  
  
 Соответствие ODBC API: Уровень 2  
  
 Устанавливает параметры, которые контролируют поведение курсоров, связанных с ручкой оператора, *hstmt.*  
  
 Визуальный драйвер FoxPro ODBC поддерживает только SQL_CONCUR_READ_ONLY; он не поддерживает значение *fConcurrency* SQL_CONCUR_ROWVER. Водитель преобразует SQL_KEYSET_SIZE, SQL_CURSOR_DYNAMIC и SQL_CURSOR_KEYSET_DRIVEN в SQL_SCROLL_STATIC с ODBC_01S02 предупреждения.  
  
 Для получения более подробной информации, *ODBC Programmer's Reference* [см.](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)
