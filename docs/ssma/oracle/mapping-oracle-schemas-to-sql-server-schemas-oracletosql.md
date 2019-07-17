---
title: Сопоставление схем Oracle со схемами SQL Server (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 0edeaa08-9c5d-4e3a-bc15-b9a1f0c8a9dc
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: e375c07ceddc995b599930c14f00710af040d6c0
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262914"
---
# <a name="mapping-oracle-schemas-to-sql-server-schemas-oracletosql"></a>Сопоставление схем Oracle со схемами SQL Server (OracleToSQL)
В Oracle каждая база данных имеет один или несколько схем. По умолчанию SSMA выполняет миграцию всех объектов в схеме Oracle для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных с именем схемы. Тем не менее, можно настраивать сопоставление схем Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных.  
  
## <a name="oracle-and-sql-server-schemas"></a>Oracle и схемы SQL Server  
Базы данных Oracle содержит схемы. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержится несколько баз данных, каждый из которых может быть несколько схем.  
  
Концепция Oracle схемы сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] концепция базы данных и один из его схемы. Например, Oracle может иметь схема с именем **HR**. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может иметь базу данных с именем **HR**, а схемы содержат эту базу данных. Одна схема является **dbo** (или владелец базы данных) схемы. По умолчанию в схеме Oracle **HR** будут сопоставлены с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных и схемы **HR.dbo**. SSMA ссылается на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сочетание базы данных и схемы как схема.  
  
Можно изменить сопоставление между Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA, схему Oracle можно сопоставить с любой доступный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы.  
  
**Для изменения базы данных и схемы**  
  
1.  В обозревателе метаданных Oracle выберите **схемы**.  
  
    **Сопоставление схемы** вкладка доступна также в случае, при выборе отдельной базы данных, **схемы** папки или отдельные схемы. В списке в **сопоставление схемы** вкладке настраивается для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите список всех схем Oracle, а затем целевое значение. Этот целевой объект обозначается в нотации двух частей (*database.schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] где объекты и данные будут перенесены.  
  
3.  Выберите строку, которая содержит сопоставление, которое вы хотите изменить и нажмите кнопку **изменить**.  
  
    В **выберите целевую схему** диалоговое окно, вы можете перейти для доступных целевую базу данных и схемы или тип базы данных и схемы, имя в текстовое поле в нотации двух частей (database.schema), а затем выберите **ОК**.  
  
4.  Целевой объект изменяется на **сопоставление схемы** вкладки.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставлено базы данных-источника к целевому объекту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если целевую базу данных, сопоставляемого несуществующий на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то появляется сообщение **«базы данных или схемы не существует в целевом объекте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите "Да". Аналогичным образом можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, который будет создан во время синхронизации.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Восстановление базы данных по умолчанию и схемы  
Если настроить сопоставление между схему Oracle и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы, можно отменить сопоставление значения по умолчанию.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, щелкните любую строку и нажмите кнопку **восстановить значения по умолчанию** для возврата в базу данных по умолчанию и схему.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите анализировать преобразование объектов Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов, вы можете [создать отчет о преобразовании](assessing-oracle-schemas-for-conversion-oracletosql.md). В противном случае вы можете [преобразовать определения объектов базы данных Oracle](converting-oracle-schemas-oracletosql.md) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определений объекта.  
  
## <a name="see-also"></a>См. также  
[Подключение к SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
[Переход с Oracle баз данных в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
