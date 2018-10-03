---
title: SQLDriverConnect (драйвер для Paradox) | Документация Майкрософт
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
manager: craigg
ms.openlocfilehash: bae4a842729c8d302731ebf5fec22abb817f4c75
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654762"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (драйвер для Paradox)
> [!NOTE]  
>  Здесь приведены сведения об особенностях драйвер для Paradox. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключиться к драйверу без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **DBQ**, и **FIL**.  
  
 **PWD** ключевое слово также поддерживается. Ключевое слово PWD не должен содержать специальные символы (см. в разделе SQL_SPECIAL_CHARACTERS в **SQLGetInfo** возвращаемые значения).  
  
 После открытия защищенного паролем файла пользователем, другим пользователям не разрешено открывать тот же файл.  
  
 В следующей таблице показаны минимальные необходимые для подключения к драйверу ключевые слова и пример пар "ключевое слово значение", используемый с **SQLDriverConnect**. Полный список значений DRIVERID, см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md).  
  
> [!NOTE]  
>  Если драйвера для Paradox DBQ или его значения не указан, драйвер будет использоваться текущий каталог.  
  
|Драйвер|Необходимые ключевые слова|Пример|  
|------------|-----------------------|-------------|  
|Для Paradox|Драйвер, DriverID|Driver = {драйвер для Paradox Microsoft (*.db)}; DBQ = c:\temp; DriverID = 26|
