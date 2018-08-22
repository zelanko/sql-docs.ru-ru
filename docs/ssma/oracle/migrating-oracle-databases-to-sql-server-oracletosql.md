---
title: Переход с Oracle баз данных в SQL Server (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 04/22/2018
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1d196dd6-4322-4c98-bb72-602c57d96134
caps.latest.revision: 9
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 05cdf94aaac3c3b5401681edb996ed740fbc94a6
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40396011"
---
# <a name="migrating-oracle-databases-to-sql-server-oracletosql"></a>Миграция баз данных Oracle в SQL Server (OracleToSQL)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant (SSMA) для Oracle — это комплексное среда, которая поможет вам быстро перенос баз данных Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], база данных SQL Azure или хранилище данных SQL Azure. С помощью SSMA для Oracle, можно просмотреть объекты базы данных и данных, оценка баз данных для миграции, миграция объектов базы данных для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], база данных SQL Azure или хранилище данных SQL Azure, и затем перенести данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], база данных SQL Azure, или данных SQL Azure Хранилище данных. Обратите внимание на то, не может выполнить миграцию схемы SYS и системе Oracle.
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Для успешного переноса объектов и данных из баз данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], база данных SQL Azure или хранилище данных SQL Azure, воспользуйтесь следующей процедурой:
  
1.  [Создание нового проекта SSMA](working-with-ssma-projects-oracletosql.md).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Сведения о параметрах проекта см. в разделе [Настройка параметров проекта &#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md). Сведения о том, как настроить сопоставления типов данных, см. в разделе [сопоставление Oracle и типы данных SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md).  
  
2.  [Подключиться к серверу базы данных Oracle](connecting-to-oracle-database-oracletosql.md).  
  
3.  [Подключитесь к экземпляру SQL Server,](connecting-to-sql-server-oracletosql.md).  
  
4.  [Сопоставление схем базы данных Oracle и схем баз данных SQL Server](mapping-oracle-schemas-to-sql-server-schemas-oracletosql.md).  
  
5.  При необходимости [создание отчетов с оценкой](assessing-oracle-schemas-for-conversion-oracletosql.md) обращаться к таким объектам базы данных для преобразования и оценить время преобразования.  
  
6.  [Преобразование схем баз данных Oracle в SQL Server схемы](converting-oracle-schemas-oracletosql.md).  
  
7.  [Загрузка преобразованных объектов в SQL Server](loading-converted-database-objects-into-sql-server-oracletosql.md).  
  
    Это можно сделать одним из следующих способов:  
  
    -   Сохраните сценарий и запустите его [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
    -   Синхронизируйте объекты базы данных.  
  
8.  [Перенос данных в SQL Server](migrating-oracle-data-into-sql-server-oracletosql.md).  
  
9. При необходимости обновите приложений баз данных.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-oracletosql.md)  
[Начало работы с SSMA для Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/getting-started-with-ssma-for-oracle-oracletosql.md)  
  
