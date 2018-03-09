---
title: "Импорт данных Visual FoxPro в Microsoft Access | Документы Microsoft"
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
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 4fd7585d60928bdae7f7be94c78c07ea35117cc0
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Импорт данных Visual FoxPro в Microsoft Access
Можно импортировать данные, хранящиеся в базе данных Visual FoxPro в базу данных Microsoft Access с помощью параметра импорта.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Для импорта данных Visual FoxPro в базе данных Microsoft Access  
  
1.  Откройте базу данных Microsoft Access.  
  
2.  В меню "файл" выберите внешние данные, затем импортировать.  
  
3.  В диалоговом окне «Импорт» выберите баз данных ODBC в списке типов файлов.  
  
4.  В диалоговом окне источников данных SQL выберите источник данных Visual FoxPro, которое подключается к данным FoxPro, необходимые для запроса и нажмите кнопку ОК.  
  
5.  В диалоговом окне Импорт объектов выберите одну или несколько таблиц, которые требуется импортировать и нажмите кнопку ОК. Имена таблиц Visual FoxPro, импортированные отображаются на вкладке таблицы базы данных Microsoft Access.  
  
 Теперь можно использовать Microsoft Access для работы с данными в импортированные таблицы Visual FoxPro. Данные, которые вы импортируете, моментальный снимок данных, хранимых в Visual FoxPro; изменения, внесенные в импортированные данные не отправляются обратно в источник данных Visual FoxPro.  
  
 Изменения, внесенные в Microsoft Access, чтобы изменить данные в источнике данных Visual FoxPro см. в разделе [запросов и обновление Visual FoxPro данных из Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
