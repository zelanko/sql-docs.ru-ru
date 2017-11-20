---
title: "SQLDriverConnect (драйвер доступа) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0041199b1168bdd639f88d4c13663b73cb54efd7
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (драйвер доступа)
> [!NOTE]  
>  В этом разделе сведения драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 **SQLDriverConnect** позволяет подключаться к драйверу, без создания источника данных (DSN).  
  
 В строке подключения для всех драйверов поддерживаются следующие ключевые слова: **DSN**, **DBQ**, и **FIL**.  
  
 **UID** и **PWD** также поддерживаются ключевые слова.  
  
 Ключевое слово PWD не должно содержать специальные символы (см. SQL_SPECIAL_CHARACTERS в **SQLGetInfo** возвращаемые значения).  
  
 В следующей таблице показаны минимальное ключевых слов, необходимые для подключения к драйверу и приведен пример пар ключ значение, используемых с **SQLDriverConnect**. Полный список значений DRIVERID см. в разделе [SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md).  
  
|Драйвер|Необходимые ключевые слова|Примеры|  
|------------|-----------------------|--------------|  
|Microsoft Access|Драйвер DBQ|Driver = {драйвером Microsoft Access (*.mdb)}; DBQ = c:\\\temp\\\sample.mdb|

