---
title: Драйверы Microsoft ODBC Desktop для баз данных | Документация Майкрософт
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
ms.openlocfilehash: 8ee91a2e544babdd02a22bcbe426a7fb0d770f66
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68109684"
---
# <a name="microsoft-odbc-desktop-database-drivers"></a>Драйверы ODBC Майкрософт для баз данных на настольном компьютере
ODBC — это API, который использует язык SQL (SQL) в качестве языка доступа к базе данных. Вы можете получить доступ к широкому спектру систем управления базами данных (СУБД) с тем же исходным кодом ODBC, который напрямую включен в исходный код приложения. С драйверами базы данных Microsoft ODBC для настольных компьютеров пользователь приложения, поддерживающего ODBC, может открывать, запрашивать и обновлять базу данных настольных систем через интерфейс ODBC.  
  
 Драйверы Microsoft ODBC для настольных систем представляют собой набор драйверов ODBC на основе Microsoft Jet. В то время как драйверы Microsoft ODBC для настольных систем 2,0 включают как 16-разрядные, так и 32-разрядные драйверы, версии 3,0 и более поздних версий включают только 32-разрядные драйверы, работающие в Windows 95 и более поздних версиях, Windows NT Workstation или Server версии 4,0, Windows 2000 Professional или Windows 2000. Сервером. Эти драйверы предоставляют доступ к следующим типам источников данных:  
  
-   Microsoft Access  
  
-   Microsoft Excel  
  
-   Таблица  
  
-   dBASE  
  
-   текст  
  
 Подробную документацию по драйверу ODBC для Microsoft Visual FoxPro® см. в разделе [драйвер ODBC для Visual FoxPro](../../odbc/microsoft/visual-foxpro-odbc-driver.md) .  
  
> [!NOTE]  
>  Доступ к другим источникам данных, таким как Lotus 1-2-3, Microsoft Exchange и HTML, включается с помощью устанавливаемых драйверов ISAM (IISAM). Дополнительные сведения об этих драйверах см. в разделе "доступ к внешним данным" статьи *Справочник программиста по Microsoft Jet ядро СУБД*. Драйверы для баз данных ODBC для настольных систем 4,0 не поддерживают форматы данных Btrieve и EMS.  
  
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
