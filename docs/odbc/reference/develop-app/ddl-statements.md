---
title: Инструкции DDL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14d9eb18a5c6c3cbd62cea0c668f3c53f8da48f3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626682"
---
# <a name="ddl-statements"></a>Инструкции DDL
Инструкции определения языка DDL данных очень зависят от СУБД. Инструкции для наиболее распространенных операций определения данных определяет ODBC SQL: Создание и удаление таблицы, индексы и представления; Изменение таблиц; и предоставление и отзыв прав. Все другие инструкции DDL, специфического для источника данных. Таким образом взаимодействующие приложения не может выполнить некоторые операции определения данных. Как правило это не проблема, так как эти операции, как правило настоятельно конкретных СУБД и лучше всего подходят влево, чтобы программное обеспечение для администрирования собственную базу данных в состав большинства СУБД или программы установки поставлялась с драйвером.  
  
 Другая проблема в определении данных будет этот тип данных, имена значительно варьироваться между СУБД. Вместо определения имен стандартные данные типа и принудительное драйверы для преобразования их имена СУБД **SQLGetTypeInfo** позволяет приложениям находить имена типов данных СУБД. Совместимые приложения должны использовать эти имена в инструкциях SQL для создания и изменения таблиц; именами, перечисленными в [грамматике SQL в C: приложение](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), и [типы данных приложение D:](../../../odbc/reference/appendixes/appendix-d-data-types.md), — это только примеры.
