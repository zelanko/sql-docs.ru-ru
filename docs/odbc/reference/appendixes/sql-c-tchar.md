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
ms.openlocfilehash: 68a03de54a8a5f63a994578d64c6bce5a1279138
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68057045"
---
# <a name="sqlctchar"></a>SQL_C_TCHAR
Идентификатор типа SQL_C_TCHAR фактически не определяет тип данных; он представляет собой макрос, который существует в файле заголовка для преобразования в формат Юникод. Они заменяются SQL_C_CHAR или SQL_C_WCHAR в зависимости от параметра Юникод **#define**. Это полезно для приложения передачи символьных данных, который компилируется как ANSI, так и приложения с поддержкой Юникода.
