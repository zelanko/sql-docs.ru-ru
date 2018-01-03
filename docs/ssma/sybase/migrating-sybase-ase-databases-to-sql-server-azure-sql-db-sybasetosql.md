---
title: "Миграция баз данных Sybase ASE для SQL Server — база данных Azure SQL | Документы Microsoft"
ms.custom: 
ms.date: 11/30/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-sybase
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
caps.latest.revision: "7"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c72fb7a884a7cf87f50327a2e653493cdc3522f3
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>Миграция баз данных SAP ASE для SQL Server — база данных SQL Azure (SybaseToSQL)
SQL Server Migration Assistant (SSMA) для SAP адаптивной Server Enterprise (ASE) — это комплексный среда, которая поможет вам быстро перенести базы данных SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure. С помощью SSMA для SAP ASE, можно просмотреть объекты базы данных и данных, оценить баз данных для миграции, миграция объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure, а затем перенесите данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure.  
  
## <a name="recommended-migration-process"></a>Процесс миграции рекомендуется  
Для успешного переноса объектов и данных из базы данных SAP ASE [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Создание нового проекта SSMA](http://msdn.microsoft.com/en-us/11091d95-c488-48c3-891a-743cac94ac93).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Сведения о параметрах проекта см. в разделе [задание параметров проекта &#40; SybaseToSQL &#41; ](../../ssma/sybase/setting-project-options-sybasetosql.md). Сведения о настройке сопоставления типов данных см. в разделе [сопоставление Sybase ASE и типов данных SQL Server &#40; SybaseToSQL &#41; ](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Подключиться к серверу базы данных SAP ASE](http://msdn.microsoft.com/en-us/a45a2330-9175-4c9e-af38-ef920e350614).  
  
3.  [Подключение к экземпляру SQL Server](http://msdn.microsoft.com/en-us/dd368a1a-45b0-40e9-b4d3-5cdb48c26606) или [подключиться к экземпляру базы данных SQL Azure](http://msdn.microsoft.com/en-us/9e77e4b0-40c0-455c-8431-ca5d43849aa7).  
  
4.  [Сопоставление схем SAP ASE базы данных SQL Server и базы данных SQL Azure схемы базы данных](http://msdn.microsoft.com/en-us/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  При необходимости [создавать отчеты для оценки](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c) для оценки для преобразования объектов базы данных и оценить время преобразования.  
  
6.  [Преобразование схем баз данных SAP ASE в SQL Server или схемы базы данных SQL Azure](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Загрузка объектов преобразованную базу данных в SQL Server и базы данных SQL Azure](http://msdn.microsoft.com/en-us/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Либо сохраните скрипт и запустите его в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure или синхронизировать объекты базы данных.  
  
8.  [Перенос данных в SQL Server и базы данных SQL Azure](http://msdn.microsoft.com/en-us/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. При необходимости обновите базы данных приложения.  
  
## <a name="see-also"></a>См. также раздел  
[Установка SSMA для SAP ASE &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Начало работы с SSMA для SAP ASE &#40; SybaseToSQL &#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
