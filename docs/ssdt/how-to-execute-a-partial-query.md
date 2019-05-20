---
title: Руководство. Выполнение частичного запроса | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 0dff2087286035b078f59ac1673a733fb3cc8358
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65090178"
---
# <a name="how-to-execute-a-partial-query"></a>Руководство. выполнить частичный запрос
Редактор Transact\-SQL позволяет выделять определенный фрагмент скрипта и выполнять его как отдельный запрос. Это упрощает отладку фрагментов сложных запросов.  
  
> [!WARNING]  
> В следующих процедурах используются сущности, которые созданы в рамках процедур, описанных в руководствах по [разработке подключенной базы данных](../ssdt/connected-database-development.md) и [автономной разработке базы данных с учетом проекта](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-partially-execute-a-query"></a>Частичное выполнение запроса  
  
1.  В **обозревателе объектов SQL Server** дважды щелкните представление **PerishableFruits** в разделе **Представления**, чтобы открыть его в редакторе Transact\-SQL.  
  
2.  Выделите сегмент `SELECT p.Id, p.Name FROM dbo.Product p` в коде, щелкните правой кнопкой мыши и выберите **Выполнить запрос**.  
  
3.  Обратите внимание, что все строки с указанными полями в таблице `Products` возвращаются в области **Результаты**.  
  
