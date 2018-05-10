---
title: Измененные функции (автономная база данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: databases
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
caps.latest.revision: 27
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2337b4535be26bed2b6c780cf845228c48eafdb6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="modified-features-contained-database"></a>Измененные функции (автономная база данных)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Для поддержки частично автономных баз данных в следующие функции были внесены изменения. Обычно функции изменяются для того, чтобы они не пересекали границу базы данных.  
  
 Дополнительные сведения см. в разделе [Contained Databases](../../relational-databases/databases/contained-databases.md).  
  
## <a name="alter-database"></a>ALTER DATABASE  
  
### <a name="application-level"></a>Уровень приложения  
 При использовании инструкции ALTER DATABASE в автономной базе данных ее синтаксис отличается от синтаксиса при использовании в неавтономной базе данных. Различия включают ограничения на элементы инструкции, действие которых выходит за рамки базы данных на уровень экземпляра. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
### <a name="instance-level"></a>Уровень экземпляра  
 При использовании инструкции ALTER DATABASE применительно к автономной базе данных из-за пределов этой базы данных ее синтаксис отличается от синтаксиса при использовании в неавтономной базе данных. Эти изменения позволяют не допустить пересечения границы базы данных. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md).  
  
## <a name="create-database"></a>CREATE DATABASE  
 При использовании инструкции CREATE DATABASE для автономной базы данных ее синтаксис отличается от синтаксиса при использовании для неавтономной базы данных. Дополнительные сведения о новых требованиях и допущениях синтаксиса см. в статье [CREATE DATABASE (SQL Server Transact-SQL)](../../t-sql/statements/create-database-sql-server-transact-sql.md).  
  
## <a name="temporary-tables"></a>Временные таблицы  
 Локальные временные таблицы в автономных базах данных допускаются, но их поведение отличается от поведения таких таблиц в неавтономных базах данных. В неавтономных базах данных данные во временных таблицах сортируются в соответствии с параметрами сортировки **tempdb**. В автономной базе данных данные во временных таблицах сортируются в соответствии с параметрами сортировки автономной базы данных.  
  
 Все метаданные, связанные со временными таблицами (например, имена таблиц и столбцов, индексов и т. п.), будут иметь параметры сортировки каталога.  
  
 Во временных таблицах не могут использоваться именованные ограничения.  
  
 Временные таблицы не могут ссылаться на определяемые пользователем типы, коллекции схем XML или определяемые пользователем функции.  
  
## <a name="collation"></a>Параметры сортировки  
 В модели неавтономной базы данных имеется три раздельных типа параметров сортировки: параметры сортировки базы данных, параметры сортировки экземпляра и параметры сортировки tempdb. В автономных базах данных используются только два набора параметров сортировки: параметры сортировки базы данных и параметры сортировки новых каталогов. Дополнительные сведения о параметрах сортировки в автономных базах данных см. в разделе [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md) .  
  
## <a name="user-options"></a>Пользовательские параметры  
 При включении поддержки автономных баз данных необходимо установить [параметр «пользовательские параметры»](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) в значение 0 для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Contained Database Collations](../../relational-databases/databases/contained-database-collations.md)   
 [Contained Databases](../../relational-databases/databases/contained-databases.md)  
  
  
