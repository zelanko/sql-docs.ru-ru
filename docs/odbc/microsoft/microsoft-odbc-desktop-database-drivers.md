---
title: Драйверы Microsoft ODBC для настольных баз данных | Документы Microsoft
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
- ODBC desktop database drivers [ODBC]
- Jet-based ODBC drivers [ODBC]
- ODBC desktop database drivers [ODBC], about desktop database drivers
- desktop database drivers [ODBC]
- Jet-based ODBC drivers [ODBC], about Jet-based ODBC drivers
- desktop database drivers [ODBC], about desktop database drivers
ms.assetid: 4e505c65-a8dd-4283-ae28-313d8a3aa046
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4411abb0d9eccf3a209f873d80360de92317ae48
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32903319"
---
# <a name="microsoft-odbc-desktop-database-drivers"></a>Драйверы Microsoft ODBC для настольных баз данных
ODBC — это API, использует язык SQL (Structured Query) в качестве языка базы данных access. Можно получить доступ к разнообразных систем управления базами данных (СУБД) с тем же кодом источника ODBC, которые непосредственно встроены в исходном коде приложения. Драйверы базы данных Microsoft ODBC рабочий стол пользователя приложения с поддержкой ODBC можно открыть запрос и обновления с помощью системной базы данных через интерфейс ODBC.  
  
 Microsoft ODBC системной базы данных являются Microsoft Jet основе набор драйверов ODBC. В то время как Microsoft ODBC системной базы данных Drivers 2.0 включает 16-разрядных и 32-разрядные драйверы, 3.0 и более поздние версии включают только 32-разрядные драйверы, которые работают в Windows 95 и более поздних версиях Windows NT Workstation или Server версии 4.0, Windows 2000 Professional или Windows 2000 Сервер. Эти драйверы обеспечивают доступ к следующие типы источников данных:  
  
-   Microsoft Access  
  
-   Microsoft Excel  
  
-   Paradox  
  
-   dBASE  
  
-   Текст  
  
 В разделе [драйвера ODBC для Visual FoxPro](../../odbc/microsoft/visual-foxpro-odbc-driver.md) подробную документацию о драйвере ODBC для Microsoft Visual FoxPro®.  
  
> [!NOTE]  
>  Доступ к другим источникам данных, например Lotus 1-2-3, Microsoft Exchange и HTML, обеспечивается устанавливаемые драйверы ISAM (IISAM). Дополнительные сведения об этих драйверов см. в разделе «Доступ к внешние данные» в *Microsoft Jet базы данных подсистемы Справочник программиста*. База данных драйверы ODBC Desktop 4.0 не поддерживают форматы данных Btrieve и EMS.  
  
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
