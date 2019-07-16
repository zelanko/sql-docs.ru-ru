---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e211797147c4da8f197247244f6f2805185b3b0b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053979"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (драйвер для Access)
> [!NOTE]  
>  В этом разделе сведения конкретного драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключиться к драйверу без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **DBQ**, и **FIL**.  
  
 **UID** и **PWD** ключевые слова, также поддерживаются.  
  
 Ключевое слово PWD не должен содержать специальные символы (см. в разделе SQL_SPECIAL_CHARACTERS в **SQLGetInfo** возвращаемые значения).  
  
 В следующей таблице показаны минимальные необходимые для подключения к драйверу ключевые слова и пример пар "ключевое слово значение", используемый с **SQLDriverConnect**. Полный список значений DRIVERID, см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Драйвер|Необходимые ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Microsoft Access|Драйвер, DBQ|Driver = {драйвером Microsoft Access (*.mdb)}; DBQ = c:\\\temp\\\sample.mdb|
