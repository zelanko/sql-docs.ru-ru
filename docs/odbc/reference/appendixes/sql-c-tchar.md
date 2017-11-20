---
title: "SQL_C_TCHAR | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b518868f3b6e77f9351877d57dc97cfee01a2c67
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlctchar"></a>SQL_C_TCHAR
Идентификатор типа SQL_C_TCHAR фактически не определяет тип данных. Это макрос, который существует в файле заголовка для преобразования в формат Юникод. Он не будет заменен SQL_C_CHAR или SQL_C_WCHAR в зависимости от настройки Юникод **#define**. Это полезно для приложения, передача символьных данных, который компилируется как ANSI и Unicode в приложении.

