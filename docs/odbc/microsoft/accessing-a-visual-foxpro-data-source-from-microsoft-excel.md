---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 575ba4abf9ed20ffbc0f2602a91bee9776e42b05
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63198195"
---
# <a name="accessing-a-visual-foxpro-data-source-from-microsoft-excel"></a>Доступ к источнику данных Visual FoxPro из Microsoft Excel
Если у вас установлен Microsoft Query, можно создать источник данных в Microsoft Excel, которая подключается к данным Visual FoxPro.  
  
### <a name="to-access-visual-foxpro-data-from-microsoft-excel"></a>Доступ к данным Visual FoxPro из Microsoft Excel  
  
1.  Откройте электронную таблицу Microsoft Excel.  
  
2.  В меню «Данные» выберите получение внешних данных. Откроется Microsoft Query.  
  
3.  В диалоговом окне Выбор источника данных выберите другой.  
  
4.  В диалоговом окне источников данных ODBC нажмите кнопку "Создать".  
  
5.  В диалоговом окне Добавить источник данных выберите Microsoft Visual FoxPro драйвер из списка установлены драйверы ODBC и нажмите кнопку ОК.  
  
6.  В [диалоговое окно настройки ODBC для Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md), введите имя источника данных, выберите тип базы данных, введите путь к базе данных или каталог и нажмите кнопку ОК.  
  
     Имя источника данных отображается в текстовом поле введите источник данных диалогового окна "Источники данных ODBC".  
  
7.  Нажмите кнопку «ОК».  
  
     Имя источника данных выбран в поле доступные источники данных в диалоговом окне Выбор источника данных.  
  
8.  Вариант.  
  
 Теперь можно добавить таблицы, чтобы открыть запрос. Дополнительные сведения о построении запроса, см. в разделе [импорта данных в Microsoft Excel из базы данных Visual FoxPro](../../odbc/microsoft/importing-data-into-microsoft-excel-from-a-visual-foxpro-database.md).
