---
title: Сопоставление схем ASE Sybase с схемами SQL Server (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Schema Mapping
ms.assetid: 2c927003-c49d-4fe1-8e3e-5b2899166268
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: acd4b7c13b2f8674f120c7f5b49f503a7f8fb5bc
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87931229"
---
# <a name="mapping-sybase-ase-schemas-to-sql-server-schemas-sybasetosql"></a>Сопоставление схем Sybase ASE со схемами SQL Server (SybaseToSQL)
В хранилище Sybase адаптивного сервера Enterprise (ASE) каждая база данных имеет одну или несколько схем. По умолчанию SSMA переносит все объекты в базе данных и схеме в ту же базу данных и схему в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure. Однако вы можете настроить сопоставление между ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных SQL Azure.  
  
## <a name="ase-and-sql-server-or-sql-azure-schemas"></a>Схемы ASE и SQL Server или SQL Azure  
ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] or SQL Azure указывают базы данных и их схемы, используя две части нотации: *Database. Schema*. Например, в **демонстрационной** базе данных ASE может существовать схема **dbo** . Эта пара базы данных и схемы указывается как **Demo. dbo**. Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure имеет одну и ту же базу данных и схему, то пара также указывается как **Demo. dbo**.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA можно сопоставлять схему ASE с любой доступной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure схемой.  
  
**Изменение базы данных и схемы**  
  
1.  В обозревателе метаданных Sybase выберите **базы данных**.  
  
    Вкладка **сопоставление схем** доступна также при выборе отдельной базы данных, папки **Schemas** или отдельных схем. Список на вкладке **сопоставление схемы** настроен для выбранного объекта.  
  
2.  На панели справа перейдите на вкладку **сопоставление схем** .  
  
    Вы увидите список всех баз данных ASE со своими схемами, за которыми следует целевое значение. Этот целевой объект обозначается в нотации с двумя частями (*Database. Schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, куда будут перенесены объекты и данные.  
  
3.  Выберите строку, содержащую сопоставление, которое необходимо изменить, и нажмите кнопку **изменить**.  
  
4.  В диалоговом окне **Выбор целевой схемы** можно просмотреть доступную целевую базу данных и схему или ввести имя базы данных и схемы в текстовое поле в нотации с двумя частями (Database. Schema), а затем нажать кнопку **ОК**.  
  
5.  Целевое изменение на вкладке **сопоставление схемы** .  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
Базу данных источника можно сопоставлять с любой целевой базой данных. По умолчанию база данных-источник сопоставляется с целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных, к которой вы подключены с помощью SSMA. Если сопоставляемая Целевая база данных не является существующей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , будет выведено сообщение **"база данных и (или) схема не существует в целевых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Он будет создан во время синхронизации. Вы хотите продолжить?»** Нажмите кнопку "Да". Аналогичным образом можно сопоставлять схему с несуществующей схемой в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных, которая будет создана во время синхронизации.  
  
-   Сопоставление с SQL Azure  
  
Можно сопоставлять базу данных источника с подключенной целевой базой данных SQL Azure или с любой схемой в подключенной целевой базе данных SQL Azure. При сопоставлении исходной схемы с любой несуществующей схемой в разделе подключенная Целевая база данных появится сообщение **"схема не существует в целевых метаданных. Он будет создан во время синхронизации. Вы хотите продолжить? "** Нажмите кнопку Да.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Возврат к базе данных и схеме по умолчанию  
Если вы настраиваете сопоставление между схемой ASE и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемой или SQL Azure, можно вернуть сопоставление к значениям по умолчанию.  
  
**Возврат к базе данных и схеме по умолчанию**  
  
1.  На вкладке Сопоставление схемы выберите любую строку и нажмите кнопку **восстановить значения по умолчанию** , чтобы вернуться к базе данных и схеме по умолчанию.  
  
## <a name="next-steps"></a>Next Steps  
Если необходимо проанализировать преобразование объектов Sybase ASE в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure объекты, можно [создать отчет о преобразовании](assessing-sybase-ase-database-objects-for-conversion-sybasetosql.md). В противном случае [определения объектов базы данных ASE можно преобразовать](converting-sybase-ase-database-objects-sybasetosql.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определения объектов или SQL Azure.  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Sybase ASE в SQL Server — база данных SQL Azure &#40;SybaseToSQL&#41;](../../ssma/sybase/migrating-sybase-ase-databases-to-sql-server-azure-sql-db-sybasetosql.md)  
  
