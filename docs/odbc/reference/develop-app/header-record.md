---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7f5fe5cf6aae0d5953cc82b845396dd4164c7fa3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139015"
---
# <a name="header-record"></a>Запись заголовка
Поля в записи заголовка содержат общие сведения о выполнении функции, включая код возврата, число строк, число записей состояния и тип выполненной инструкции. Запись заголовка создается всегда, если функция не возвращает SQL_INVALID_HANDLE. Полный список полей в записи заголовка см. в описании функции [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md) .
