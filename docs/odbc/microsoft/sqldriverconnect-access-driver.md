---
title: S'LDriverConnect (Драйвер доступа) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a679cbb16ece3f239b1d17daabc8a294b808287
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302915"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (драйвер для Access)
> [!NOTE]  
>  Эта тема содержит информацию о драйверах доступа. Для получения общей информации об этой [ODBC API Reference](../../odbc/reference/syntax/odbc-api-reference.md)функции, см.  
  
 **SLDriverConnect** позволяет подключиться к драйверу без создания источника данных (DSN).  
  
 Следующие ключевые слова поддерживаются в строке соединения для всех драйверов: **DSN,** **DB**и **FIL**.  
  
 Ключевые слова **UID** и **PWD** также поддерживаются.  
  
 Ключевое слово PWD не должно включать в себя какие-либо специальные символы (см. SQL_SPECIAL_CHARACTERS в добавленных значениях **S'LGetInfo).**  
  
 В следующей таблице показаны минимальные ключевые слова, необходимые для подключения к каждому драйверу, и приводится пример пар ключевых слов/значений, используемых в **s'LDriverConnect.** Полный список значений DRIVERID можно найти в [s'LConfigDataSource.](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)  
  
|Драйвер|Обязательные ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Microsoft Access|Драйвер, ДБЗ|Драйвер драйвера доступа Microsoft (no.mdb); ДБЗК:\\«Темп»-образец.mdb\\|
