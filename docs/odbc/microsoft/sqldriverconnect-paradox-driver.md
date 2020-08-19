---
description: SQLDriverConnect (драйвер для Paradox)
title: SQLDriverConnect (Драйвер Paradox) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8b6bffe650bfc204660d7345b1bd5a051105fb5b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88421818"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (драйвер для Paradox)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу Paradox. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключаться к драйверу без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **ДБК** **и.**  
  
 Также поддерживается ключевое слово **PWD** . Ключевое слово PWD не должно включать специальные символы (см. раздел SQL_SPECIAL_CHARACTERS **SQLGetInfo** возвращаемые значения).  
  
 После открытия пользователем защищенного паролем файла другие пользователи не смогут открыть тот же файл.  
  
 В следующей таблице приведены минимальные ключевые слова, необходимые для подключения к каждому драйверу, а также пример пар «ключевое слово-значение», используемых с **SQLDriverConnect**. Полный список значений ДРИВЕРИД см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Если для драйвера Paradox не указан ДБК или Дефаултдир, драйвер будет подключаться к текущему каталогу.  
  
|Драйвер|Требуются ключевые слова|Пример|  
|------------|-----------------------|-------------|  
|Таблица|Драйвер, Дриверид|Драйвер = {Драйвер Microsoft Paradox (*. DB)}; ДБК = c:\temp; Дриверид = 26|
