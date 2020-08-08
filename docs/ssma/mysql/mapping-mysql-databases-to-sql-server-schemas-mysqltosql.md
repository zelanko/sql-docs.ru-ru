---
title: Сопоставление баз данных MySQL с SQL Server схемами (MySQLToSQL) | Документация Майкрософт
description: Узнайте, как настроить SSMA для сопоставления MySQL между схемами MySQL и SQL Server или базой данных SQL Azure или принять значение по умолчанию.
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
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: ded91465a2a9c7b5a0e8ddcdc219b2af5a84395e
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935369"
---
# <a name="mapping-mysql-databases-to-sql-server-schemas-mysqltosql"></a>Сопоставление баз данных MySQL со схемами SQL Server (MySQLToSQL)
По умолчанию SSMA для MySQL переносит все объекты в схеме MySQL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базу данных SQL Azure или с именем схемы. Однако вы можете настроить сопоставление между схемами MySQL и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных SQL Azure.  
  
## <a name="mysql-and-sql-server-or-sql-azure-schemas"></a>Схемы MySQL и SQL Server или SQL Azure  
Концепция MySQL схемы сопоставляется с SQL Server концепцией базы данных и одной из ее схем. SSMA относится к сочетанию SQL Server базы данных и схемы в виде схемы.  
  
Концепция MySQL схемы сопоставляется с SQL Server концепцией базы данных и одной из ее схем. Например, MySQL может иметь схему с именем **HR**. Экземпляр SQL Server может иметь базу данных с именем **HR**, а в этой базе данных — схемы. Одной из схем является схема **dbo** (или владелец базы данных). По умолчанию схема MySQL **HR** будет сопоставлена с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных и схемой **HR. dbo**. SSMA ссылается на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сочетание базы данных и схемы в качестве схемы.  
  
Вы можете изменить сопоставление между MySQL и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] схемами Azure.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
В SSMA можно сопоставлять схему MySQL с любой доступной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure схемой.  
  
**Изменение базы данных и схемы**  
  
1.  В обозревателе метаданных MySQL выберите **схемы**.  
  
    Вкладка **сопоставление схем** доступна также при выборе отдельных схем. Список на вкладке **сопоставление схемы** настроен для выбранного объекта.  
  
2.  На панели справа перейдите на вкладку **сопоставление схем** .  
  
    Вы увидите список всех схем MySQL, за которыми следует целевое значение. Этот целевой объект обозначается в нотации с двумя частями (*Database. Schema*) в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, куда будут перенесены объекты и данные.  
  
3.  Выберите строку, содержащую сопоставление, которое необходимо изменить, и нажмите кнопку **изменить**.  
  
    В диалоговом окне **Выбор целевой схемы** можно просмотреть доступную целевую базу данных и схему или ввести имя базы данных и схемы в текстовое поле в нотации с двумя частями (Database. Schema), а затем нажать кнопку **ОК**.  
  
4.  Целевое изменение на вкладке **сопоставление схемы** .  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
Базу данных источника можно сопоставлять с любой целевой базой данных. По умолчанию база данных-источник сопоставляется с целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных, к которой вы подключены с помощью SSMA. Если сопоставляемая Целевая база данных не является существующей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , будет выведено сообщение **"база данных и (или) схема не существует в целевых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Он будет создан во время синхронизации. Вы хотите продолжить?»** Нажмите кнопку "Да". Аналогичным образом можно сопоставлять схему с несуществующей схемой в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных, которая будет создана во время синхронизации.  
  
-   Сопоставление с SQL Azure  
  
Исходную базу данных можно сопоставлять с подключенной целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базой данных или с любой схемой в подключенной целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базе данных. При сопоставлении исходной схемы с любой несуществующей схемой в разделе подключенная Целевая база данных появится сообщение **"схема не существует в целевых метаданных. Он будет создан во время синхронизации. Вы хотите продолжить? "** Нажмите кнопку Да.  
  
## <a name="reverting-to-the-default-database-and-schema"></a>Возврат к базе данных и схеме по умолчанию  
При настройке сопоставления между схемой MySQL и схемой SQL Server можно вернуть сопоставление к значениям по умолчанию.  
  
**Возврат к базе данных и схеме по умолчанию**  
  
1.  На вкладке Сопоставление схемы выберите любую строку и нажмите кнопку **восстановить значения по умолчанию** , чтобы вернуться к базе данных и схеме по умолчанию.  
  
## <a name="next-steps"></a>Next Steps  
Если требуется проанализировать преобразование объектов MySQL в SQL Server или SQL Azure объекты, можно [создать отчет о преобразовании](assessing-mysql-databases-for-conversion-mysqltosql.md) . в противном случае можно [преобразовать определения объектов базы данных MySQL](converting-mysql-databases-mysqltosql.md) в схемы SQL Server или SQL Azure  
  
## <a name="see-also"></a>См. также:  
[Параметры проекта &#40;преобразование&#41; &#40;MySQLToSQL&#41;](../../ssma/mysql/project-settings-conversion-mysqltosql.md)  
[Подключение к базе данных SQL Azure &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-azure-sql-db-mysqltosql.md)  
[Перенос баз данных MySQL в SQL Server базы данных SQL Azure &#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
[Подключение к SQL Server &#40;MySQLToSQL&#41;](../../ssma/mysql/connecting-to-sql-server-mysqltosql.md)  
  
