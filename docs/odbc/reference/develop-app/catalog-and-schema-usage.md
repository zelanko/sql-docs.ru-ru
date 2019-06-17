---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9476f4f928890514354f97ce604f871bd8a06d11
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63007892"
---
# <a name="catalog-and-schema-usage"></a>Использование каталога и схемы
Источники данных поддерживают не обязательно имена каталога и схемы как идентификаторы объектов имя во всех инструкциях SQL. Источники данных поддерживают имена каталога и схемы в одном или нескольких из следующих классов инструкций SQL: Инструкции языка обработки (DML) данных, вызовы процедур, инструкции определения таблицы, инструкции определения индекса и инструкции определения прав доступа. Чтобы определить классы инструкций SQL, в какие каталога и схемы можно использовать имена, приложение вызывает **SQLGetInfo** параметры SQL_CATALOG_USAGE и SQL_SCHEMA_USAGE.
