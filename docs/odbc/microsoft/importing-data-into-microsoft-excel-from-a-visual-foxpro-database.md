---
title: Импорт данных в Microsoft Excel из базы данных Visual FoxPro | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- importing data [ODBC]
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], importing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 3085bc4c-00a7-40e5-bffb-c3962cd3d509
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa6da8abaca5b3b14c48bc4324a50301d5a36d87
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Импорт данных в Microsoft Excel из базы данных Visual FoxPro
При указании источника данных для него можно импортировать данные Visual FoxPro в лист Microsoft Excel. Сведения о создании источника данных Visual FoxPro см. в разделе [доступ к источнику данных Visual FoxPro из Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Для импорта данных Visual FoxPro в лист Microsoft Excel  
  
1.  Откройте электронную таблицу Microsoft Excel.  
  
2.  В меню Данные выберите внешние данные. Откроется Microsoft Query.  
  
3.  В диалоговом окне Выбор источника данных выберите источник данных Visual FoxPro и нажмите кнопку использования.  
  
4.  Если база данных, осуществляется из источника данных содержит таблицы, выберите таблицу, в диалоговом окне Добавить таблицы. Microsoft Query добавлена таблица отображается в верхней части конструктора запросов.  
  
    > [!NOTE]  
    >  Список владельцев не доступен в этом диалоговом окне, поскольку драйвер не поддерживает владельцев. Список баз данных недоступен, так как драйвер не поддерживает несколько баз данных в источнике данных.  
  
5.  Выберите поля для запроса, перетащив их из таблицы в нижней части конструктора.  
  
6.  Закройте Microsoft Query. Выбранные данные импортируется в электронную таблицу Microsoft Excel.
