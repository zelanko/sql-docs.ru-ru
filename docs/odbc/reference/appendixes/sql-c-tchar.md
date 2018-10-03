---
title: SQL_C_TCHAR | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- sql_c_tchar [ODBC]
- pseudo-type identifiers [ODBC], SQL_C_TCHAR
- data types [ODBC], pseudo-type identifiers
ms.assetid: 9e27c8bd-ee15-4ce9-b70a-34cf1bf16f4c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 42afb911dda26cbda53f9cd14c883abb3775b94b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792353"
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
Идентификатор типа SQL_C_TCHAR фактически не определяет тип данных; он представляет собой макрос, который существует в файле заголовка для преобразования в формат Юникод. Они заменяются SQL_C_CHAR или SQL_C_WCHAR в зависимости от параметра Юникод **#define**. Это полезно для приложения передачи символьных данных, который компилируется как ANSI, так и приложения с поддержкой Юникода.
