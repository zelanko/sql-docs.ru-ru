---
description: Запись заголовка
title: Запись заголовка | Документация Майкрософт
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
ms.openlocfilehash: 4de764381e54a0b3485130c1a3bdf25b2a9bf9fa
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88476646"
---
# <a name="header-record"></a>Запись заголовка
Поля в записи заголовка содержат общие сведения о выполнении функции, включая код возврата, число строк, число записей состояния и тип выполненной инструкции. Запись заголовка создается всегда, если функция не возвращает SQL_INVALID_HANDLE. Полный список полей в записи заголовка см. в описании функции [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .
