---
title: SQL_C_TCHAR | Документы Microsoft
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
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 720ba82080f13d7ea9a8ecf47d9101627b756dec
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
Идентификатор типа SQL_C_TCHAR фактически не определяет тип данных. Это макрос, который существует в файле заголовка для преобразования в формат Юникод. Он не будет заменен SQL_C_CHAR или SQL_C_WCHAR в зависимости от настройки Юникод **#define**. Это полезно для приложения, передача символьных данных, который компилируется как ANSI и Unicode в приложении.
