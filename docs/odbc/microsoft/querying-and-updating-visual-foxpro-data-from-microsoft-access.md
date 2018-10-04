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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1097e03c414d919a606ffd21ae50ffddf51173b7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732952"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Запрос и обновление данных Visual FoxPro из Microsoft Access
Можно запрашивать и обновлять данные, хранящиеся в базе данных Visual FoxPro из базы данных Microsoft Access с помощью параметра таблицы ссылок.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Чтобы связать базу данных Visual FoxPro в базу данных Microsoft Access  
  
1.  Откройте базу данных Microsoft Access.  
  
2.  На вкладке «таблицы» нажмите кнопку "Создать".  
  
3.  В диалоговом окне новой таблицы выберите таблицу ссылку и нажмите кнопку ОК.  
  
4.  В диалоговом окне связи выберите базу данных ODBC в списке типов файлов.  
  
5.  В диалоговом окне источников данных SQL выберите источник данных, который подключается к данным Visual FoxPro для запроса и нажмите кнопку ОК.  
  
6.  В диалоговом окне связи таблиц выберите таблицы, которые вы хотите запрашивать и обновлять и нажмите кнопку ОК. Связанные таблицы Visual FoxPro, отображаются на вкладке таблицы базы данных Microsoft Access.  
  
 Теперь можно использовать Microsoft Access для запроса и обновления данных в связанных таблицах Visual FoxPro. Изменения, вносимые в связанные данные отправляются обратно к источнику данных Visual FoxPro.  
  
 Если не хотите, чтобы изменения, внесенные в Microsoft Access, чтобы повлиять на данные в источнике данных Visual FoxPro, см. в разделе [импорта Visual FoxPro данных в Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
