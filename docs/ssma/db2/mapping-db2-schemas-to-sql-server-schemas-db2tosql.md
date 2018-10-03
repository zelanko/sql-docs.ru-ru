---
title: Сопоставление схем DB2 со схемами SQL Server (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 05ff7bd4-e60b-4f48-a893-bc2346aa9a8a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b0f5bcfff72abb16c45aebc12f7c1a2220e2330f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47735502"
---
# <a name="mapping-db2-schemas-to-sql-server-schemas-db2tosql"></a>Сопоставление схем DB2 со схемами SQL Server (DB2ToSQL)
В DB2 каждая база данных имеет один или несколько схем. По умолчанию SSMA выполняет миграцию всех объектов в схеме DB2 для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных с именем схемы. Тем не менее, можно настраивать сопоставление схем DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных.  
  
## <a name="db2-and-sql-server-schemas"></a>DB2 и схемы SQL Server  
Базы данных DB2 содержит схемы. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] содержится несколько баз данных, каждый из которых может быть несколько схем.  
  
Концепция DB2 схемы сопоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] концепция базы данных и один из его схемы. Например, DB2 может иметь схема с именем **HR**. Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может иметь базу данных с именем **HR**, а схемы содержат эту базу данных. Одна схема является **dbo** (или владелец базы данных) схемы. По умолчанию схемы DB2 **HR** будут сопоставлены с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных и схемы **HR.dbo**. SSMA ссылается на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сочетание базы данных и схемы как схема.  
  
Можно изменить сопоставление между DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA, вы можете сопоставить схему DB2 с любой доступный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы.  
  
**Для изменения базы данных и схемы**  
  
1.  В обозревателе метаданных DB2 выберите **схемы**.  
  
    **Сопоставление схемы** вкладка доступна также в случае, при выборе отдельной базы данных, **схемы** папки или отдельные схемы. В списке в **сопоставление схемы** вкладке настраивается для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите список всех схем DB2, а затем целевое значение. Этот целевой объект обозначается в нотации двух частей (*database.schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] где объекты и данные будут перенесены.  
  
3.  Выберите строку, которая содержит сопоставление, которое вы хотите изменить и нажмите кнопку **изменить**.  
  
    В **выберите целевую схему** диалоговое окно, вы можете перейти для доступных целевую базу данных и схемы или тип базы данных и схемы, имя в текстовое поле в нотации двух частей (database.schema), а затем выберите **ОК**.  
  
4.  Целевой объект изменяется на **сопоставление схемы** вкладки.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставлено базы данных-источника к целевому объекту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если целевую базу данных, сопоставляемого несуществующий на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то появляется сообщение **«базы данных или схемы не существует в целевом объекте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите "Да". Аналогичным образом можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, который будет создан во время синхронизации.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Восстановление базы данных по умолчанию и схемы  
Если настроить сопоставление между использованием схемы DB2 и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемы, можно отменить сопоставление значения по умолчанию.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, щелкните любую строку и нажмите кнопку **восстановить значения по умолчанию** для возврата в базу данных по умолчанию и схему.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите анализировать преобразование объектов DB2 в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] объектов, вы можете [(SSMA распространено) отчет о миграции данных](http://msdn.microsoft.com/bbfb9d88-5a98-4980-8d19-c5d78bd0d241).  
  
## <a name="see-also"></a>См. также  
[Подключение к SQL Server &#40;DB2eToSQL&#41;](../../ssma/db2/connecting-to-sql-server-db2etosql.md)  
[Миграция DB2 баз данных в SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/migrating-db2-databases-to-sql-server-db2tosql.md)  
  
