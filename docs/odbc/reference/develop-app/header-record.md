---
title: Заголовочная | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b7b6ffacb618dd2b7714be59814f3f1a88a52228
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47813922"
---
# <a name="header-record"></a>Запись заголовка
Поля в заголовочной записи содержат общие сведения о выполнении функции, включая код возврата, число строк, число записей состояния и типом выполняемой инструкции. Если функция возвращает SQL_INVALID_HANDLE всегда создается запись заголовка. Полный список полей в заголовочной записи, см. в разделе [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) описание функции.
