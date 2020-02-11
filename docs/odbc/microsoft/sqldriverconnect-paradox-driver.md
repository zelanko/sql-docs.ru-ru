---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e17ca12e0c8745dcad30a3e5ce2c9689b041e7d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967485"
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
