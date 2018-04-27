---
title: Сопоставление схемы Oracle для схемы SQL Server (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: On Demand
ms.openlocfilehash: e51a3b70f585bebd353a84b9c0274180a0daf870
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>Сопоставление схемы Oracle для схемы SQL Server (OracleToSQL)
В Oracle каждая база данных имеет один или несколько схем. По умолчанию SSMA выполняет миграцию всех объектов в схеме Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с именем схемы. Тем не менее, можно настроить сопоставление между схемами Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных.  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle и схемы SQL Server  
Базы данных Oracle содержит схемы. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] содержится несколько баз данных, каждый из которых может быть несколько схем.  
  
Концепция Oracle схемы сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] концепция базы данных и один из его схемы. Например, Oracle установлена схема с именем **HR**. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , возможно, база данных, с именем **HR**, и в этой базе данных, схемы. Одна схема является **dbo** (или владелец базы данных) схемы. По умолчанию в схеме Oracle **HR** будут сопоставлены с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных и схемы **HR.dbo**. SSMA ссылается на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] сочетание базы данных и схемы как схема.  
  
Можно изменить сопоставление между Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схем.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA, вы можете сопоставить схеме Oracle доступных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схемы.  
  
**Для изменения базы данных и схемы**  
  
1.  Выберите в обозревателе метаданных Oracle **схемы**.  
  
    **Сопоставление схемы** вкладка доступна при выборе отдельной базы данных, **схемы** папки или отдельные схемы. В списке **сопоставление схемы** вкладку, настроенные для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите список всех схем Oracle, за которым следует значение целевой. Этот целевой объект, отображаются в виде двух частей (*database.schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] которой будет выполнена миграция объектов и данных.  
  
3.  Выберите строку, которая содержит сопоставления, которое требуется изменить и нажмите кнопку **изменить**.  
  
    В **целевой схемы выберите** диалоговое окно, выполнить обзор для целевой доступные базы данных и схемы или типа базы данных и схемы имя в текстовом поле в нотации двух частей (database.schema) и нажмите кнопку **ОК**.  
  
4.  Целевой объект изменяется на **сопоставление схемы** вкладки.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставляется базы данных-источника в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если в целевую базу данных, сопоставляемого несуществующий на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], то появится сообщение **» базы данных или схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите кнопку Да. Аналогичным образом, можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, который будет создан во время синхронизации.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Восстановление базы данных по умолчанию и схемы  
Если настроить сопоставление между использованием схемы Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] схемы, можно отменить сопоставление значения по умолчанию.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, выберите любую строку и нажмите кнопку **по умолчанию** Чтобы восстановить базу данных по умолчанию и схемы.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите проанализировать преобразование объектов Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] объектов, вы можете [создать отчет о преобразовании](http://msdn.microsoft.com/en-us/4de9bcf6-1346-4740-87f9-7f24a8226357). В противном случае вы можете [преобразование определения объектов базы данных Oracle](http://msdn.microsoft.com/en-us/e021182d-31da-443d-b110-937f5db27272) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] определений объекта.  
  
## <a name="see-also"></a>См. также  
[Подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[Миграция Oracle баз данных SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
