---
title: Поддерживаемые типы данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5ec0f3943fd52540f094a23e9b3f9f3886e1371
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68114080"
---
# <a name="supported-data-types"></a>Поддерживаемые типы данных
Типы данных, поддерживаемые СУБД значительно изменяться. Приложение может определить имена и характеристик, поддерживаемых типов данных, вызвав **SQLGetTypeInfo**. Из-за широкого отличия в имена типов данных, приложение должно использовать имена типов данных, возвращенных **SQLGetTypeInfo** в **CREATE TABLE** инструкций. Дополнительные сведения см. в разделе [типы данных в ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
