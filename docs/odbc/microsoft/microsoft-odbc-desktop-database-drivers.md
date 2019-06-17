---
title: Драйверы Microsoft ODBC для настольных баз данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- Jet-based ODBC drivers [ODBC]
- ODBC desktop database drivers [ODBC], about desktop database drivers
- desktop database drivers [ODBC]
- Jet-based ODBC drivers [ODBC], about Jet-based ODBC drivers
- desktop database drivers [ODBC], about desktop database drivers
ms.assetid: 4e505c65-a8dd-4283-ae28-313d8a3aa046
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81cdf1738d35d89c35c34500900be79f7702f877
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045956"
---
# <a name="microsoft-odbc-desktop-database-drivers"></a>Драйверы ODBC Майкрософт для баз данных на настольном компьютере
ODBC — это API, который использует Structured Query Language (SQL) в качестве языка доступа к базе данных. С помощью того же исходного кода ODBC, которая включена в исходный код приложения доступны самых разнообразных систем управления базами данных (СУБД). Microsoft ODBC Desktop драйверы для баз данных пользователь приложения с поддержкой ODBC можно открыть, запроса и обновить базу данных рабочего стола через интерфейс ODBC.  
  
 Драйверы для баз данных Microsoft ODBC Desktop представляют собой Microsoft Jet базе набор драйверов ODBC. В то время как Microsoft ODBC Desktop Database Drivers 2.0 входят 16-разрядных и 32-разрядные драйверы, версии 3.0 и более поздние версии включают в себя только 32-битные драйверы, которые работают в Windows 95 и более поздних версиях Windows NT Workstation или версии 4.0, Windows 2000 Professional или Windows 2000 Server Сервер. Эти драйверы обеспечивают доступ к следующие типы источников данных:  
  
-   Microsoft Access  
  
-   Microsoft Excel  
  
-   Для Paradox  
  
-   для dBASE  
  
-   Text  
  
 См. в разделе [драйвер ODBC для Visual FoxPro](../../odbc/microsoft/visual-foxpro-odbc-driver.md) подробную документацию о драйвер ODBC для Microsoft Visual FoxPro®.  
  
> [!NOTE]  
>  Доступ к другим источникам данных, например Lotus 1-2-3, Microsoft Exchange и HTML, обеспечивается устанавливаемые драйверы ISAM (IISAM). Дополнительные сведения об этих драйверов см. в разделе «Доступ внешних данных» в *Microsoft Jet Database Engine Справочник по программированию*. База данных драйверы ODBC Desktop 4.0 не поддерживают форматы данных Btrieve и EMS.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Архитектура драйверов для баз данных на настольном компьютере](../../odbc/microsoft/desktop-database-drivers-architecture.md)  
  
-   [Журнал драйверов для баз данных на настольном компьютере](../../odbc/microsoft/history-of-the-desktop-database-drivers.md)  
  
-   [Поддержка продуктов](../../odbc/microsoft/product-support.md)  
  
-   [Реализация драйверов для баз данных на настольном компьютере](../../odbc/microsoft/implementing-desktop-database-drivers.md)  
  
-   [Замечания по программированию драйверов для Microsoft Access](../../odbc/microsoft/microsoft-access-driver-programming-considerations.md)  
  
-   [Замечания по программированию драйверов для Microsoft Excel](../../odbc/microsoft/microsoft-excel-driver-programming-considerations.md)  
  
-   [Замечания по программированию драйверов для Paradox](../../odbc/microsoft/paradox-driver-programming-considerations.md)  
  
-   [Замечания по программированию драйверов для dBASE](../../odbc/microsoft/dbase-driver-programming-considerations.md)  
  
-   [Замечания по программированию драйверов текстовых файлов](../../odbc/microsoft/text-file-driver-programming-considerations.md)  
  
-   [Дополнительная поддерживаемая грамматика SQL (ODBC)](../../odbc/microsoft/additional-supported-odbc-sql-grammar.md)  
  
-   [Ограничения](../../odbc/microsoft/limitations.md)  
  
-   [Ошибки ODBC](../../odbc/microsoft/odbc-errors.md)  
  
-   [Поддерживаемые функции API ODBC](../../odbc/microsoft/supported-odbc-api-functions.md)
