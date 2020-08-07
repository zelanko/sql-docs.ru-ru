---
title: Перенос баз данных MySQL в SQL Server в базе данных SQL Azure | Документация Майкрософт
description: Используйте этот рекомендуемый процесс для переноса баз данных MySQL в SQL Server или базу данных SQL Azure с помощью Помощник по миграции SQL Server (SSMA).
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 8006f9a0-394d-4238-8dc5-44255134628b
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: c6f360e67621288e6c04381931a7c0df0de3e256
ms.sourcegitcommit: 21bedbae28840e2f96f5e8b08bcfc794f305c8bc
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2020
ms.locfileid: "87862361"
---
# <a name="migrating-mysql-databases-to-sql-server---azure-sql-database-mysqltosql"></a>Перенос баз данных MySQL в SQL Server в базе данных SQL Azure (MySQLToSql)
Помощник по миграции SQL Server (SSMA) для MySQL — это Комплексная среда, которая помогает быстро перенести базы данных MySQL в SQL Server или SQL Azure. С помощью SSMA для MySQL можно просматривать объекты и данные базы данных, оценивать базы данных для миграции, переносить объекты базы данных в SQL Server или SQL Azure, а затем переносить данные в SQL Server или SQL Azure.  
  
## <a name="recommended-migration-process"></a>Рекомендуемый процесс миграции  
Чтобы успешно перенести объекты и данные из баз данных MySQL в SQL Server или SQL Azure, используйте следующую процедуру.  
  
1.  [Работа с проектами SSMA &#40;MySQLToSQL&#41;](../../ssma/mysql/working-with-ssma-projects-mysqltosql.md).  
  
    После создания проекта можно задать параметры преобразования проекта, миграции и сопоставления типов. Дополнительные сведения о параметрах проекта см. в разделе [Установка параметров проекта &#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md). Сведения о настройке сопоставлений типов данных см. в разделе [Сопоставление типов данных MySQL и SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
2.  [Подключение к MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-mysql-mysqltosql.md)  
  
3.  [Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
4.  [Сопоставление баз данных MySQL с SQL Server схемами &#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
5.  [Подключение к базе данных SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
  
6.  При необходимости [оцените базы данных MySQL для преобразования &#40;MySQLToSQL&#41;](../../ssma/mysql/assessing-mysql-databases-for-conversion-mysqltosql.md) , чтобы оценить объекты базы данных для преобразования и оценить время преобразования.  
  
7.  [Преобразование баз данных MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
8.  [Синхронизация](loading-converted-database-objects-into-sql-server-mysqltosql.md)  
  
9. Это можно сделать одним из следующих способов:  
  
    -   Сохраните скрипт и запустите его на SQL Server или SQL Azure.  
  
    -   Синхронизируйте объекты базы данных.  
  
10. [Перенос данных MySQL в SQL Server базу данных SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/migrating-mysql-data-into-sql-server-azure-sql-db-mysqltosql.md)  
  
11. При необходимости обновите приложения базы данных.  
  
> [!NOTE]  
> Вы не можете перенести схемы Information_schema и MySQL.  
  
## <a name="see-also"></a>См. также:  
[Установка SSMA для MySQL &#40;MySqlToSql&#41;](../../ssma/mysql/installing-ssma-for-mysql-mysqltosql.md)  
[Начало работы с SSMA для MySQL &#40;MySQLToSQL&#41;](../../ssma/mysql/getting-started-with-ssma-for-mysql-mysqltosql.md)  
  
