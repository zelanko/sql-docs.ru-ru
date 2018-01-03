---
title: "Миграция Oracle баз данных SQL Server (OracleToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssma-oracle
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: "9"
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Active
ms.openlocfilehash: c3b6bc1f359cd54c1380fbe193fb007e1e337a3d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Миграция баз данных Oracle в SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]Migration Assistant (SSMA) для Oracle — это комплексный среда, которая поможет вам быстро перенести базы данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. С помощью SSMA для Oracle, можно просмотреть объекты базы данных и данных, оценить баз данных для миграции, миграция объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базе данных SQL Azure, а затем перенесите данные [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базу данных SQL Azure. Обратите внимание, невозможно выполнить миграцию схемы SYS и системе Oracle.  
  
## <a name="recommended-migration-process"></a>Рекомендуется использовать процесс миграции  
Для успешного переноса объектов и данных из баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или база данных SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Создание нового проекта SSMA](http://msdn.microsoft.com/en-us/ee5d94c0-c7a6-4779-bd32-729bdaf61e1b).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Сведения о параметрах проекта см. в разделе [задание параметров проекта &#40; OracleToSQL &#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Сведения о том, как настроить сопоставления типов данных см. в разделе [сопоставление Oracle и типы данных SQL Server &#40; OracleToSQL &#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Подключиться к серверу базы данных Oracle](http://msdn.microsoft.com/en-us/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6).  
  
3.  [Подключитесь к экземпляру SQL Server](http://msdn.microsoft.com/en-us/1b2a8059-1829-4904-a82f-9c06de1e245f).  
  
4.  [Сопоставление схем базы данных Oracle для схемы базы данных SQL Server](http://msdn.microsoft.com/en-us/0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc).  
  
5.  При необходимости [создавать отчеты для оценки](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357) для оценки для преобразования объектов базы данных и оценить время преобразования.  
  
6.  [Преобразование схем баз данных Oracle в SQL Server схемы](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272).  
  
7.  [Загрузка объектов преобразованную базу данных в SQL Server](http://msdn.microsoft.com/en-us/a8ae33b2-1883-4785-922b-ea0e31c0b37a).  
  
    Это можно сделать одним из следующих способов:  
  
    -   Сохраните скрипт и запустите его в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)].  
  
    -   Синхронизируйте объекты базы данных.  
  
8.  [Перенос данных в SQL Server](http://msdn.microsoft.com/en-us/e23c5268-41ed-4e55-9fe7-a11376202a13).  
  
9. При необходимости обновить базу данных приложения.  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Начало работы с SSMA для Oracle &#40; OracleToSQL &#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
