---
title: "Запросы и обновления данных Visual FoxPro из Microsoft Access | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d4faac1ac4f917557a0827a0ad434bf6d8f36cb
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Запросы и обновления данных Visual FoxPro из Microsoft Access
Можно запрашивать и обновлять данные, хранящиеся в базе данных Visual FoxPro из базы данных Microsoft Access с помощью параметра связанной таблицы.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Для связи с базой данных Microsoft Access базы данных Visual FoxPro  
  
1.  Откройте базу данных Microsoft Access.  
  
2.  На вкладке «таблицы» нажмите кнопку "Создать".  
  
3.  В диалоговом окне Создать таблицу выберите ссылку таблицы и нажмите кнопку ОК.  
  
4.  В диалоговом окне связи выберите базу данных ODBC в списке типов файлов.  
  
5.  В диалоговом окне SQL источников данных выберите источник данных, который подключается к данным Visual FoxPro, необходимые для запроса и нажмите кнопку ОК.  
  
6.  В диалоговом окне связь с таблицами выберите таблицы, которые вы хотите запросить обновление и нажмите кнопку ОК. Связанные таблицы Visual FoxPro, отображаются на вкладке таблицы базы данных Microsoft Access.  
  
 Теперь можно использовать Microsoft Access для запроса и обновления данных в связанных таблицах Visual FoxPro. Изменения, вносимые в связанные данные отправляются обратно в источник данных Visual FoxPro.  
  
 Если не хотите, чтобы изменения, внесенные в Microsoft Access, чтобы повлиять на данные в источнике данных Visual FoxPro см. в разделе [импорта Visual FoxPro данных в Microsoft Access](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md).
