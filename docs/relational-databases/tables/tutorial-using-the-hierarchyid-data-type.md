---
description: Руководство по Использование типа данных hierarchyid
title: Руководство. Использование типа данных hierarchyid | Документация Майкрософт
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
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8aae425506ebc8a2a17aadb2fa9c2d4485fe8f85
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97426749"
---
# <a name="tutorial-using-the-hierarchyid-data-type"></a>Руководство по Использование типа данных hierarchyid
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]
Этот учебник предназначен для пользователей, имеющих опыт работы с [!INCLUDE[tsql](../../includes/tsql-md.md)], но незнакомых с типом данных **hierarchyid** .  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
Учебник разделен на два занятия.  
  
[Урок 1. Преобразование таблицы в иерархическую структуру](../../relational-databases/tables/lesson-1-converting-a-table-to-a-hierarchical-structure.md)  
На этом занятии возьмем существующую таблицу сотрудников, структурированную по иерархии "родители-потомки", и переместим данные в новую таблицу, представляющую иерархию с помощью типа данных **hierarchyid** . Для этого занятия требуется образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] .  
  
[Урок 2. Создание данных и управление ими в иерархической таблице](../../relational-databases/tables/lesson-2-creating-and-managing-data-in-a-hierarchical-table.md)  
На этом занятии создается таблица с помощью типа данных **hierarchyid** для представления структуры иерархии. Затем создаются запросы и производится управление данными с помощью иерархических методов.  
  
## <a name="requirements"></a>Требования  
В системе должно быть установлено следующее.  
  
-   Любой выпуск [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] или более поздней версии.  
  
-   Среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] Express.  
  
-   Internet Explorer 6 или более поздней версии.  
  
## <a name="see-also"></a>См. также  
[Руководство. Начало работы с ядром СУБД](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
[Руководство. Составление инструкций Transact-SQL](../../t-sql/tutorial-writing-transact-sql-statements.md)  
[Справочник по методам типа данных hierarchyid](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)  
[Иерархические данные (SQL Server)](../../relational-databases/hierarchical-data-sql-server.md)  
[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)  
  
  
