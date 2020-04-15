---
title: Запись заголовка (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], diagnostic records
- header records [ODBC]
- diagnostic records [ODBC]
ms.assetid: d0fff1ed-5616-422a-a394-7ea1d2486f89
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 372185966cc1644147feb2683177ae3a5b69e788
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300184"
---
# <a name="header-record"></a>Запись заголовка
Поля в записи заголовка содержат общую информацию об выполнении функции, включая код возврата, количество строк, количество записей состояния и тип выполняемых отчетов. Запись заголовка всегда создается, если функция не возвращается SQL_INVALID_HANDLE. Полный список полей в записи заголовка приведен в описании [функции S'LGetDiagField.](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)
