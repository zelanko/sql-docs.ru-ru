---
title: Импорт визуальных данных FoxPro в доступ к Microsoft (ru) Документы Майкрософт
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 90ac16bbdbaf7f4dd29e14e66cf5b9dc666057f4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302455"
---
# <a name="importing-visual-foxpro-data-into-microsoft-access"></a>Импорт данных Visual FoxPro в Microsoft Access
Вы можете импортировать данные, хранящиеся в базе данных Visual FoxPro, в базу данных Microsoft Access с помощью опции «Импорт».  
  
### <a name="to-import-visual-foxpro-data-into-a-microsoft-access-database"></a>Импорт визуальных данных FoxPro в базу данных Microsoft Access  
  
1.  Откройте базу данных Microsoft Access.  
  
2.  Из меню файла выберите Получить внешние данные, а затем импорт.  
  
3.  В поле диалога импорта выберите базы данных ODBC в списке файлов типов.  
  
4.  В диалоговом окне источников данных S'L выберите источник данных Visual FoxPro, который подключается к данным FoxPro, которые вы хотите задать и щелкнуть ОК.  
  
5.  В диалоговом окне объектов импорта выберите одну или несколько таблиц, которые вы хотите импортировать, и нажмите OK. Имена импортируемых таблиц Visual FoxPro отображаются во вкладке Таблицы базы данных Microsoft Access.  
  
 Теперь можно использовать Microsoft Access для управления данными в импортируемых таблицах Visual FoxPro. Импортируемые данные — это моментальный снимок данных, хранящихся в Visual FoxPro; изменения, внесенные в импортируемые данные, не отправляются обратно в источник данных Visual FoxPro.  
  
 Если вы хотите внести изменения в Microsoft Access для изменения данных в источнике данных Visual FoxPro, [см.](../../odbc/microsoft/querying-and-updating-visual-foxpro-data-from-microsoft-access.md)
