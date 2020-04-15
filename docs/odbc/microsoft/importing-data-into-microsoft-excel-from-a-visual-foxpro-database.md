---
title: Импорт данных в Microsoft Excel из визуальной базы данных FoxPro (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1bfd86233e5a0a406febcb30bf7a4fae595e53d2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287674"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Импорт данных из базы данных Visual FoxPro в Microsoft Excel
Вы можете импортировать визуальные данные FoxPro в свой лист Microsoft Excel, если вы определили источник данных для него. Для получения информации о создании источника данных Visual FoxPro [см. Доступ к визуальному источнику данных FoxPro от Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Импорт визуальных данных FoxPro в лист Microsoft Excel  
  
1.  Откройте электронную таблицу Microsoft Excel.  
  
2.  Из меню данных выберите Получить внешние данные. Открывается запрос Microsoft.  
  
3.  В диалоговом окне Select Data Source выберите источник данных Visual FoxPro, а затем нажмите «Использование».  
  
4.  Если база данных, доступ к ней имеет источник данных, включает таблицы, выберите таблицу из диалогового окна Add Tables. Запрос Майкрософт отображает добавленную таблицу в верхней половине конструктора запросов.  
  
    > [!NOTE]  
    >  Список Владельца недоступен в этом диалоговом поле, поскольку драйвер не поддерживает владельцев. Список базы данных недоступен, поскольку драйвер не поддерживает несколько баз данных в источнике данных.  
  
5.  Выберите поля для запроса, перетащив их из таблицы на нижнюю половину конструктора.  
  
6.  Закройте запрос Microsoft. Выбранные данные импортируются в электронную таблицу Microsoft Excel.
