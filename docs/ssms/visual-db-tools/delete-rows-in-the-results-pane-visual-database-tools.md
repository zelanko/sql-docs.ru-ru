---
title: Удаление строк на панели результатов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- View Designer, Results pane
- removing rows
- row removal [SQL Server], Visual Database Tools Results pane
- row deletions [SQL Server], Visual Database Tools Results pane
- Query Designer [SQL Server], Results pane
- deleting rows
- Results pane
ms.assetid: a1147905-fe4a-4fac-b576-a17622477e66
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d333704d285993e546d6b4e9d110abe5c5ad8b78
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="delete-rows-in-the-results-pane-visual-database-tools"></a>Удаление строк на панели «Результаты» (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Удалите строки на панели «Результаты» если нужно удалить записи в базе данных. Чтобы удалить все строки, можно использовать запрос «Delete». Дополнительные сведения см. в разделе [Создание запросов на удаление (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md). Если необходимо только удалить строки из панели «Результаты», измените критерии для запроса. Дополнительные сведения см. в разделе [Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md).  
  
### <a name="to-delete-a-row-or-rows"></a>Удаление строки или строк  
  
1.  Установите флажки слева от строки или строк, которые необходимо удалить, на панели «Результаты».  
  
2.  Нажмите клавишу DELETE.  
  
3.  В окне сообщения с требованием подтверждения нажмите кнопку **Да**.  
  
> [!CAUTION]  
> Строки, удаленные таким способом, окончательно удаляются из базы данных и не могут быть восстановлены в дальнейшем.  
  
> [!NOTE]  
> Если какие-либо из выбранных строк нельзя удалить из базы данных, ни одна из них не будет удалена, при этом выводится сообщение, указывающее, какие именно строки невозможно удалить.  
  
## <a name="see-also"></a>См. также:  
[Создание запросов на удаление (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-delete-queries-visual-database-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
  
