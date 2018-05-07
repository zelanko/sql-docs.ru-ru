---
title: Запросы и обновления данных Visual FoxPro из Microsoft Access | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- querying Visual FoxPro data [ODBC]
- FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], Access
- Visual FoxPro ODBC driver [ODBC], Access
- Visual FoxPro data [ODBC], querying and updating
- updating Visual FoxPro data [ODBC]
ms.assetid: 2d314e78-9edf-44b2-bd8b-96784236bcbe
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6704fb70b7c8764e0299c7334aa384410c45a0a7
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
