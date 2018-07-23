---
title: Практическое руководство. Выполнение частичного запроса | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af04ab37-6cbb-4185-9382-e5922fa5b1df
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 84598f015ae1c70276f5ed546674aaa4b43e4bc3
ms.sourcegitcommit: 2f07d285824a8982c279f3816b220e61a2d91b06
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37094716"
---
# <a name="how-to-execute-a-partial-query"></a>Как выполнить частичный запрос
Редактор Transact\-SQL позволяет выделять определенный фрагмент скрипта и выполнять его как отдельный запрос. Это упрощает отладку фрагментов сложных запросов.  
  
> [!WARNING]  
> В следующих процедурах используются сущности, которые созданы в рамках процедур, описанных в руководствах по [разработке подключенной базы данных](../ssdt/connected-database-development.md) и [автономной разработке базы данных с учетом проекта](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-partially-execute-a-query"></a>Частичное выполнение запроса  
  
1.  В **обозревателе объектов SQL Server** дважды щелкните представление **PerishableFruits** в разделе **Представления**, чтобы открыть его в редакторе Transact\-SQL.  
  
2.  Выделите сегмент `SELECT p.Id, p.Name FROM dbo.Product p` в коде, щелкните правой кнопкой мыши и выберите **Выполнить запрос**.  
  
3.  Обратите внимание, что все строки с указанными полями в таблице `Products` возвращаются в области **Результаты**.  
  
