---
title: "Инструкции DDL | Документы Microsoft"
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
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4ebd19e39919265d2161927056bb9a4ebb9d55c2
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="ddl-statements"></a>Инструкции DDL
Инструкции определения языка DDL данных невероятно зависят от СУБД. Инструкции для наиболее распространенных операций определения данных определяет ODBC SQL: Создание и удаление таблиц, индексов и представления; Изменение таблиц; Предоставление и Отмена прав. Все другие инструкции DDL, зависящее от источника данных. Таким образом взаимодействующие приложения не может выполнять некоторые операции определения данных. Как правило это не проблема, из-за таких операций, как правило, очень конкретных СУБД и наилучшим образом влево, чтобы программное обеспечение администрирования собственную базу данных, поставляемых с большинством СУБД или программы установки поставлялась с драйвером.  
  
 Другая проблема в определении данных относится к этому типу данных, может различаться невероятно между СУБД. Вместо определения имен типов данных и принудительного драйверы для преобразования их имена СУБД **SQLGetTypeInfo** позволяет приложениям обнаруживать имена типов данных СУБД. Совместимые приложения должны использовать эти имена в инструкциях SQL для создания и изменения таблиц. имена, перечисленные в [грамматику SQL приложение C:](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), и [типы данных приложение D:](../../../odbc/reference/appendixes/appendix-d-data-types.md), — это только примеры.

