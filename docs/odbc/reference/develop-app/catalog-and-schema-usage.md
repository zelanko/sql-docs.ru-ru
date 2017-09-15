---
title: "Каталога и схемы для использования | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 217f68d674dc7099b741e77d287ca81fcc2688e5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="catalog-and-schema-usage"></a>Каталога и схемы для использования
Источники данных обязательно не поддерживают имена каталога и схемы как идентификаторы объектов имя во всех инструкциях SQL. Источники данных могут поддерживать имена каталога и схемы в одном или нескольких из следующих классов инструкций SQL: инструкций языка обработки данных (DML), вызовы процедур, инструкции определения таблицы, инструкции определения индекса и определение прав доступа инструкции. Чтобы определить классы инструкций SQL, в которой каталога и схемы можно использовать имена, приложение вызывает **SQLGetInfo** параметры SQL_CATALOG_USAGE и SQL_SCHEMA_USAGE.
