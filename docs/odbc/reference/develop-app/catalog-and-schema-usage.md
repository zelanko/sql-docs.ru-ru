---
title: Каталог и схема использования (ru) Документы Майкрософт
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
ms.openlocfilehash: 245bd007f070a94689283830ba7a1362e31353e6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306255"
---
# <a name="catalog-and-schema-usage"></a>Использование каталога и схемы
Источники данных не обязательно поддерживают каталог и имена схем в качестве идентификаторов имен объектов во всех инструкциях S'L. Источники данных могут поддерживать имена каталогов и схем в одном или нескольких из следующих классов заявлений S'L: заявления о языке манипулирования данными (DML), процедурные вызовы, заявления об определении таблицы, заявления об определении индекса и заявления о определении привилегий. Для определения классов выписок S'L, в которых можно использовать имена каталогов и схем, приложение вызывает **s'LGetInfo** с SQL_CATALOG_USAGE и SQL_SCHEMA_USAGE опций.
