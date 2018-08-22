---
title: Сопоставление исходной и целевой баз данных (AccessToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
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
caps.latest.revision: 17
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: acb6a8c71c3f144850cb9c24431bcff440cdf761
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2018
ms.locfileid: "40392395"
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>Сопоставление исходной и целевой баз данных (AccessToSQL)
При подключении к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure, необходимо указать целевую базу данных для миграции. Если у вас есть несколько баз данных Access можно сопоставить их к нескольким [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных (или схемы), а также несколько схем в группе соединений с базой данных SQL Azure.  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server и схемы баз данных SQL Azure  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] баз данных используют концепцию схемы для разделения объектов в базе данных в логические группы. Например, использовать три схемы с именем базы данных библиотеки **книги**, **аудио**, и **видео** в отдельные объекты книг, аудио и видео друг от друга. По умолчанию сопоставляется с базой данных access **master** базы данных и **dbo** схемы в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и подключенной базы данных и **dbo** схемы в SQL Azure.  
  
Если не настроить сопоставление между каждой базы данных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных и схемы, SSMA перенесет все схемы и данные, связанные с базой данных доступ к базе данных по умолчанию, сопоставленной.  
  
## <a name="modifying-the-target-database-and-schema"></a>Изменение целевой базы данных и схемы  
SSMA позволяет сопоставить каждую базу данных Access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в базе данных SQL Azure, так и в схеме. Следующая процедура описывает настраивать сопоставление каждой базы данных.  
  
**Чтобы изменить целевую базу данных и схемы**  
  
1.  В панели обозревателя метаданных доступа выберите **доступ к метаданным**.  
  
    Сопоставление схем также доступна, когда вы выбираете **баз данных** узел или любой узел базы данных. Список схем сопоставления настраивается для выбранного объекта.  
  
2.  В области справа щелкните **сопоставление схемы** вкладки.  
  
    Вы увидите таблицу, содержащую доступа имена баз данных и его соответствующий ssNoVersion или схемы Sql Azure. В целевой схеме обозначается в нотации двух частей (database.schema).  
  
3.  Выберите строку, которая содержит сопоставление, вы хотите настроить и нажмите кнопку **изменить**.  
  
4.  В **выберите целевую схему** диалоговое окно, вы можете перейти для доступных целевую базу данных и схемы или тип базы данных и схемы, имя в текстовое поле в нотации двух частей (database.schema), а затем выберите **ОК**.  
  
**Режимы сопоставления**  
  
-   Сопоставление с SQL Server  
  
База данных-источник можно сопоставить с любой целевой базы данных. По умолчанию сопоставлено базы данных-источника к целевому объекту [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, с которым вы подключились, с помощью SSMA. Если выполняется сопоставление целевой базы данных не существует на [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то появится сообщение **«базы данных или схемы не существует в целевом объекте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить?»** Нажмите "Да". Аналогичным образом можно сопоставить схемы и схемы не существует в целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных, который будет создан во время синхронизации.  
  
-   Сопоставление с SQL Azure  
  
База данных-источник можно сопоставить с подключенным целевым [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных или ни одной схеме в подключенном целевом [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных. Если сопоставить источник схемы ни одной схеме, не существует в списке подключенных целевую базу данных, то появится сообщение **«схемы не существует в целевой объект метаданных. Он будет создан во время синхронизации. Вы действительно хотите продолжить? «** Нажмите "Да".  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>Возврат к исходной базы данных и схемы  
Если настроить сопоставление между базой данных Access и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или в базе данных SQL Azure, так и в схеме, можно отменить сопоставление в базе данных, указанной при подключения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или SQL Azure.  
  
**Чтобы восстановить базу данных по умолчанию и схемы**  
  
1.  На вкладке схемы сопоставления, щелкните любую строку и нажмите кнопку **восстановить значения по умолчанию** для возврата в базу данных по умолчанию и схему.  
  
## <a name="next-step"></a>Следующий шаг  
Следующим шагом в процессе миграции является [преобразование объектов базы данных](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>См. также  
[Миграция баз данных Access в SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
