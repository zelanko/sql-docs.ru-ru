---
description: Доступ к источнику данных Visual FoxPro из Microsoft Excel
title: Доступ к источнику данных Visual FoxPro из Microsoft Excel | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- FoxPro ODBC driver [ODBC], Excel
- Visual FoxPro data [ODBC], Excel
- Visual FoxPro data [ODBC], accessing
- Visual FoxPro ODBC driver [ODBC], Excel
ms.assetid: 2c143020-0403-4592-80e0-84229f3d40be
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ce4e3bf96a41918fff392117a2fbbd1b9eb47f2
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487577"
---
# <a name="accessing-a-visual-foxpro-data-source-from-microsoft-excel"></a>Доступ к источнику данных Visual FoxPro из Microsoft Excel
Если установлен Microsoft Query, можно создать источник данных в Microsoft Excel, который подключается к данным Visual FoxPro.  
  
### <a name="to-access-visual-foxpro-data-from-microsoft-excel"></a>Доступ к данным Visual FoxPro из Microsoft Excel  
  
1.  Откройте электронную таблицу Microsoft Excel.  
  
2.  В меню Данные выберите получить внешние данные. Откроется Microsoft Query.  
  
3.  В диалоговом окне Выбор источника данных нажмите кнопку другие.  
  
4.  В диалоговом окне Источники данных ODBC нажмите кнопку Создать.  
  
5.  В диалоговом окне Добавление источника данных выберите драйвер Microsoft Visual FoxPro в списке установленные драйверы ODBC и нажмите кнопку ОК.  
  
6.  В [диалоговом окне Установка ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)введите имя источника данных, выберите тип базы данных, введите путь к базе данных или каталогу и нажмите кнопку ОК.  
  
     Новое имя источника данных отображается в текстовом поле введите источник данных диалогового окна Источники данных ODBC.  
  
7.  Щелкните ОК.  
  
     Новое имя источника данных выбирается в текстовом поле Доступные источники данных диалогового окна Выбор источника данных.  
  
8.  Нажмите кнопку Использовать.  
  
 Теперь можно добавлять таблицы в открытый запрос. Дополнительные сведения о построении запроса см. в разделе [Импорт данных в Microsoft Excel из базы данных Visual FoxPro](../../odbc/microsoft/importing-data-into-microsoft-excel-from-a-visual-foxpro-database.md).
