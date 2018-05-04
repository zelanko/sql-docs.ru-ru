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
ms.topic: conceptual
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7f2367dcae307e3152005c1bb47885a274c6cc0a
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
Идентификатор типа SQL_C_TCHAR фактически не определяет тип данных. Это макрос, который существует в файле заголовка для преобразования в формат Юникод. Он не будет заменен SQL_C_CHAR или SQL_C_WCHAR в зависимости от настройки Юникод **#define**. Это полезно для приложения, передача символьных данных, который компилируется как ANSI и Unicode в приложении.
