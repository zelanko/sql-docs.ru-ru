---
title: Руководство. Использование типа данных hierarchyid | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.suite: sql
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- tutorials [hierarchyid]
- hierarchyid [Database Engine], tutorial
ms.assetid: 5a7f7cfd-7faf-439f-8085-8fd6bf7db355
caps.latest.revision: 14
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: c271e0400448b9493be5a4e5e91bebcc36fb7a31
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39550294"
---
# <a name="tutorial-using-the-hierarchyid-data-type"></a>Учебник. Использование типа данных hierarchyid
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
Этот учебник предназначен для пользователей, имеющих опыт работы с [!INCLUDE[tsql](../../includes/tsql-md.md)], но незнакомых с типом данных **hierarchyid** .  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
Учебник разделен на два занятия.  
  
[Занятие 1. Преобразование таблицы в иерархическую структуру](../../relational-databases/tables/lesson-1-converting-a-table-to-a-hierarchical-structure.md)  
На этом занятии возьмем существующую таблицу сотрудников, структурированную по иерархии "родители-потомки", и переместим данные в новую таблицу, представляющую иерархию с помощью типа данных **hierarchyid** . Для этого занятия требуется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
[Занятие 2. Создание данных и управление ими в иерархической таблице](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
На этом занятии создается таблица с помощью типа данных **hierarchyid** для представления структуры иерархии. Затем создаются запросы и производится управление данными с помощью иерархических методов.  
  
## <a name="requirements"></a>Требования  
В системе должно быть установлено следующее.  
  
-   Любой выпуск [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней версии.  
  
-   Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express.  
  
-   Internet Explorer 6 или более поздней версии.  
  
## <a name="see-also"></a>См. также:  
[Учебник. Приступая к работе с компонентом Database Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
[Учебник. Составление инструкций Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
[Справочник по методам типа данных hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)  
  
  
  
