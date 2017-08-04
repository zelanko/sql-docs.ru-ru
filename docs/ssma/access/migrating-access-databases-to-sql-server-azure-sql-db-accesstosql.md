---
title: "Перенос базы данных Access в SQL Server — база данных Azure SQL | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- instructions, migration
- migrating databases, overview
- overview, migration process
- procedure, migration
- recommended migration process
ms.assetid: 76a3abcf-2998-4712-9490-fe8d872c89ca
caps.latest.revision: 23
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6d3c44ed3c73edae1b2b8d9cd244a2530c5748cf
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-access-databases-to-sql-server---azure-sql-db-accesstosql"></a>Миграция баз данных Access в SQL Server — базы данных Azure SQL (AccessToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) — это комплексный среда, которая поможет вам быстро перенести базы данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Доступ можно просмотреть с помощью SSMA, и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure объектов базы данных, оценить для миграции базы данных Access, преобразования объектов базы данных Access, загрузить их в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, а затем перенести данные.  
  
## <a name="recommended-migration-process"></a>Рекомендуется использовать процесс миграции  
Для успешного переноса объектов и данных с доступом к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Создание нового проекта SSMA](http://msdn.microsoft.com/en-us/f2d1f0b0-5394-4adb-b3f3-abd71eb68ca7). После создания проекта вы можете [задать параметры проекта](http://msdn.microsoft.com/en-us/0a7304df-2f35-4453-96ef-7ac83dea1167). К ним относятся параметры преобразования, вариантов миграции и сопоставления типов данных.  
  
2.  [Добавление базы данных Access](http://msdn.microsoft.com/en-us/e944c740-4c8a-4bc1-b0ed-be57bc06dced) в проект.  
  
    Можно добавить отдельные файлы, или можно добавить файлы, расположенные на компьютере или в сети.  
  
3.  [Подключение к целевому экземпляру SQL Server](http://msdn.microsoft.com/en-us/f84cf007-ddf1-4396-a07c-3e0729abc769) или [подключение к целевому экземпляру SQL Azure](http://msdn.microsoft.com/en-us/1ba0d113-dc05-4431-8689-e14a8821bafd).  
  
    Можно подключиться к SQL Server или SQL Azure.  
  
4.  Чтобы настроить сопоставление одного или нескольких баз данных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схем SQL Azure [сопоставление исходной и целевой баз данных](http://msdn.microsoft.com/en-us/69bee937-7b2c-49ee-8866-7518c683fad4).  
  
5.  При необходимости можно [Создание отчета оценки](http://msdn.microsoft.com/en-us/8b9e23d6-da62-437a-8c05-8ad2628b9441)для определения объектов базы данных Access может быть успешно преобразован в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
6.  [Преобразование объектов базы данных Access](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или определения объектов SQL Azure.  
  
7.  [Загрузка объектов преобразованную базу данных в SQL Server](http://msdn.microsoft.com/en-us/4e854eee-b10c-4f0b-9d9e-d92416e6f2ba).  
  
    Вы можете либо нагрузки объекты базы данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure с помощью SSMA, или можно сохранить [!INCLUDE[tsql](../../includes/tsql_md.md)] сценариев.  
  
8.  [Перенос данных Access в SQL Server](http://msdn.microsoft.com/en-us/f3b18af7-1af0-499d-a00d-a0af94895625).  
  
    > [!NOTE]  
    > Преобразование, загрузка и перенос схемы и данные за один шаг. Чтобы выполнить миграцию одним щелчком, нажмите кнопку **преобразовать, загрузить и перенести** кнопки.  
  
9. Если необходимо, чтобы приложения доступа могут использовать данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, используйте [связь таблицы Access с таблицами SQL Server](http://msdn.microsoft.com/en-us/82374ad2-7737-4164-a489-13261ba393d4).  
  
Также можно использовать мастер миграции поможет вам этот процесс. Дополнительные сведения см. в разделе [мастер миграции](http://msdn.microsoft.com/en-us/5bab5914-b2ae-4795-8cf5-83e42d64bef2).  
  
## <a name="see-also"></a>См. также:  
[Приступая к работе с SQL Server Migration Assistant для Access](http://msdn.microsoft.com/en-us/462a731f-08f1-44e1-9eeb-4deac6d2f6c5)  
[Подготовка к миграции базы данных Access](http://msdn.microsoft.com/en-us/9b80a9e0-08e7-4b4d-b5ec-cc998d3f5114)  
  

