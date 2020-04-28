---
title: Запрос и обновление данных Visual FoxPro из Microsoft Access | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f11b49ed099ba29d0e7e013af99a8ad96ca6825c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292874"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Запрос и обновление данных Visual FoxPro из Microsoft Access
Вы можете запрашивать и обновлять данные, хранящиеся в базе данных Visual FoxPro, из базы данных Microsoft Access с помощью параметра link Table.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Связывание базы данных Visual FoxPro с базой данных Microsoft Access  
  
1.  Откройте базу данных Microsoft Access.  
  
2.  На вкладке таблицы нажмите кнопку Создать.  
  
3.  В диалоговом окне Новая таблица выберите связать таблицу и нажмите кнопку ОК.  
  
4.  В диалоговом окне Ссылка выберите База данных ODBC в списке Тип файлов.  
  
5.  В диалоговом окне Источники данных SQL выберите источник данных, который подключается к данным Visual FoxPro, к которым требуется выполнить запрос, и нажмите кнопку ОК.  
  
6.  В диалоговом окне Связывание таблиц выберите таблицы, которые необходимо запрашивать и обновить, и нажмите кнопку ОК. Связанные таблицы Visual FoxPro отображаются на вкладке таблицы базы данных Microsoft Access.  
  
 Теперь можно использовать Microsoft Access для запроса и обновления данных в связанных таблицах Visual FoxPro. Изменения, вносимые в связанные данные, отправляются обратно в источник данных Visual FoxPro.  
  
 Если вы не хотите, чтобы изменения, вносимые в Microsoft Access, влияли на данные в источнике данных Visual FoxPro, см. статью [Импорт данных Visual FoxPro в Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
