---
title: Импорт данных в Microsoft Excel из базы данных Visual FoxPro | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: de81b606d31514cf6e7a518deeb68794d1011132
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63127287"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Импорт данных из базы данных Visual FoxPro в Microsoft Excel
Если вы определили для него источнику данных, можно импортировать данных Visual FoxPro в электронной таблице Excel. Сведения о создании источника данных Visual FoxPro, см. в разделе [доступ к источнику данных Visual FoxPro из Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Для импорта данных Visual FoxPro в электронной таблице Microsoft Excel  
  
1.  Откройте электронную таблицу Microsoft Excel.  
  
2.  В меню «Данные» выберите получение внешних данных. Откроется Microsoft Query.  
  
3.  В диалоговом окне Выбор источника данных выберите источник данных Visual FoxPro и нажмите кнопку использования.  
  
4.  Если база данных, поддерживаемого источника данных содержит таблицы, выберите таблицу, в диалоговом окне Добавить таблицы. Microsoft Query Отображает добавлена таблица в верхней части конструктора запросов.  
  
    > [!NOTE]  
    >  Список владельцев не доступен в этом диалоговом окне, поскольку драйвер не поддерживает владельцев. Список баз данных не доступен, поскольку драйвер не поддерживает несколько баз данных в источнике данных.  
  
5.  Выберите поля для запроса, перетащив их из таблицы в нижней части конструктора.  
  
6.  Закройте Microsoft Query. Данные, которые вы выбрали импортируется в электронной таблице Microsoft Excel.
