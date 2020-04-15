---
title: S'LDriverConnect (драйвер dBASE) Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302925"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (драйвер для dBASE)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах dBASE. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 **SLDriverConnect** позволяет подключиться к драйверу без создания источника данных (DSN).  
  
 Следующие ключевые слова поддерживаются в строке соединения для всех драйверов: **DSN,** **DB**и **FIL**.  
  
 При использовании драйвера Paradox после того, как защищенный паролем файл был открыт пользователем, другим пользователям не разрешается открывать тот же файл.  
  
 В следующей таблице показаны минимальные ключевые слова, необходимые для подключения к каждому драйверу, и приводится пример пар ключевых слов/значений, используемых в **s'LDriverConnect.** Полный список значений DRIVERID можно найти в [s'LConfigDataSource.](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)  
  
> [!NOTE]  
>  Если dB- или DefaultDir не указаны для dBASEdriver, драйвер подключится к текущему каталогу.  
  
|Драйвер|Требуются ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Dbase|Водитель, ВодительID|Драйвер »Водитель Microsoft dBASE»; ДБЗК:-темп; ВодительID-277|
