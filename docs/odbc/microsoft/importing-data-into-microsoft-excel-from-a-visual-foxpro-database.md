---
description: Импорт данных из базы данных Visual FoxPro в Microsoft Excel
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a4bd1cf7983ed0a552de4f9d0f491960b48f0d7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88500297"
---
# <a name="importing-data-into-microsoft-excel-from-a-visual-foxpro-database"></a>Импорт данных из базы данных Visual FoxPro в Microsoft Excel
Вы можете импортировать данные Visual FoxPro в лист Microsoft Excel, если для него определен источник данных. Сведения о создании источника данных Visual FoxPro см. в разделе [доступ к источнику данных Visual FoxPro из Microsoft Excel](../../odbc/microsoft/accessing-a-visual-foxpro-data-source-from-microsoft-excel.md).  
  
### <a name="to-import-visual-foxpro-data-into-an-microsoft-excel-worksheet"></a>Импорт данных Visual FoxPro в лист Microsoft Excel  
  
1.  Откройте электронную таблицу Microsoft Excel.  
  
2.  В меню Данные выберите получить внешние данные. Откроется Microsoft Query.  
  
3.  В диалоговом окне Выбор источника данных выберите источник данных Visual FoxPro и нажмите кнопку использовать.  
  
4.  Если база данных, к которой обращается источник данных, содержит таблицы, выберите таблицу в диалоговом окне Добавление таблиц. Microsoft Query отобразит добавленную таблицу в верхней половине конструктора запросов.  
  
    > [!NOTE]  
    >  Список "владелец" недоступен в этом диалоговом окне, так как драйвер не поддерживает владельцев. Список баз данных недоступен, так как драйвер не поддерживает несколько баз данных в источнике данных.  
  
5.  Выберите поля для запроса, перетащив их из таблицы в нижнюю половину конструктора.  
  
6.  Закройте Microsoft Query. Выбранные данные импортируются в электронную таблицу Microsoft Excel.
