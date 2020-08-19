---
description: SQLDriverConnect (драйвер для Access)
title: SQLDriverConnect (драйвер для Access) | Документация Майкрософт
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
ms.openlocfilehash: 52bbcbfa379be53ea24c150d2522242e85e61fea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449216"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (драйвер для Access)
> [!NOTE]  
>  В этом разделе содержатся сведения, относящиеся к драйверу. Общие сведения об этой функции см. в соответствующем разделе [справочника по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключаться к драйверу без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **ДБК** **и.**  
  
 Также поддерживаются ключевые слова **UID** и **PWD** .  
  
 Ключевое слово PWD не должно включать специальные символы (см. раздел SQL_SPECIAL_CHARACTERS **SQLGetInfo** возвращаемые значения).  
  
 В следующей таблице приведены минимальные ключевые слова, необходимые для подключения к каждому драйверу, а также пример пар «ключевое слово-значение», используемых с **SQLDriverConnect**. Полный список значений ДРИВЕРИД см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Драйвер|Требуются ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Microsoft Access|Драйвер, ДБК|Драйвер = {Драйвер Microsoft Access (*. mdb)}; ДБК = c: \\ \temp \\ \сампле.МДБ|
