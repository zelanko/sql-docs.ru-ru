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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 245bd007f070a94689283830ba7a1362e31353e6
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306255"
---
# <a name="catalog-and-schema-usage"></a>Использование каталога и схемы
Источники данных не обязательно поддерживают имена каталогов и схем в качестве идентификаторов имен объектов во всех инструкциях SQL. Источники данных могут поддерживать имена каталогов и схем в одном или нескольких следующих классах инструкций SQL: инструкции языка обработки данных (DML), вызовы процедур, инструкции определения таблицы, инструкции определения индекса и инструкции определения привилегий. Чтобы определить классы инструкций SQL, в которых можно использовать имена каталогов и схем, приложение вызывает **SQLGetInfo** с параметрами SQL_CATALOG_USAGE и SQL_SCHEMA_USAGE.
