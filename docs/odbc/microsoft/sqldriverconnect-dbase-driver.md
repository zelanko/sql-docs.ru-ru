---
title: SQLDriverConnect (драйвер для dBASE) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], dBASE Driver
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39d3d062ef8371ce37f812216cbb642d103eff98
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81302925"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (драйвер для dBASE)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу dBASE. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключаться к драйверу без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **ДБК** **и.**  
  
 При использовании драйвера Paradox после открытия пользователем файла, защищенного паролем, другим пользователям не разрешается открывать тот же файл.  
  
 В следующей таблице приведены минимальные ключевые слова, необходимые для подключения к каждому драйверу, а также пример пар «ключевое слово-значение», используемых с **SQLDriverConnect**. Полный список значений ДРИВЕРИД см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).  
  
> [!NOTE]  
>  Если ДБК или Дефаултдир не указаны для Дбаседривер, драйвер будет подключаться к текущему каталогу.  
  
|Драйвер|Требуются ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|dBASE|Драйвер, Дриверид|Драйвер = {Драйвер Microsoft dBASE Driver (*. dbf)}; ДБК = c:\temp; Дриверид = 277|
