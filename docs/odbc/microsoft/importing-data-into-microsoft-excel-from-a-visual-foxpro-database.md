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
ms.openlocfilehash: 3c65635132c5f98b0565391122877f2e3c0a6714
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085547"
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
