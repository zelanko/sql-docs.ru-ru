---
title: Задание параметров сортировки пользовательских баз данных совпадают с главной и базами данных модели | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: c686446f-dae1-4b05-a3df-837b3422988d
caps.latest.revision: 12
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2c6cbe79e2af21444e39fb7da7546122cd273ed
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37314584"
---
# <a name="set-the-collation-of-user-defined-databases-to-match-those-of-the-master-and-model-databases"></a>Задание параметров сортировки пользовательских баз данных в соответствии с параметрами баз данных master и model
  Это правило проверяет, определены ли в пользовательской базе данных те же параметры сортировки, что и в базах данных master и model.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Рекомендуется, чтобы параметры сортировки пользовательских баз данных соответствовали параметрам сортировки баз данных master и model. Иначе может произойти конфликт параметров сортировки, мешающий выполнению кода. Например, если хранимая процедура производит соединение таблицы с временной таблицей, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] может завершить работу пакета и вернуть ошибку конфликта параметров сортировки, если параметры сортировки базы данных model отличаются от параметров сортировки пользовательской базы данных. Это происходит потому, что в базе данных tempdb создаются временные таблицы, параметры сортировки которых основаны на параметрах сортировки базы данных model.  
  
 При возникновении ошибок из-за конфликтующих параметров сортировки рекомендуется одно из следующих решений.  
  
-   Экспортируйте данные из пользовательской базы данных и импортируйте их в новые таблицы, параметры сортировки которых совпадают с параметрами сортировки баз данных master и model.  
  
-   Перестройте системные базы данных таким образом, чтобы их параметры сортировки совпадали с параметрами сортировки пользовательской базы данных. Дополнительные сведения о том, как Перестроение системных баз данных см. в разделе [Перестроение системных баз данных](../relational-databases/databases/system-databases.md).  
  
-   Внесите изменения во все хранимые процедуры, производящие соединение пользовательских таблиц с таблицами в базе данных tempdb, чтобы таблицы в tempdb создавались с параметрами сортировки пользовательской базы данных. Для этого в определения столбцов временной таблицы добавьте предложение `COLLATE database_default`, как показано в следующем примере.  
  
    ```  
    CREATE TABLE #temp1 ( c1 int, c2 varchar(30) COLLATE database_default )  
    ```  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [Установка и изменение параметров сортировки базы данных](../relational-databases/collations/set-or-change-the-database-collation.md)  
  
 [Задание или изменение параметров сортировки столбца](../relational-databases/collations/set-or-change-the-column-collation.md)  
  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
 [COLLATE (Transact-SQL)](/sql/t-sql/statements/collations)  
  
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
 [Статье 325335 базы знаний Майкрософт](http://go.microsoft.com/fwlink/?linkid=117751)  
  
 [Как: установить SQL Server 2008 из командной строки](http://go.microsoft.com/fwlink/?LinkId=81585)  
  
## <a name="see-also"></a>См. также  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
