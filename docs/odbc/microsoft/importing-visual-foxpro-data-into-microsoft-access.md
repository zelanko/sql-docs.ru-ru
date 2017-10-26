---
title: "Импорт данных Visual FoxPro в Microsoft Access | Документы Microsoft"
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
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6bdf35fb9c9b7b4688aa7f5bf4173b2a6a9eefb5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

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

