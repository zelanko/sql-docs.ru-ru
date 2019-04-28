---
title: Сопоставление схем Sybase ASE со схемами SQL Server (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 2a27b2e7c915a1ac13050d0ed188002cd42746c8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62705937"
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>Сопоставление схем Sybase ASE со схемами SQL Server (SybaseToSQL)
В Sybase Adaptive Server Enterprise (ASE), каждая база данных имеет один или несколько схем. По умолчанию SSMA выполняет миграцию всех объектов в пределах базы данных и схемы на один и тот же базы данных и схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Тем не менее, можно настроить сопоставление между ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или баз данных SQL Azure, так и схемы.  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>ASE и SQL Server или SQL Azure схемы  
ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или указать оба SQL Azure баз данных и их схем с помощью двух нотации часть как *database.schema*. Например, в среде ASE **Демонстрация** базы данных, может возникнуть **dbo** схемы. Что задаются в виде пары из базы данных и схемы **demo.dbo**. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure с одной базы данных и схемы, пары также указывается как **demo.dbo**.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA, схему ASE можно сопоставить с любой доступный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы SQL Azure.  
  
**Для изменения базы данных и схемы**  
  
1.  Выберите в обозревателе метаданных Sybase **баз данных**.  
  
    **Сопоставление схемы** вкладка доступна также в случае, при выборе отдельной базы данных, **схемы** папки или отдельные схемы. В списке в **сопоставление схемы** вкладке настраивается для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите список всех баз данных ASE с их схем, а затем целевое значение. Этот целевой объект обозначается в нотации двух частей (*database.schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, где объекты и данные будут перенесены.  
  
3.  Выберите строку, которая содержит сопоставление, которое вы хотите изменить и нажмите кнопку **изменить**.  
  
4.  В **выберите целевую схему** диалоговое окно, вы можете перейти для доступных целевую базу данных и схемы или тип базы данных и схемы, имя в текстовое поле в нотации двух частей (database.schema), а затем выберите **ОК**.  
  
5.  Целевой объект изменяется на **сопоставление схемы** вкладки.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставлено базы данных-источника к целевому объекту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если целевую базу данных, сопоставляемого несуществующий на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то появляется сообщение **«базы данных или схемы не существует в целевом объекте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите "Да". Аналогичным образом можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, который будет создан во время синхронизации.  
  
-   Сопоставление с SQL Azure  
  
Вы можете сопоставить базы данных-источника, подключенных целевую базу данных SQL Azure или ни одной схеме подключенного целевой базы данных SQL Azure. Если сопоставить источник схемы ни одной схеме, не существует в списке подключенных целевую базу данных, то появится сообщение **«схемы не существует в целевой объект метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить? "** Нажмите "Да".  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Восстановление базы данных по умолчанию и схемы  
Если настроить сопоставление между схему ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схему SQL Azure, можно отменить сопоставление значения по умолчанию.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, щелкните любую строку и нажмите кнопку **восстановить значения по умолчанию** для возврата в базу данных по умолчанию и схему.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите анализировать преобразование объектов Sybase ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или объекты, SQL Azure, вы можете [создать отчет о преобразовании](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md). В противном случае вы можете [преобразовать определения объектов базы данных ASE](converting-sybase-ase-database-objects-sybasetosql.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или определения объектов SQL Azure.  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Sybase ASE в SQL Server — база данных Azure SQL &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
