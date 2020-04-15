---
title: SQL_C_TCHAR Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 973d94b9b47371090a5f54fd3d259854ba78e9c2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304075"
---
# <a name="sql_c_tchar"></a>SQL_C_TCHAR
Идентификатор типа SQL_C_TCHAR фактически не идентифицирует тип данных; это макрос, который существует в файле заголовка для преобразования Unicode. Он заменяется SQL_C_CHAR или SQL_C_WCHAR в зависимости от настройки **#define**UNICODE. Это полезно для приложения, передающего данные о персонажах, которые компилируются как ANSI, так и в приложение Unicode.
