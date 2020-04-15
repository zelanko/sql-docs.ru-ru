---
title: Запрос и обновление визуальных данных FoxPro из Microsoft Access Документы Майкрософт
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292874"
---
# <a name="querying-and-updating-visual-foxpro-data-from-microsoft-access"></a>Запрос и обновление данных Visual FoxPro из Microsoft Access
Вы можете задавить запрос и обновить данные, хранящиеся в базе данных Visual FoxPro из базы данных Microsoft Access, используя опцию Link Table.  
  
### <a name="to-link-a-visual-foxpro-database-to-a-microsoft-access-database"></a>Связать базу данных Visual FoxPro с базой данных Microsoft Access  
  
1.  Откройте базу данных Microsoft Access.  
  
2.  Со вкладки Таблицы щелкните Новый.  
  
3.  В диалоговом поле New Table выберите таблицу ссылок и нажмите OK.  
  
4.  В поле Link Dialog выберите базу данных ODBC в списке файлов типа.  
  
5.  В диалоговом окне источников данных s'L выберите источник данных, который подключается к данным Visual FoxPro, которые вы хотите задать и щелкнуть ОК.  
  
6.  В диалоговом окне таблицы ссылок выберите таблицы, которые вы хотите задать запрос, обновить и нажать OK. Связанные таблицы Visual FoxPro отображаются во вкладке Таблицы базы данных Microsoft Access.  
  
 Теперь вы можете использовать Microsoft Access для запроса и обновления данных в связанных таблицах Visual FoxPro. Изменения, внесенные в связанные данные, отправляются обратно в источник данных Visual FoxPro.  
  
 Если вы не хотите, чтобы изменения, внесенные в Microsoft Access, повлияли на данные, содеянемые в источнике данных Visual FoxPro, [см. Импорт визуальных данных FoxPro в Microsoft Access.](../../odbc/microsoft/importing-visual-foxpro-data-into-microsoft-access.md)
