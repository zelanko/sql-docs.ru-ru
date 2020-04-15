---
title: S'LКолонки (драйвер dBASE) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColumns function [ODBC], dBASE Driver
- DBase driver [ODBC], SQLColumns
ms.assetid: 168171de-ab7d-4b5b-af7f-6e2106adfcce
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 242e4c2c95340aaf8bd4a8d8d41959b388a1cf70
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307895"
---
# <a name="sqlcolumns-dbase-driver"></a>SQLColumns (драйвер для dBASE)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах dBASE. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
|Столбец|Комментарии|  
|------------|--------------|  
|TABLE_QUALIFIER|Возвращается путь к каталогу.|  
|TABLE_OWNER|NULL возвращается в этой колонке, поскольку имя владельца не поддерживается.|  
|NULLABLE|SQL_NO_NULLS возвращается для столбцов, участвующих в основном ключевом или уникальном индексе.|
