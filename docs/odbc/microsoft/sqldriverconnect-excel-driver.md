---
title: SQLDriverConnect (драйвер для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e38f2f513b7da2c9342470ba75e2ee11b3d7e52a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053901"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (драйвер для Excel)
> [!NOTE]  
>  В этом разделе приводятся сведения, относящиеся к драйверу Excel. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключаться к драйверу без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **ДБК** **и.**  
  
 В следующей таблице приведены минимальные ключевые слова, необходимые для подключения к каждому драйверу, а также пример пар «ключевое слово-значение», используемых с **SQLDriverConnect**. Полный список значений ДРИВЕРИД см. в разделе [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md).  
  
> [!NOTE]  
>  Если ДБК или Дефаултдир не указаны для драйвера Microsoft Excel 3,0 или 4,0, драйвер будет подключаться к текущему каталогу.  
  
|Драйвер|Требуются ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3,0 или 4,0|Драйвер, Дриверид|Драйвер = {Драйвер Microsoft Excel (*. xls)}; ДБК = c:\temp; Дриверид = 278|  
|Microsoft Excel 5.0/7.0|Driver, Дриверид, ДБК|Драйвер = {Драйвер Microsoft Excel (*. xls)}; ДБК = к:\темп\сампле.кслс; Дриверид = 22|  
|Microsoft Excel 97 и более поздние версии|Driver, Дриверид, ДБК|Драйвер = {Драйвер Microsoft Excel (*. xls)}; ДБК = к:\темп\сампле.кслс; Дриверид = 790|
