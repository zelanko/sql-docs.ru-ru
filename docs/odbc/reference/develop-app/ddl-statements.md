---
title: Заявления ОДН Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cae06efe6dd11e651e8553fa5c1004c2fa145478
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302995"
---
# <a name="ddl-statements"></a>Инструкции DDL
Язык определения данных (DDL) заявления сильно различаются между DBMSs. ODBC S'L определяет операторы для наиболее распространенных операций определения данных: создание и падение таблиц, индексов и представлений; изменение таблиц; и предоставление и отмена привилегий. Все остальные заявления DDL специфичны для исходных данных. Таким образом, совместимые приложения не могут выполнять некоторые операции определения данных. В общем, это не проблема, потому что такие операции, как правило, в высшей степени DBMS-специфических и лучше оставить на проприетарное программное обеспечение администрирования базы данных поставляется с большинством DBMS s или программы установки поставляется с драйвером.  
  
 Еще одна проблема в определении данных заключается в том, что имена типов данных сильно различаются между DBMS. Вместо определения стандартных имен типов данных и заставить драйверы преобразовать их в конкретные имена DBMS, **S'LGetTypeInfo** предоставляет приложениям возможность для обнаружения имен типов данных, специфийных для DBMS. Совместимые приложения должны использовать эти имена в инструкциях по S'L для создания и изменения таблиц; имена, перечисленные в [приложении C: Грамматика S'L](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md), и [Приложение D: Типы данных,](../../../odbc/reference/appendixes/appendix-d-data-types.md)являются только примерами.
