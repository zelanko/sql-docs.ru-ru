---
title: Сопоставление баз данных MySQL в схемы SQL Server (MySQLToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-mysql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Mapping, Modifying target database and schema
- Mapping, reverting to default database and schema
ms.assetid: 5c6fb445-92ae-4933-b77d-80230931c024
caps.latest.revision: 7
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 79cbcae3c7c272f871b18ff0fc9b5a5c1acce57f
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>Сопоставление баз данных MySQL в схемы SQL Server (MySQLToSQL)
По умолчанию SSMA для MySQL выполняет миграцию всех объектов в схему, MySQL [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure с именем схемы. Тем не менее, можно настроить сопоставление между схемами, MySQL и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или баз данных SQL Azure.  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>MySQL и SQL Server или SQL Azure схемы  
Концепция MySQL схемы сопоставляется концепция SQL Server из базы данных и один из его схемы. SSMA относится к SQL Server как схема сочетание базы данных и схемы.  
  
Концепция MySQL схемы сопоставляется концепция SQL Server из базы данных и один из его схемы. Например, MySQL установлена схема с именем **HR**. Возможно, экземпляр SQL Server с именем базы данных **HR**, и в этой базе данных, схемы. Одна схема является **dbo** (или владелец базы данных) схемы. По умолчанию схемы MySQL **HR** будут сопоставлены с [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных и схемы **HR.dbo**. SSMA ссылается на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] сочетание базы данных и схемы как схема.  
  
Можно изменить сопоставление между MySQL и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или Azure схем.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA, вы можете сопоставить схемы MySQL доступных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или схема SQL Azure.  
  
**Для изменения базы данных и схемы**  
  
1.  Выберите в обозревателе метаданных MySQL **схемы**.  
  
    **Сопоставление схемы** вкладка доступна при выборе отдельные схемы. В списке **сопоставление схемы** вкладку, настроенные для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите список всех схем, MySQL, следуют целевое значение. Этот целевой объект, отображаются в виде двух частей (*database.schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, где будет выполнена миграция объектов и данных.  
  
3.  Выберите строку, которая содержит сопоставления, которое требуется изменить и нажмите кнопку **изменить**.  
  
    В **целевой схемы выберите** диалоговое окно, выполнить обзор для целевой доступные базы данных и схемы или типа базы данных и схемы имя в текстовом поле в нотации двух частей (database.schema) и нажмите кнопку **ОК**.  
  
4.  Целевой объект изменяется на **сопоставление схемы** вкладки.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставляется базы данных-источника в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если в целевую базу данных, сопоставляемого несуществующий на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], то появится сообщение **» базы данных или схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите кнопку Да. Аналогичным образом, можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, который будет создан во время синхронизации.  
  
-   Сопоставление с SQL Azure  
  
База данных-источник может быть сопоставлен подключенным целевым [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных или к любой схемы в подключенным целевым [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Если сопоставить источник схемы ни одной схеме не существует в списке подключенных целевой базы данных, то появится сообщение **«схемы не существует в целевой метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить? «** Нажмите кнопку Да.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Восстановление базы данных по умолчанию и схемы  
Если настроить сопоставление схемы MySQL и схемы SQL Server, можно вернуть сопоставление значения по умолчанию.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, выберите любую строку и нажмите кнопку **по умолчанию** Чтобы восстановить базу данных по умолчанию и схемы.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите проанализировать преобразование объектов MySQL в объекты SQL Server или SQL Azure, вы можете [создать отчет о преобразовании](http://msdn.microsoft.com/en-us/2a56a003-3b0f-453a-963c-00c9e40933ec) в противном случае вы можете [преобразование определения объектов базы данных MySQL](http://msdn.microsoft.com/en-us/ac21850b-fb32-4704-9985-5759b7c688c7) в схемы SQL Server или SQL Azure  
  
## <a name="see-also"></a>См. также  
[Параметры проекта &#40;преобразования&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[Подключение к базе данных Azure SQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[Миграция MySQL баз данных SQL Server — Azure SQL DB &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
