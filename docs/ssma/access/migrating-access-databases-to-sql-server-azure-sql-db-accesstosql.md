---
title: Перенос баз данных Access в SQL Server — база данных Azure SQL | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 08/15/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- instructions, migration
- migrating databases, overview
- overview, migration process
- procedure, migration
- recommended migration process
ms.assetid: 76a3abcf-2998-4712-9490-fe8d872c89ca
author: Shamikg
ms.author: Shamikg
manager: murato
ms.openlocfilehash: 959af9bcb1879dc19d2bfb99253b4c40d637fd1e
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68260237"
---
# <a name="migrating-access-databases-to-sql-server---azure-sql-db-accesstosql"></a>Миграция баз данных Access в SQL Server — база данных SQL Azure (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) — это средство, которое предоставляет комплексную среду, которая поможет вам быстро перенести базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. С помощью SSMA, можно проверить доступ и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure объектов базы данных, оценка базы данных Access для миграции, преобразование объектов базы данных Access, загрузить их в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, а затем перенести данные.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Для успешного переноса объектов и данных с доступом к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Создание нового проекта SSMA](creating-and-managing-projects-accesstosql.md). После создания проекта, вы можете [задать параметры проекта](setting-conversion-and-migration-options-accesstosql.md), включая параметры преобразования, вариантов миграции и сопоставления типов данных.  
  
2.  [Добавление базы данных Access](adding-and-removing-access-database-files-accesstosql.md) в проект.  
  
    Можно добавить отдельные файлы, включая файлы, расположенные на компьютере или в сети.  
  
3.  [Подключение к целевому экземпляру SQL Server](connecting-to-sql-server-accesstosql.md) или [подключение к целевому экземпляру SQL Azure](connecting-to-azure-sql-db-accesstosql.md).  
  
    Вы можете подключиться к SQL Server или SQL Azure.  
  
4.  Чтобы настроить сопоставление между одной или нескольких баз данных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схем SQL Azure, [сопоставление исходной и целевой баз данных](mapping-source-and-target-databases-accesstosql.md).  
  
5.  При необходимости можно [создать отчет об оценке](assessing-access-database-objects-for-conversion-accesstosql.md) для определения объектов базы данных Access может быть успешно преобразован в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
6.  [Преобразование объектов базы данных Access](converting-access-database-objects-accesstosql.md) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или определения объектов SQL Azure.  
  
7.  [Загрузка преобразованных объектов в SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
    Вы можете загрузить объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure с помощью SSMA, или можно сохранить [!INCLUDE[tsql](../../includes/tsql-md.md)] сценариев.  
  
8.  [Перенос данных Access в SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
    > [!NOTE]  
    > Можно преобразовать, загрузить и перенос схемы и данных за один шаг. Чтобы выполнить миграцию одним щелчком, нажмите кнопку **преобразование, загрузка и перенос** кнопки.  
  
9. Если необходимо, чтобы приложения доступа могут использовать данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, используйте [свяжите таблицы Access в таблицы SQL Server](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
Можно также использовать мастер миграции описывают этот процесс. Дополнительные сведения см. в разделе [мастер миграции](migration-wizard-accesstosql.md).  
  
## <a name="see-also"></a>См. также  
[Приступая к работе с SQL Server Migration Assistant для Access](getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Подготовка к миграции базы данных Access](preparing-access-databases-for-migration-accesstosql.md)
