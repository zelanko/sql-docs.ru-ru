---
title: Поддерживаемые типы данных Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d19cde2d531819a60229dd7a780181571e169503
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307785"
---
# <a name="supported-data-types"></a>Поддерживаемые типы данных
Типы данных, поддерживаемые DBMS, значительно различаются. Приложение может определить имена и характеристики поддерживаемых типов данных, позвонив по **телефону S'LGetTypeInfo.** Из-за больших различий в именах типов данных приложение должно использовать имена типов данных, возвращенные **s'LGetTypeInfo,** в **заявлениях CREATE TABLE.** Для получения дополнительной информации [см.](../../../odbc/reference/develop-app/data-types-in-odbc.md)
