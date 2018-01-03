---
title: "SQLTransact (драйвер доступа) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Access driver [ODBC], SQLTransact
- SQLTransact function [ODBC], Access Driver
ms.assetid: 892b79c7-9e20-4d1f-bc60-d4b25694ca25
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 418185791c921e55762456f7fd66584879a447e3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="sqltransact-access-driver"></a>SQLTransact (драйвер доступа)
> [!NOTE]  
>  В этом разделе сведения драйвера доступа. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Когда используется драйвер Microsoft Access, поддерживается параметром SQL_COMMIT и SQL_ROLLBACK для *fType* аргумента в вызове **SQLTransact**.  
  
 В случае сбоя в процессе фиксации этой базы данных могут быть восстановлены с помощью параметра восстановления базы данных в программе установки драйвера Microsoft Access или с помощью ключевого слова REPAIR_DB в **SQLConfigDataSource** функция.
