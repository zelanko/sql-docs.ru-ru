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
ms.openlocfilehash: 9100405c91387faa66b714a94b8259167ae31899
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63267656"
---
# <a name="ddl-statements"></a>Инструкции DDL
Инструкции определения языка DDL данных очень зависят от СУБД. Инструкции для наиболее распространенных операций определения данных определяет ODBC SQL: Создание и удаление таблицы, индексы и представления; Изменение таблиц; и предоставление и отзыв прав. Все другие инструкции DDL, зависящие от источника данных. Таким образом взаимодействующие приложения не может выполнить некоторые операции определения данных. Как правило это не проблема, так как эти операции, как правило настоятельно конкретных СУБД и лучше всего подходят влево, чтобы программное обеспечение для администрирования собственную базу данных в состав большинства СУБД или программы установки поставлялась с драйвером.  
  
 Другая проблема в определении данных будет этот тип данных, имена значительно варьироваться между СУБД. Вместо определения имен стандартные данные типа и принудительное драйверы для преобразования их имена СУБД **SQLGetTypeInfo** позволяет приложениям находить имена типов данных СУБД. Совместимые приложения должны использовать эти имена в инструкциях SQL для создания и изменения таблиц; именами, перечисленными в [приложение в: Грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), и [приложение г. Типы данных](../../../odbc/reference/appendixes/appendix-d-data-types.md), — это только примеры.
