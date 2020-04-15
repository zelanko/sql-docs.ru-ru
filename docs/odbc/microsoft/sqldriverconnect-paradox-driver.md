---
title: S'LDriverConnect (Парадокс Драйвер) Документы Майкрософт
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
ms.openlocfilehash: 68171cfab2b65634433b107d829dd2a6e9b5c985
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307115"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (драйвер для Paradox)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах парадокса. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 **SLDriverConnect** позволяет подключиться к драйверу без создания источника данных (DSN).  
  
 Следующие ключевые слова поддерживаются в строке соединения для всех драйверов: **DSN,** **DB**и **FIL**.  
  
 Ключевое слово **PWD** также поддерживается. Ключевое слово PWD не должно включать в себя какие-либо специальные символы (см. SQL_SPECIAL_CHARACTERS в добавленных значениях **S'LGetInfo).**  
  
 После того, как защищенный паролем файл был открыт пользователем, другим пользователям не разрешается открывать тот же файл.  
  
 В следующей таблице показаны минимальные ключевые слова, необходимые для подключения к каждому драйверу, и приводится пример пар ключевых слов/значений, используемых в **s'LDriverConnect.** Полный список значений DRIVERID можно найти в [s'LConfigDataSource.](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)  
  
> [!NOTE]  
>  Если драйвер парадокса не указан dB или DefaultDir, драйвер подключается к текущему каталогу.  
  
|Драйвер|Требуются ключевые слова|Пример|  
|------------|-----------------------|-------------|  
|Парадокс|Водитель, ВодительID|Драйвер »Драйвер парадокса Microsoft »(.db); ДБЗК:-темп;ДрайверИД-26|
