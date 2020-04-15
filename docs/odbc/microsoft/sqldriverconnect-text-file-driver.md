---
title: S'LDriverConnect (Драйвер текстовых файлов) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2768669b7dbb2066de0acedd5711911be0eac8fa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307105"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (драйвер для текстовых файлов)
> [!NOTE]  
>  Эта тема предоставляет информацию о драйверах, специфийных для драйверов текста. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 **SLDriverConnect** позволяет подключиться к драйверу без создания источника данных (DSN).  
  
 Следующие ключевые слова поддерживаются в строке соединения для всех драйверов: **DSN,** **DB**и **FIL**.  
  
 В следующей таблице показаны минимальные ключевые слова, необходимые для подключения к каждому драйверу, и приводится пример пар ключевых слов/значений, используемых в **s'LDriverConnect.** Полный список значений DRIVERID можно найти в [s'LConfigDataSource.](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)  
  
> [!NOTE]  
>  Если драйвер текста не указан dB или DefaultDir, драйвер подключается к текущему каталогу.  
  
|Драйвер|Требуются ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Text|Драйвер|Драйвер текста Microsoft (.txt;;\*. csv)) По умолчаниюДирик: Температура|
