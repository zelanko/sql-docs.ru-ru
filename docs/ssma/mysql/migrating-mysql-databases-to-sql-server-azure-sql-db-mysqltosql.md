---
title: Перенос баз данных MySQL в SQL Server — база данных Azure SQL | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: badfb3afaeba92f366e62fce8dfcb3ec7dae9f29
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "63311958"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-db-mysqltosql"></a>Миграция баз данных MySQL в SQL Server — база данных Azure SQL (MySQLToSql)
SQL Server Migration Assistant (SSMA) для MySQL — это комплексное среда, которая поможет вам быстро перенести базы данных MySQL в SQL Server или SQL Azure. С помощью SSMA для MySQL, можно просмотреть объекты базы данных и данных, оценить баз данных для миграции, миграция объектов базы данных в SQL Server или SQL Azure и затем перенести данные в SQL Server или SQL Azure.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Для успешного переноса объектов и данных из базы данных MySQL в SQL Server или SQL Azure, воспользуйтесь следующей процедурой:  
  
1.  [Работа с проектами SSMA &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    После создания проекта можно задать преобразование проекта, миграции и параметры сопоставления типов. Дополнительные сведения о параметрах проекта см. в разделе [Настройка параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md). Сведения о том, как настроить сопоставления типов данных, см. в разделе [сопоставление MySQL и типы данных SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [Подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [Сопоставление баз данных MySQL со схемами SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Подключение к базе данных Azure SQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  При необходимости [оценка баз данных MySQL для преобразования &#40;MySQLToSQL&#41; ](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md) обращаться к таким объектам базы данных для преобразования и оценить время преобразования.  
  
7.  [Преобразование баз данных MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Синхронизация](loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
9. Это можно сделать одним из следующих способов:  
  
    -   Сохраните сценарий и запустите его на SQL Server или SQL Azure.  
  
    -   Синхронизируйте объекты базы данных.  
  
10. [Миграция данных MySQL в SQL Server — база данных Azure SQL &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. При необходимости обновите приложений баз данных.  
  
> [!NOTE]  
> Нельзя перенести схемы Information_schema и MySQL.  
  
## <a name="see-also"></a>См. также  
[Установка SSMA для MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[Начало работы с SSMA для MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
