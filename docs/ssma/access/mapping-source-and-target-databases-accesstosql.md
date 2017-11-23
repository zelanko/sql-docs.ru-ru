---
title: "Сопоставление исходной и целевой баз данных (AccessToSQL) | Документы Microsoft"
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
helpviewer_keywords:
- database schemas
- mapping, databases
- schemas, mapping to
- schemas, SQL Azure
- schemas, SQL Server
- source database
- target database
ms.assetid: 69bee937-7b2c-49ee-8866-7518c683fad4
caps.latest.revision: "17"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3871ac3aa30e788841b0fef27d4134640aac5ad4
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>Сопоставление исходной и целевой баз данных (AccessToSQL)
При подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure, необходимо указать целевую базу данных для миграции. При наличии нескольких баз данных Access их можно привязать к нескольким [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] баз данных (или схемы) или несколько схем в группе соединений с базой данных SQL Azure.  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server или схемы базы данных Azure SQL  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]баз данных используют концепцию схемы к отдельным объектам в базе данных в логические группы. Например, использовать три схемы с именем базы данных библиотеки **электронной**, **аудио**, и **видео** к отдельным объектам книги, аудио и видео друг от друга. По умолчанию базы данных access сопоставляется **master** базы данных и **dbo** схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] и для соединений с базой данных и **dbo** схемы в SQL Azure.  
  
Если не настроить сопоставление между каждой базы данных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных и схемы, SSMA миграция схемы и данные, связанные с базой данных access в базу данных по умолчанию сопоставлено.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
SSMA позволяет сопоставить каждую базу данных Access для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure и схемы. Следующая процедура описывает настраивать сопоставление каждой базы данных.  
  
**Чтобы изменить целевую базу данных и схемы**  
  
1.  В панели обозревателя метаданных доступа выберите **доступ к метаданным**.  
  
    Сопоставление схем будет доступен при выборе **баз данных** узел или узел любой базы данных. В списке Схема сопоставления настраивается для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите таблицу, содержащую доступа имена баз данных и его соответствующие ssNoVersion или схема Sql Azure. В нотации двух частей (database.schema) обозначен в целевой схеме.  
  
3.  Выберите строку, которая содержит сопоставления, нужно настроить и нажмите кнопку **изменить**.  
  
4.  В **целевой схемы выберите** диалоговое окно, выполнить обзор для целевой доступные базы данных и схемы или типа базы данных и схемы имя в текстовом поле в нотации двух частей (database.schema) и нажмите кнопку **ОК**.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставляется базы данных-источника в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если в целевую базу данных, сопоставляемого не существует на [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], то появится сообщение **» базы данных или схемы не существует в целевом [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите кнопку Да. Аналогичным образом, можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, который будет создан во время синхронизации.  
  
-   Сопоставление с SQL Azure  
  
База данных-источник может быть сопоставлен подключенным целевым [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных или к любой схемы в подключенным целевым [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных. Если сопоставить источник схемы ни одной схеме не существует в списке подключенных целевой базы данных, то появится сообщение **«схемы не существует в целевой метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить? «** Нажмите кнопку Да.  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>Возврат к исходной базы данных и схемы  
Если настроить сопоставление между базой данных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или базы данных SQL Azure и схемы, можно вернуть сопоставления в базе данных, указанной при подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] или SQL Azure.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, выберите любую строку и нажмите кнопку **по умолчанию** Чтобы восстановить базу данных по умолчанию и схемы.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом в процессе миграции является [преобразование объектов базы данных](http://msdn.microsoft.com/en-us/e0ef67bf-80a6-4e6c-a82d-5d46e0623c6c)  
  
## <a name="see-also"></a>См. также:  
[Миграция баз данных Access в SQL Server](http://msdn.microsoft.com/en-us/76a3abcf-2998-4712-9490-fe8d872c89ca)  
  
