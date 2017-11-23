---
title: "Сопоставление схемы DB2 схемы SQL Server (DB2ToSQL) | Документы Microsoft"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 05ff7bd4-e60b-4f48-a893-bc2346aa9a8a
caps.latest.revision: "5"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e422c99f45b5da02214aee96bb0520dc8c851e74
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mapping-db2-schemas-to-sql-server-schemas-db2tosql"></a>Сопоставление схемы DB2 схемы SQL Server (DB2ToSQL)
В DB2 каждая база данных имеет один или несколько схем. По умолчанию SSMA выполняет миграцию всех объектов в схеме DB2 нужно [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с именем схемы. Тем не менее, можно настроить сопоставление между схемами DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных.  
  
## <a name="db2-and-sql-server-schemas"></a>DB2 и схемы SQL Server  
Базы данных DB2 содержит схемы. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] содержится несколько баз данных, каждый из которых может быть несколько схем.  
  
Концепция DB2 схемы сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] концепция базы данных и один из его схемы. Например, DB2 установлена схема с именем **HR**. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , возможно, база данных, с именем **HR**, и в этой базе данных, схемы. Одна схема является **dbo** (или владелец базы данных) схемы. По умолчанию схемы DB2 **HR** будут сопоставлены с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных и схемы **HR.dbo**. SSMA ссылается на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] сочетание базы данных и схемы как схема.  
  
Можно изменить сопоставление между DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схем.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA, вы можете сопоставить схемы DB2 доступных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схемы.  
  
**Для изменения базы данных и схемы**  
  
1.  Выберите в обозревателе метаданных DB2 **схемы**.  
  
    **Сопоставление схемы** вкладка доступна при выборе отдельной базы данных, **схемы** папки или отдельные схемы. В списке **сопоставление схемы** вкладку, настроенные для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите список всех схем, DB2, следуют целевое значение. Этот целевой объект, отображаются в виде двух частей (*database.schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] которой будет выполнена миграция объектов и данных.  
  
3.  Выберите строку, которая содержит сопоставления, которое требуется изменить и нажмите кнопку **изменить**.  
  
    В **целевой схемы выберите** диалоговое окно, выполнить обзор для целевой доступные базы данных и схемы или типа базы данных и схемы имя в текстовом поле в нотации двух частей (database.schema) и нажмите кнопку **ОК**.  
  
4.  Целевой объект изменяется на **сопоставление схемы** вкладки.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставляется базы данных-источника в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если в целевую базу данных, сопоставляемого несуществующий на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], то появится сообщение **» базы данных или схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите кнопку Да. Аналогичным образом, можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, который будет создан во время синхронизации.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Восстановление базы данных по умолчанию и схемы  
Если настроить сопоставление между использованием схемы DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схемы, можно отменить сопоставление значения по умолчанию.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, выберите любую строку и нажмите кнопку **по умолчанию** Чтобы восстановить базу данных по умолчанию и схемы.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите проанализировать преобразование объектов DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] объекты, вы можете [(SSMA Common) отчет о миграции данных](http://msdn.microsoft.com/en-us/bbfb9d88-5a98-4980-8d19-c5d78bd0d241).  
  
## <a name="see-also"></a>См. также:  
[Подключение к SQL Server &#40; DB2eToSQL &#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
[Миграция баз данных DB2 в SQL Server &#40; DB2ToSQL &#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
