---
title: S'LDriverConnect (Водитель Excel) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1108206bf38183887540b114fda5a1e913aa67d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307125"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (драйвер для Excel)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах Excel. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 **SLDriverConnect** позволяет подключиться к драйверу без создания источника данных (DSN).  
  
 Следующие ключевые слова поддерживаются в строке соединения для всех драйверов: **DSN,** **DB**и **FIL**.  
  
 В следующей таблице показаны минимальные ключевые слова, необходимые для подключения к каждому драйверу, и приводится пример пар ключевых слов/значений, используемых в **s'LDriverConnect.** Полный список значений DRIVERID можно найти в [s'LConfigDataSource.](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)  
  
> [!NOTE]  
>  Если для драйвера Microsoft Excel 3.0 или 4.0 не указаны DB или DefaultDir, драйвер подключается к текущему каталогу.  
  
|Драйвер|Обязательные ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3.0 или 4.0|Водитель, ВодительID|Драйвер »Водитель Microsoft Excel (я.xls); ДБЗК:-темп; ВодительID-278|  
|Microsoft Excel 5.0/7.0|Драйвер, DriverID, DB|Драйвер »Водитель Microsoft Excel (я.xls); ДБЗК:-темп-образец.xls; ВодительID-22|  
|Microsoft Excel 97 и более поздние|Драйвер, DriverID, DB|Драйвер »Водитель Microsoft Excel (я.xls); ДБЗК:-темп-образец.xls; ВодительID-790|
