---
title: Каталога и схемы для использования | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], catalog names
- catalog names [ODBC]
- interoperability of SQL statements [ODBC], schema names
- schema names in SQL statements [ODBC]
ms.assetid: 84f7ef61-1ef1-46f3-9678-b087aa8e8e34
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0aa8e5c112bbd3bc807ecba821da2e754016b23a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="catalog-and-schema-usage"></a>Каталога и схемы для использования
Источники данных обязательно не поддерживают имена каталога и схемы как идентификаторы объектов имя во всех инструкциях SQL. Источники данных могут поддерживать имена каталога и схемы в одном или нескольких из следующих классов инструкций SQL: инструкций языка обработки данных (DML), вызовы процедур, инструкции определения таблицы, инструкции определения индекса и определение прав доступа инструкции. Чтобы определить классы инструкций SQL, в которой каталога и схемы можно использовать имена, приложение вызывает **SQLGetInfo** параметры SQL_CATALOG_USAGE и SQL_SCHEMA_USAGE.
