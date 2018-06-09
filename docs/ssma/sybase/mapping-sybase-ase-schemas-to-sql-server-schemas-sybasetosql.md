---
title: Сопоставление схем Sybase ASE схемы SQL Server (SybaseToSQL) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6ab6b3e6d61290bdad64da2507e562d5cf7e2dae
ms.sourcegitcommit: 8aa151e3280eb6372bf95fab63ecbab9dd3f2e5e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/05/2018
ms.locfileid: "34779080"
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>Sybase ASE схемы сопоставления для схемы SQL Server (SybaseToSQL)
В Sybase адаптивной Server Enterprise (ASE), каждая база данных имеет один или несколько схем. По умолчанию SSMA выполняет миграцию всех объектов базы данных и схемы с одной базой данных и схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure. Тем не менее, можно настроить сопоставление между ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схемы и базы данных SQL Azure.  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>ASE и SQL Server или SQL Azure схемы  
ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или оба SQL Azure укажите баз данных и их схем с помощью двух частей нотации как *database.schema*. Например, в ASE **Демонстрация** базы данных, может возникнуть **dbo** схемы. Что задаются в виде пары базы данных и схемы **demo.dbo**. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure имеет то же базы данных и схема, пары также указана в качестве **demo.dbo**.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA, вы можете сопоставить схему ASE доступных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схема SQL Azure.  
  
**Для изменения базы данных и схемы**  
  
1.  Выберите в обозревателе метаданных Sybase **баз данных**.  
  
    **Сопоставление схемы** вкладка доступна при выборе отдельной базы данных, **схемы** папки или отдельные схемы. В списке **сопоставление схемы** вкладку, настроенные для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите список всех баз данных ASE с их схем, за которым следует значение целевой. Этот целевой объект, отображаются в виде двух частей (*database.schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, где будет выполнена миграция объектов и данных.  
  
3.  Выберите строку, которая содержит сопоставления, которое требуется изменить и нажмите кнопку **изменить**.  
  
4.  В **целевой схемы выберите** диалоговое окно, выполнить обзор для целевой доступные базы данных и схемы или типа базы данных и схемы имя в текстовом поле в нотации двух частей (database.schema) и нажмите кнопку **ОК**.  
  
5.  Целевой объект изменяется на **сопоставление схемы** вкладки.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставляется базы данных-источника в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если в целевую базу данных, сопоставляемого несуществующий на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], то появится сообщение **» базы данных или схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите кнопку Да. Аналогичным образом, можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, который будет создан во время синхронизации.  
  
-   Сопоставление с SQL Azure  
  
Можно сопоставить базы данных-источника в базу данных SQL Azure подключенным целевым ни одной схеме в базе данных SQL Azure подключенным целевым. Если сопоставить источник схемы ни одной схеме не существует в списке подключенных целевой базы данных, то появится сообщение **«схемы не существует в целевой метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить? «** Нажмите кнопку Да.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Восстановление базы данных по умолчанию и схемы  
Если настроить сопоставление между схемой ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схему SQL Azure, можно отменить сопоставление значения по умолчанию.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, выберите любую строку и нажмите кнопку **по умолчанию** Чтобы восстановить базу данных по умолчанию и схемы.  
  
## <a name="next-steps"></a>Следующие шаги  
Нужно выполнить анализ преобразование Sybase ASE объектов в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или объекты, SQL Azure, вы можете [создать отчет о преобразовании](http://msdn.microsoft.com/en-us/eb996b7c-1eef-4f73-b5e6-2fa6faf7336c). В противном случае вы можете [преобразование определения объектов базы данных ASE](http://msdn.microsoft.com/en-us/509cb65d-2f54-427a-83d7-37919cc4e3e3) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или определения объектов SQL Azure.  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Sybase ASE в SQL Server — Azure SQL DB &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
