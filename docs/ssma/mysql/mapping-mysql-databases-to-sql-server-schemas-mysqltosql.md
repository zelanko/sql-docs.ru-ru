---
title: Сопоставление баз данных MySQL со схемами SQL Server (MySQLToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Mapping, Modifying target database and schema
- Mapping, reverting to default database and schema
ms.assetid: 5c6fb445-92ae-4933-b77d-80230931c024
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 40a3cf9db1248292d66d2a296c25c53ccfda002d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63311994"
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>Сопоставление баз данных MySQL со схемами SQL Server (MySQLToSQL)
По умолчанию SSMA для MySQL переносит все объекты в схеме MySQL для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или базы данных SQL Azure с именем схемы. Тем не менее, можно настроить сопоставление между схемами MySQL и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или баз данных SQL Azure.  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>MySQL и SQL Server или SQL Azure схемы  
Концепция MySQL схемы сопоставляется понятия SQL Server базу данных и один из его схемы. SSMA относится к SQL Server как схема сочетание базы данных и схемы.  
  
Концепция MySQL схемы сопоставляется понятия SQL Server базу данных и один из его схемы. Например, MySQL может быть схема с именем **HR**. Экземпляр SQL Server может иметь базу данных с именем **HR**, а схемы содержат эту базу данных. Одна схема является **dbo** (или владелец базы данных) схемы. По умолчанию схемы MySQL **HR** будут сопоставлены с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных и схемы **HR.dbo**. SSMA ссылается на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сочетание базы данных и схемы как схема.  
  
Можно изменить сопоставление между MySQL и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или Azure схемы.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA, вы можете сопоставить схемы MySQL любой доступный [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или схемы SQL Azure.  
  
**Для изменения базы данных и схемы**  
  
1.  В обозревателе метаданных MySQL выберите **схемы**.  
  
    **Сопоставление схемы** вкладка доступна также в случае, при выборе отдельные схемы. В списке в **сопоставление схемы** вкладке настраивается для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите список всех схем, MySQL, а затем целевое значение. Этот целевой объект обозначается в нотации двух частей (*database.schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, где объекты и данные будут перенесены.  
  
3.  Выберите строку, которая содержит сопоставление, которое вы хотите изменить и нажмите кнопку **изменить**.  
  
    В **выберите целевую схему** диалоговое окно, вы можете перейти для доступных целевую базу данных и схемы или тип базы данных и схемы, имя в текстовое поле в нотации двух частей (database.schema), а затем выберите **ОК**.  
  
4.  Целевой объект изменяется на **сопоставление схемы** вкладки.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставлено базы данных-источника к целевому объекту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если целевую базу данных, сопоставляемого несуществующий на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то появляется сообщение **«базы данных или схемы не существует в целевом объекте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите "Да". Аналогичным образом можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, который будет создан во время синхронизации.  
  
-   Сопоставление с SQL Azure  
  
База данных-источник можно сопоставить с подключенным целевым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных или ни одной схеме в подключенном целевом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Если сопоставить источник схемы ни одной схеме, не существует в списке подключенных целевую базу данных, то появится сообщение **«схемы не существует в целевой объект метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить? "** Нажмите "Да".  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Восстановление базы данных по умолчанию и схемы  
Если настроить сопоставление схемы MySQL и схемы SQL Server, можно вернуть сопоставление значения по умолчанию.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, щелкните любую строку и нажмите кнопку **восстановить значения по умолчанию** для возврата в базу данных по умолчанию и схему.  
  
## <a name="next-steps"></a>Следующие шаги  
Если вы хотите проанализировать преобразование объектов MySQL в объекты SQL Server или SQL Azure, вы можете [создать отчет о преобразовании](assessing-mysql-databases-for-conversion-mysqltosql.md) в противном случае вы можете [преобразовать определения объектов базы данных MySQL](converting-mysql-databases-mysqltosql.md) в SQL Схемы Server или SQL Azure  
  
## <a name="see-also"></a>См. также  
[Параметры проекта &#40;преобразования&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[Подключение к базе данных Azure SQL &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[Миграция MySQL базы данных в SQL Server — база данных Azure SQL &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
