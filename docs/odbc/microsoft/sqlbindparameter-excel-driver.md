---
title: S'LBindParameter (Excel Драйвер) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLBindParameter
- SQLBindParameter function [ODBC], Excel Driver
ms.assetid: 40489bc5-3e2a-425e-892d-e0dc037f4d7a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c3a2d0a03bded3ec909cd158b36f52ee9007647e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300634"
---
# <a name="sqlbindparameter-excel-driver"></a>SQLBindParameter (драйвер для Excel)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах Excel. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 При использовании драйвера Microsoft Excel выполнение оператора INSERT, использующей параметр для вставки NULL в SQL_CHAR столбец, возвращает SQL_SUCCESS_WITH_INFO с s'LSTATE 01004 , "Данные Truncated".
