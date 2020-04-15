---
title: История драйверов настольных баз данных (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], history
- ODBC desktop database drivers [ODBC], history
- desktop database drivers [ODBC], history
ms.assetid: b4a2aff8-bde7-4bd5-8580-bc50f27311c8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89434b397c07fdee751ca4272b65ac2eada94cf3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304985"
---
# <a name="history-of-the-desktop-database-drivers"></a>Журнал драйверов для баз данных на настольном компьютере
В следующей таблице показана история версии драйверов настольной базы данных.  
  
|Version|Дата выпуска|Описание|  
|-------------|------------------|-----------------|  
|1.0|Август 1993 г.|Использовалпроцессор запроса SIMBA, созданный PageAhead Software. SIMBA получил вызовы ODBC и выписки по S'L, обработал их в Microsoft Jet, устанавливаемые вызовы ISAM, а затем назвал слой отправки Microsoft Jet ISAM для загрузки и вызова соответствующего установленного драйвера ISAM.|  
|2.0|Декабрь 1994 года|Используется с ODBC 2.0, что значительно расширило функциональность ODBC. Основное изменение в версии 2.0 заключалось в том, что движок базы данных Microsoft Jet заменил процессор запроса SIMBA. С движком базы данных Microsoft Jet водители настольных баз данных гораздо более плотно интегрировались с установленными драйверами ISAM и технологией Microsoft Access. Значительные усовершенствования были:<br /><br /> - Поддержка коренных народов для прокрутки курсоров.<br />- Поддержка коренных народов для внешних соединений, updatable и неоднородных соединений и транзакций.<br />- 32-битные версии драйверов для Microsoft Windows NT.|  
|3.0|Октябрь 1995 г.|Предоставляет поддержку Windows 95 и Windows NT Workstation или NT Server 3.51. Только 32-битные драйверы были включены в этот релиз; 16-битные драйверы для версии Windows 3.1 были удалены.|  
|3,5|Октябрь 1996 г.|Эти драйверы были двойным байт-набором символов (DBCS) с поддержкой, были лучше приспособлены для использования с интернет-приложениями, чем предыдущие версии, и учитывали использование имен источников данных файлов (DSNs). Драйвер Microsoft Access был выпущен в версии RISC для использования на платформах Alpha для Windows 95/98 и Windows NT 3.51 и более поздних операционных систем.|  
|4,0|Конец 1998 года|Обеспечивает поддержку формата Microsoft Jet Engine Unicode наряду с совместимостью формата ANSI более ранних версий.|  
  
> [!NOTE]  
>  Драйверы версии3.5 были разработаны для работы с ODBC2. *x*. Хотя они также работают с ODBC 3.0, они не поддерживают все функции ODBC 3.0. Для получения дополнительной [информации](../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)о том, как эти драйверы работают с ODBC 3.0, см.
