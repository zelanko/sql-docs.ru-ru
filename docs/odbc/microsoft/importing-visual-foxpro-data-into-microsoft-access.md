---
title: Импорт данных Visual FoxPro в Microsoft Access | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], importing
ms.assetid: a3591295-0a76-4e3c-b4fa-8bd4f1cde705
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f19b58ba93c94088c4cae19f1093d89c8decb843
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471305"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Импорт данных Visual FoxPro в Microsoft Access
Можно импортировать данные, хранящиеся в базе данных Visual FoxPro в базу данных Microsoft Access с помощью параметра импорта.  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Для импорта данных Visual FoxPro в базу данных Microsoft Access  
  
1.  Откройте базу данных Microsoft Access.  
  
2.  В меню "файл" выберите затем импортировать внешние данные.  
  
3.  В диалоговом окне импорта Выбор баз данных ODBC в списке типов файлов.  
  
4.  В диалоговом окне источников данных SQL выберите источник данных Visual FoxPro, которое подключается к данным FoxPro, необходимые для запроса и нажмите кнопку ОК.  
  
5.  В диалоговом окне Импорт объектов выберите одну или несколько таблиц, которые требуется импортировать и нажмите кнопку ОК. Имена таблиц Visual FoxPro, импортированных отображаются на вкладке таблицы базы данных Microsoft Access.  
  
 Теперь можно использовать Microsoft Access для работы с данными в импортированные таблицы Visual FoxPro. Данные, импортируемые, моментальный снимок данных, хранящихся в Visual FoxPro; изменения, внесенные в импортированные данные не отправляются обратно к источнику данных Visual FoxPro.  
  
 Если вы хотите, чтобы изменения, внесенные в Microsoft Access, чтобы изменить данные в источнике данных Visual FoxPro, см. в разделе [запросы и обновление Visual FoxPro данные из Microsoft Access](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md).
