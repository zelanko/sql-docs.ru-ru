---
title: "SQLAllocConnect (драйвер ODBC для Visual FoxPro) | Документы Microsoft"
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
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5614b69fddd5b5430f15e8266bef6872d4294f4e
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect (драйвер ODBC для Visual FoxPro)
> [!NOTE]  
>  Этот раздел содержит сведения по Visual FoxPro ODBC драйвера. Общие сведения об этой функции см. в соответствующем разделе [Справочник по API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Поддержка: полный  
  
 Соответствия ODBC API: Уровень Core  
  
 Выделяет память для дескриптора соединения *hdbc*, в среде определяется *henv*. Диспетчер драйверов обрабатывает этот вызов и вызывает драйвер **SQLAllocConnect** всякий раз, когда [SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md), **SQLBrowseConnect**, или [SQLDriverConnect ](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md) вызывается.  
  
 Дополнительные сведения см. в разделе [SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md) в *справочнике программиста ODBC*.

