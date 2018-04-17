---
title: SQLDriverConnect (драйвер доступа) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a931f9f6118144e12b90a689e05d5d4f3810aa3b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
