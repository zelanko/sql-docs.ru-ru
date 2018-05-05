---
title: Поддерживаемые типы данных | Документы Microsoft
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
- data types [ODBC], DBMS support
- interoperability [ODBC], data types
ms.assetid: a89d4bab-ef3c-45c2-aa72-2639b3e0f856
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66a631aeb28a0ef67fdb7c1d59d60424827b6b79
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="supported-data-types"></a>Поддерживаемые типы данных
Типы данных, поддерживаемые СУБД значительно изменяться. Приложение может определить имена и характеристики поддерживаемых типов данных, вызвав **SQLGetTypeInfo**. Из-за широкого колебаний имена типов данных, приложение должно использовать имена типов данных, возвращенных **SQLGetTypeInfo** в **CREATE TABLE** инструкции. Дополнительные сведения см. в разделе [типы данных ODBC в](../../../odbc/reference/develop-app/data-types-in-odbc.md).
