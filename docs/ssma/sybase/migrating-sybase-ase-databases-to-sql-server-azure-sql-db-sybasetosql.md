---
title: "Миграция баз данных Sybase ASE для SQL Server — база данных Azure SQL | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 63dc9188d93def41a5116386f93bf29e3b744e8e
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="migrating-sybase-ase-databases-to-sql-server---azure-sql-db-sybasetosql"></a>Миграция баз данных Sybase ASE в SQL Server — базы данных Azure SQL (SybaseToSQL)
SQL Server Migration Assistant (SSMA) для Sybase — это комплексный среда, которая поможет вам быстро перенести базы данных Sybase адаптивной Server Enterprise (ASE) для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. С помощью SSMA для СУБД Sybase, можно просмотреть объекты базы данных и данных, оценить баз данных для миграции, миграция объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базе данных SQL Azure, а затем перенесите данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure.  
  
## <a name="recommended-migration-process"></a>Рекомендуется использовать процесс миграции  
Для успешного переноса объектов и данных из базы данных ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или база данных SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Создание нового проекта SSMA](http://msdn.microsoft.com/en-us/11091d95-c488-48c3-891a-743cac94ac93).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Сведения о параметрах проекта см. в разделе [задание параметров проекта &#40; SybaseToSQL &#41; ](../../ssma/sybase/setting-project-options-sybasetosql.md). Сведения о настройке сопоставления типов данных см. в разделе [сопоставление Sybase ASE и типов данных SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Подключиться к серверу базы данных Sybase ASE](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614).  
  
3.  [Подключение к экземпляру SQL Server](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) или [подключиться к экземпляру базы данных SQL Azure](http://msdn.microsoft.com/en-us/9e77e4b0-40c0-455c-8431-ca5d43849aa7).  
  
4.  [Сопоставление схем ASE базы данных SQL Server и базу данных SQL Azure схемы базы данных](http://msdn.microsoft.com/en-us/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  При необходимости [создавать отчеты для оценки](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c) для оценки для преобразования объектов базы данных и оценить время преобразования.  
  
6.  [Преобразование схем баз данных Sybase ASE в SQL Server или схемы базы данных SQL Azure](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Загрузка объектов преобразованную базу данных в SQL Server и базу данных SQL Azure](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Можно либо сохранить сценарий и запустите его в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure, или можно синхронизировать объекты базы данных.  
  
8.  [Перенос данных в SQL Server и базу данных SQL Azure](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. При необходимости обновите базы данных приложения.  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Начало работы с SSMA для Sybase &#40; SybaseToSQL &#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  

