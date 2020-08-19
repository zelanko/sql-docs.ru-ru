---
description: Драйверы ODBC Майкрософт для баз данных на настольном компьютере
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e60052bda67b792cbba81447d6ae20ebdeb565bd
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449436"
---
# <a name="microsoft-odbc-desktop-database-drivers"></a>Драйверы ODBC Майкрософт для баз данных на настольном компьютере
ODBC — это API, который использует язык SQL (SQL) в качестве языка доступа к базе данных. Вы можете получить доступ к широкому спектру систем управления базами данных (СУБД) с тем же исходным кодом ODBC, который напрямую включен в исходный код приложения. С драйверами базы данных Microsoft ODBC для настольных компьютеров пользователь приложения, поддерживающего ODBC, может открывать, запрашивать и обновлять базу данных настольных систем через интерфейс ODBC.  
  
 Драйверы Microsoft ODBC для настольных систем представляют собой набор драйверов ODBC на основе Microsoft Jet. В то время как 2,0 драйверы базы данных Microsoft ODBC для настольных систем включают как 16-разрядные, так и 32-разрядные драйверы, версии 3,0 и более поздних версий включают только 32-разрядные драйверы, работающие под управлением Windows 95 или более поздней версии, Windows NT Workstation или Server Version 4,0, Windows 2000 Professional или Windows 2000 Server. Эти драйверы предоставляют доступ к следующим типам источников данных:  
  
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
  
-   [Поддержка продукта](../../odbc/microsoft/product-support.md)  
  
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
