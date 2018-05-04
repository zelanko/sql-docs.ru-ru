---
title: SQLDriverConnect (драйвер Paradox) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6f34d1cd8d17c077a4879cf8dd39331533e3b0c5
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (драйвер Paradox)
> [!NOTE]  
>  В этом разделе сведения драйвера Paradox. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключаться к драйверу, без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **DBQ**, и **FIL**.  
  
 **PWD** также поддерживается ключевое слово. Ключевое слово PWD не должно содержать специальные символы (см. SQL_SPECIAL_CHARACTERS в **SQLGetInfo** возвращаемые значения).  
  
 После открытия пользователем защищенный паролем файл другим пользователям не разрешено открывать тот же файл.  
  
 В следующей таблице показаны минимальное ключевых слов, необходимые для подключения к драйверу и приведен пример пар ключ значение, используемых с **SQLDriverConnect**. Полный список значений DRIVERID см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Если для драйвера Paradox DBQ или его значения не указано, драйвер подключается к текущему каталогу.  
  
|Драйвер|Необходимые ключевые слова|Пример|  
|------------|-----------------------|-------------|  
|Paradox|Драйвер DriverID|Driver = {драйвера Paradox (*.db)}; DBQ = c:\temp; DriverID = 26|
