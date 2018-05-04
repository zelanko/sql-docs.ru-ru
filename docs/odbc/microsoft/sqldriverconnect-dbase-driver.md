---
title: SQLDriverConnect (драйвера dBASE) | Документы Microsoft
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
- DBase driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], dBASE Driver
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7fe97e7c3541a86119459ba4c65ee247d06b96ac
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (драйвера dBASE)
> [!NOTE]  
>  В этом разделе сведения dBASE специфические для драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключаться к драйверу, без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **DBQ**, и **FIL**.  
  
 При использовании драйвера Paradox после открытия пользователем файл защищен паролем, другим пользователям не разрешено открывать тот же файл.  
  
 В следующей таблице показаны минимальное ключевых слов, необходимые для подключения к драйверу и приведен пример пар ключ значение, используемых с **SQLDriverConnect**. Полный список значений DRIVERID см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md).  
  
> [!NOTE]  
>  Если для dBASEdriver DBQ или его значения не указано, драйвер подключается к текущему каталогу.  
  
|Драйвер|Необходимые ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|dBASE|Драйвер DriverID|Driver = {Microsoft dBASE драйвера (*.dbf)}; DBQ = c:\temp; DriverID = 277|
