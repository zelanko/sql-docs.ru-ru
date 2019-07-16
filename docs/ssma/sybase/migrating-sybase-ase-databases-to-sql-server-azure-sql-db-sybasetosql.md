---
title: Перенос баз данных Sybase ASE в SQL Server — база данных Azure SQL | Документация Майкрософт
ms.custom: ''
ms.date: 11/30/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: ed7952d4-8331-44d7-bccf-3440e17238b2
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c3735e03e3196f899ab33ca152364244e3331ac5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68028848"
---
# <a name="migrating-sap-ase-databases-to-sql-server---azure-sql-database-sybasetosql"></a>Миграция баз данных SAP ASE на SQL Server — база данных SQL Azure (SybaseToSQL)
SQL Server Migration Assistant (SSMA) для SAP Adaptive Server Enterprise (ASE) — это комплексное среда, которая поможет вам быстро перенос баз данных SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure. С помощью SSMA для SAP ASE, можно просмотреть объекты базы данных и данных, оценка баз данных для миграции, миграция объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure, а затем перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Для успешного переноса объектов и данных из баз данных SAP ASE для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Создание нового проекта SSMA](working-with-ssma-projects-sybasetosql.md).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Сведения о параметрах проекта см. в разделе [Настройка параметров проекта &#40;SybaseToSQL&#41;](../../ssma/sybase/setting-project-options-sybasetosql.md). Сведения о настройке сопоставления типов данных, см. в разделе [сопоставление Sybase ASE и типы данных SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/mapping-sybase-ase-and-sql-server-data-types-sybasetosql.md).  
  
2.  [Подключиться к серверу базы данных SAP ASE](connecting-to-sybase-ase-sybasetosql.md).  
  
3.  [Подключение к экземпляру SQL Server](connecting-to-sql-server-sybasetosql.md) или [подключиться к экземпляру базы данных SQL Azure](connecting-to-azure-sql-db-sybasetosql.md).  
  
4.  [Сопоставление схем базы данных SAP ASE и SQL Server / схемы баз данных базы данных SQL Azure](https://msdn.microsoft.com/2c927003-c49d-4fe1-8e3e-5b2899166268).  
  
5.  При необходимости [создание отчетов с оценкой](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md) обращаться к таким объектам базы данных для преобразования и оценить время преобразования.  
  
6.  [Преобразование схем баз данных SAP ASE в SQL Server / схемы базы данных SQL Azure](https://msdn.microsoft.com/509cb65d-2f54-427a-83d7-37919cc4e3e3).  
  
7.  [Загрузка преобразованных объектов в SQL Server и базы данных SQL Azure](https://msdn.microsoft.com/4c59256f-99a8-4351-9559-a455813dbd06).  
  
    Либо сохраните сценарий и запустите его [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure, или синхронизировать объекты базы данных.  
  
8.  [Перенос данных в SQL Server и базы данных SQL Azure](https://msdn.microsoft.com/54a39f5e-9250-4387-a3ae-eae47c799811).  
  
9. При необходимости обновите приложения базы данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
[Начало работы с SSMA для SAP ASE &#40;SybaseToSQL&#41;](../../ssma/sybase/getting-started-with-ssma-for-sybase-sybasetosql.md)  
  
