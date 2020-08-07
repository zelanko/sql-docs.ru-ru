---
title: Перенос баз данных Access в SQL Server в базе данных SQL Azure | Документация Майкрософт
description: Используйте этот рекомендуемый процесс для переноса баз данных Access в SQL Server или базу данных SQL Azure с помощью Помощник по миграции SQL Server (SSMA).
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
ms.openlocfilehash: d35f359186fca7d862ee8da8f4c4932d849c421b
ms.sourcegitcommit: 777704aefa7e574f4b7d62ad2a4c1b10ca1731ff
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87823559"
---
# <a name="migrating-access-databases-to-sql-server---azure-sql-database-accesstosql"></a>Миграция баз данных Access в SQL Server — база данных SQL Azure (Акцесстоскл)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Помощник по миграции (SSMA) — это средство, предоставляющее исчерпывающую среду, помогающую быстро перенести базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. С помощью SSMA можно просматривать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объекты базы данных Access и SQL Azure, оценивать базу данных Access для миграции, преобразовывать объекты базы данных Access, загружать их в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, а затем переносить данные.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Чтобы успешно перенести объекты и данные из доступа в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, используйте следующую процедуру.  
  
1.  [Создайте новый проект SSMA](creating-and-managing-projects-accesstosql.md). После создания проекта можно [задать параметры проекта](setting-conversion-and-migration-options-accesstosql.md), включая параметры преобразования, параметры миграции и сопоставления типов данных.  
  
2.  [Добавьте файлы базы данных Access](adding-and-removing-access-database-files-accesstosql.md) в проект.  
  
    Можно добавить отдельные файлы, включая файлы, найденные на компьютере или в сети.  
  
3.  [Подключитесь к целевому экземпляру SQL Server](connecting-to-sql-server-accesstosql.md) или [подключитесь к целевому экземпляру SQL Azure](connecting-to-azure-sql-db-accesstosql.md).  
  
    Можно подключиться либо к SQL Server, либо к SQL Azure.  
  
4.  Чтобы настроить сопоставление одной или нескольких баз данных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схем SQL Azure, [сопоставьте исходную и целевую базы данных](mapping-source-and-target-databases-accesstosql.md).  
  
5.  При необходимости можно [создать отчет об оценке](assessing-access-database-objects-for-conversion-accesstosql.md) , чтобы определить, можно ли успешно преобразовать объекты базы данных Access в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
6.  [Преобразуйте объекты базы данных Access](converting-access-database-objects-accesstosql.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определения объектов или SQL Azure.  
  
7.  [Загрузите преобразованные объекты базы данных в SQL Server](loading-converted-database-objects-into-sql-server-accesstosql.md).  
  
    Можно загрузить либо объекты базы данных, либо [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SQL Azure с помощью SSMA, либо сохранить [!INCLUDE[tsql](../../includes/tsql-md.md)] скрипты.  
  
8.  [Перенос данных доступа в SQL Server](migrating-access-data-into-sql-server-azure-sql-db-accesstosql.md).  
  
    > [!NOTE]  
    > Вы можете преобразовать, загрузить и перенести схемы и данные за один шаг. Чтобы выполнить миграцию одним щелчком, нажмите кнопку **преобразовать, загрузить и выполнить миграцию** .  
  
9. Если вы хотите, чтобы приложения Access использовали данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, используйте [Связывание таблиц доступа с SQL Server таблицами](linking-access-applications-to-sql-server-azure-sql-db-accesstosql.md).  
  
Вы также можете использовать мастер миграции для пошагового выполнения этого процесса. Дополнительные сведения см. в разделе [Мастер миграции](migration-wizard-accesstosql.md).  
  
## <a name="see-also"></a>См. также  
[начало работы с Помощник по миграции SQL Server для доступа](getting-started-with-sql-server-migration-assistant-for-access-accesstosql.md)  
[Подготовка баз данных Access к миграции](preparing-access-databases-for-migration-accesstosql.md)
