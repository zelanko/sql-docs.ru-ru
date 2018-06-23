---
title: Поведения курсоров | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- version-based optimistic concurrency
- cursors [ODBC], cursor behaviors
- ODBC applications, cursors
- SQL_ATTR_CURSOR_SENSITIVITY option
- SQL_ATTR_CURSOR_SCROLLABLE option
- sensitivity behavior of cursor
- ODBC cursors, cursor behaviors
ms.assetid: 742ddcd2-232b-4aa1-9212-027df120ad35
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 15aee78cfc531a7b80e034021b26404e5735a0ec
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36086688"
---
# <a name="cursor-behaviors"></a>Режимы работы курсоров
  ODBC поддерживает параметры ISO, предназначенные для указания поведения курсоров, задавая их прокручиваемость и чувствительность. Эти варианты поведения задаются с помощью параметров SQL_ATTR_CURSOR_SCROLLABLE и SQL_ATTR_CURSOR_SENSITIVITY во время вызова [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md). Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] реализует эти параметры, запрашивая серверные курсоры со следующими характеристиками.  
  
|Параметры режима работы курсоров|Запрошенные характеристики серверного курсора|  
|------------------------------|---------------------------------------------|  
|SQL_SCROLLABLE и SQL_SENSITIVE|Курсор, управляемый набором ключей, и основанный на версии оптимистический параллелизм|  
|SQL_SCROLLABLE и SQL_INSENSITIVE|Статический курсор и параллелизм в режиме «только чтение»|  
|SQL_SCROLLABLE и SQL_UNSPECIFIED|Статический курсор и параллелизм в режиме «только чтение»|  
|SQL_NONSCROLLABLE и SQL_SENSITIVE|Однопроходный курсор и основанный на версии оптимистический параллелизм|  
|SQL_NONSCROLLABLE и SQL_INSENSITIVE|Результирующий набор по умолчанию (последовательный доступ, только чтение)|  
|SQL_NONSCROLLABLE и SQL_UNSPECIFIED|Результирующий набор по умолчанию (последовательный доступ, только чтение)|  
  
 Основанный на версии оптимистический параллелизм требует **timestamp** столбца в базовой таблице. При запросе таблицы, у которого нет управления оптимистичным параллелизмом на основе версии **timestamp** столбец, сервер использует основанный на значениях оптимистического параллелизма.  
  
## <a name="scrollability"></a>Прокручиваемость  
 Если параметр SQL_ATTR_CURSOR_SCROLLABLE имеет значение SQL_SCROLLABLE, курсор поддерживает все различные значения для *FetchOrientation* параметр [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md). Если параметр SQL_ATTR_CURSOR_SCROLLABLE имеет значение SQL_NONSCROLLABLE, курсор поддерживает только *FetchOrientation* для SQL_FETCH_NEXT.  
  
## <a name="sensitivity"></a>Чувствительность  
 Если параметр SQL_ATTR_CURSOR_SENSITIVITY имеет значение SQL_SENSITIVE, курсор отражает изменения данных, произведенные текущим пользователем или зафиксированные другими пользователями. Если параметр SQL_ATTR_CURSOR_SENSITIVITY имеет значение SQL_INSENSITIVE, курсор не отражает изменения данных.  
  
## <a name="see-also"></a>См. также  
 [Использование курсоров &#40;ODBC&#41;](using-cursors-odbc.md)  
  
  