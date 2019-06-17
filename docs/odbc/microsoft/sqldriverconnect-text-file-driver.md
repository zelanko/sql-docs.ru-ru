---
title: SQLDriverConnect (драйвер для текстовых файлов) | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 715d51aeccf3085b8f98cd4b49b4a14efa87afe9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63238323"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (драйвер для текстовых файлов)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера текстовый файл. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключиться к драйверу без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **DBQ**, и **FIL**.  
  
 В следующей таблице показаны минимальные необходимые для подключения к драйверу ключевые слова и пример пар "ключевое слово значение", используемый с **SQLDriverConnect**. Полный список значений DRIVERID, см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md).  
  
> [!NOTE]  
>  Если DBQ или его значения не указан текст драйвера, драйвер будет подключаться к текущий каталог.  
  
|Драйвер|Необходимые ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Text|Драйвер|Driver={Microsoft Text Driver (*.txt;\*.csv)}; DefaultDir=c:\temp|
