---
title: Измененные функции (автономная база данных) | Документация Майкрософт
ms.custom: ''
ms.date: 07/17/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- contained database, modifications to DBs
ms.assetid: a2942509-39a2-4903-b504-ae80a300a9de
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9577ef03aafe17a7590812a49212ff1e5263ed46
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36087867"
---
# <a name="modified-features-contained-database"></a>Измененные функции (автономная база данных)
  Для поддержки частично автономных баз данных в следующие функции были внесены изменения. Обычно функции изменяются для того, чтобы они не пересекали границу базы данных.  
  
 Дополнительные сведения см. в разделе [Contained Databases](contained-databases.md).  
  
## <a name="alter-database"></a>ALTER DATABASE  
  
### <a name="application-level"></a>Уровень приложения  
 При использовании инструкции ALTER DATABASE в автономной базе данных ее синтаксис отличается от синтаксиса при использовании в неавтономной базе данных. Различия включают ограничения на элементы инструкции, действие которых выходит за рамки базы данных на уровень экземпляра. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql).  
  
### <a name="instance-level"></a>Уровень экземпляра  
 При использовании инструкции ALTER DATABASE применительно к автономной базе данных из-за пределов этой базы данных ее синтаксис отличается от синтаксиса при использовании в неавтономной базе данных. Эти изменения позволяют не допустить пересечения границы базы данных. Дополнительные сведения см. в разделе [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql).  
  
## <a name="create-database"></a>CREATE DATABASE  
 При использовании инструкции CREATE DATABASE для автономной базы данных ее синтаксис отличается от синтаксиса при использовании для неавтономной базы данных. Дополнительные сведения о новых требованиях и допущениях синтаксиса см. в статье [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql).  
  
## <a name="temporary-tables"></a>Временные таблицы  
 Локальные временные таблицы в автономных базах данных допускаются, но их поведение отличается от поведения таких таблиц в неавтономных базах данных. В неавтономных базах данных данные во временных таблицах сортируются в соответствии с параметрами сортировки **tempdb**. В автономной базе данных данные во временных таблицах сортируются в соответствии с параметрами сортировки автономной базы данных.  
  
 Все метаданные, связанные со временными таблицами (например, имена таблиц и столбцов, индексов и т. п.), будут иметь параметры сортировки каталога.  
  
 Во временных таблицах не могут использоваться именованные ограничения.  
  
 Временные таблицы не могут ссылаться на определяемые пользователем типы, коллекции схем XML или определяемые пользователем функции.  
  
## <a name="collation"></a>Параметры сортировки  
 В модели неавтономной базы данных имеется три раздельных типа параметров сортировки: параметры сортировки базы данных, параметры сортировки экземпляра и параметры сортировки tempdb. В автономных базах данных используются только два набора параметров сортировки: параметры сортировки базы данных и параметры сортировки новых каталогов. Дополнительные сведения о параметрах сортировки в автономных базах данных см. в разделе [Contained Database Collations](contained-database-collations.md) .  
  
## <a name="user-options"></a>Пользовательские параметры  
 При включении поддержки автономных баз данных необходимо установить [параметр «пользовательские параметры»](../../database-engine/configure-windows/configure-the-user-options-server-configuration-option.md) в значение 0 для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Contained Database Collations](contained-database-collations.md)   
 [Contained Databases](contained-databases.md)  
  
  
