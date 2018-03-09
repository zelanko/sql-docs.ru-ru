---
title: "Журнал драйверов для настольных баз данных | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6dfa1dc1b533c9e40175e9a3d29dc872344bd664
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="history-of-the-desktop-database-drivers"></a>Журнал драйверов для настольных баз данных
В следующей таблице показаны журнал версий драйверов базы данных.  
  
|Version|Дата выпуска|Description|  
|-------------|------------------|-----------------|  
|1.0|Август 1993|Использовать обработчик запросов SIMBA, созданных PageAhead программного обеспечения. SIMBA полученных вызовов ODBC и инструкций SQL, обработать их в устанавливаемый ISAM вызовы Microsoft Jet, а затем вызывает слоя диспетчеризации Microsoft Jet ISAM для загрузки и вызовов соответствующего устанавливаемого драйвера ISAM.|  
|2.0|Декабрь 1994|При использовании ODBC 2.0, который значительно расширен функции ODBC. Значительное изменение в версии 2.0 была замены, базы данных Microsoft Jet SIMBA обработчик запросов. С ядром базы данных Microsoft Jet драйверов базы данных гораздо более тесно интегрирован с Microsoft Jet устанавливаемые драйверы ISAM и технологии Microsoft Access. Значительные улучшения были:<br /><br /> — Встроенная поддержка Прокручиваемые курсоры.<br />— Встроенная поддержка внешние соединения, обновить и разнородных соединения и транзакции.<br />-32-разрядные версии драйверов для Microsoft Windows NT.|  
|3.0|Октябрь 1995 г.|Обеспечивает поддержку для Windows 95 и Windows NT Workstation или Windows NT Server 3.51. Только 32-разрядные драйверы были включены в этой версии; 16-разрядные драйверы для Windows версии 3.1 были удалены.|  
|3.5|Октябрь 1996|Эти драйверы были двухбайтовой кодировки (DBCS)-включена, были лучше всего подходят для использования с веб-приложений от предыдущих версий и размещено использование файла имена источников данных (DSN). Драйвер Microsoft Access был выпущен в RISC версии для использования на платформах альфа-канал для Windows 95/98 и Windows NT 3.51 и более поздних операционных системах.|  
|4.0|Позднее 1998|Обеспечивает поддержку Microsoft ядра Jet Юникоде вместе с совместимости для формата ANSI более ранних версий.|  
  
> [!NOTE]  
>  Драйверы version3.5 были разработаны для работы с ODBC2. *x*. Несмотря на то, что они также работают с ODBC 3.0, они не поддерживают все функции ODBC 3.0. Дополнительные сведения о работе этих драйверов ODBC 3.0 см. в разделе [обратной совместимости и соответствия стандартам](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md).
