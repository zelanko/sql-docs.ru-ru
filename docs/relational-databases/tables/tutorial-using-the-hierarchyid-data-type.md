---
title: Руководство. Использование типа данных hierarchyid | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: quickstart
helpviewer_keywords:
- tutorials [hierarchyid]
- hierarchyid [Database Engine], tutorial
ms.assetid: 5a7f7cfd-7faf-439f-8085-8fd6bf7db355
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ae451d86f2490765f3871deca925f4b6348e2304
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68140415"
---
# <a name="tutorial-using-the-hierarchyid-data-type"></a>Руководство. Использование типа данных hierarchyid
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]
Этот учебник предназначен для пользователей, имеющих опыт работы с [!INCLUDE[tsql](../../includes/tsql-md.md)], но незнакомых с типом данных **hierarchyid** .  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
Учебник разделен на два занятия.  
  
[Занятие 1. Преобразование таблицы в иерархическую структуру](../../relational-databases/tables/lesson-1-converting-a-table-to-a-hierarchical-structure.md)  
На этом занятии возьмем существующую таблицу сотрудников, структурированную по иерархии "родители-потомки", и переместим данные в новую таблицу, представляющую иерархию с помощью типа данных **hierarchyid** . Для этого занятия требуется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
[Занятие 2. Создание данных и управление ими в иерархической таблице](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
На этом занятии создается таблица с помощью типа данных **hierarchyid** для представления структуры иерархии. Затем создаются запросы и производится управление данными с помощью иерархических методов.  
  
## <a name="requirements"></a>Требования  
В системе должно быть установлено следующее.  
  
-   Любой выпуск [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней версии.  
  
-   Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express.  
  
-   Internet Explorer 6 или более поздней версии.  
  
## <a name="see-also"></a>См. также:  
[Учебник. Начало работы с ядром СУБД](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
[Учебник. Составление инструкций Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
[Справочник по методам типа данных hierarchyid](https://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)  
  
  
  
