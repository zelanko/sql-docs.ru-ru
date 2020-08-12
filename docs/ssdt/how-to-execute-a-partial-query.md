---
title: выполнить частичный запрос
description: Узнайте, как отлаживать разделы сложных запросов. Используйте редактор Transact-SQL для выделения определенного фрагмента скрипта и выполнения его как отдельного запроса.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: f9aaa7712726b37d03c7d7de0994bb8abe01a7d9
ms.sourcegitcommit: b860fe41b873977649dca8c1fd5619f294c37a58
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2020
ms.locfileid: "85518804"
---
# <a name="how-to-execute-a-partial-query"></a>Руководство. выполнить частичный запрос

Редактор Transact\-SQL позволяет выделять определенный фрагмент скрипта и выполнять его как отдельный запрос. Это упрощает отладку фрагментов сложных запросов.  
  
> [!WARNING]  
> В следующих процедурах используются сущности, которые созданы в рамках процедур, описанных в руководствах по [разработке подключенной базы данных](../ssdt/connected-database-development.md) и [автономной разработке базы данных с учетом проекта](../ssdt/project-oriented-offline-database-development.md).  
  
## <a name="to-partially-execute-a-query"></a>Частичное выполнение запроса  
  
1. В **обозревателе объектов SQL Server** дважды щелкните представление **PerishableFruits** в разделе **Представления**, чтобы открыть его в редакторе Transact\-SQL.  
  
2. Выделите сегмент `SELECT p.Id, p.Name FROM dbo.Product p` в коде, щелкните правой кнопкой мыши и выберите **Выполнить запрос**.  
  
3. Обратите внимание, что все строки с указанными полями в таблице `Products` возвращаются в области **Результаты**.