---
description: Использование каталога и схемы
title: Использование каталога и схемы | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2506810c477e9d75e1d3b38f38185d22edf9d010
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494694"
---
# <a name="catalog-and-schema-usage"></a>Использование каталога и схемы
Источники данных не обязательно поддерживают имена каталогов и схем в качестве идентификаторов имен объектов во всех инструкциях SQL. Источники данных могут поддерживать имена каталогов и схем в одном или нескольких следующих классах инструкций SQL: инструкции языка обработки данных (DML), вызовы процедур, инструкции определения таблицы, инструкции определения индекса и инструкции определения привилегий. Чтобы определить классы инструкций SQL, в которых можно использовать имена каталогов и схем, приложение вызывает **SQLGetInfo** с параметрами SQL_CATALOG_USAGE и SQL_SCHEMA_USAGE.
