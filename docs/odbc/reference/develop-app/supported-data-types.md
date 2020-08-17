---
description: Поддерживаемые типы данных
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 349636553112449485d99fed269a43069974fccf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88385830"
---
# <a name="supported-data-types"></a>Поддерживаемые типы данных
Типы данных, поддерживаемые СУБД, значительно изменяются. Приложение может определить имена и характеристики поддерживаемых типов данных, вызвав **SQLGetTypeInfo**. Из-за широких вариаций в именах типов данных приложение должно использовать имена типов данных, возвращаемые функцией **SQLGetTypeInfo** в инструкциях **CREATE TABLE** . Дополнительные сведения см. [в разделе Типы данных в ODBC](../../../odbc/reference/develop-app/data-types-in-odbc.md).
