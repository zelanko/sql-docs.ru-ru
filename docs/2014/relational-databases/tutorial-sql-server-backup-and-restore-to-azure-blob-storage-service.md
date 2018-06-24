---
title: 'Учебник: SQL Server резервного копирования и восстановления в Windows Azure BLOB-объект службы хранилища | Документы Microsoft'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 85f16d4f3a96c8d661981a998eab93eaffdc67d7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195547"
---
# <a name="tutorial-sql-server-backup-and-restore-to-windows-azure-blob-storage-service"></a>Tutorial: SQL Server Backup and Restore to Windows Azure Blob Storage Service
  Добро пожаловать в учебник «Приступая к резервному копированию и восстановлению данных SQL Server при помощи службы хранилищ больших двоичных объектов Windows Azure». С помощью этого учебника вы научитесь создавать и восстанавливать резервные копии с помощью службы хранилища больших двоичных объектов Windows Azure.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 В этом учебнике показано, как создать учетную запись хранения Windows, контейнер больших двоичных объектов, учетные данные для доступа к учетной записи хранения, как записать резервную копию в службу хранилищ больших двоичных объектов и выполнить простое восстановление. Учебник разделен на четыре занятия.  
  
 [Занятие 1. Создание объектов хранения Microsoft Azure](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 На этом занятии вы создадите учетную запись хранения Windows Azure и контейнер больших двоичных объектов.  
  
 [Занятие 2. Создание учетных данных SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 На этом занятии вы также создадите учетные данные для хранения сведений о безопасности, которые будут использоваться для доступа к учетной записи хранения Windows Azure.  
  
 [Занятие 3. Запись полной резервной копии базы данных в службе хранилища больших двоичных объектов Microsoft Azure](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 Кроме того, на этом занятии вам предстоит выполнить инструкцию Т-SQL для записи резервной копии базы данных AdventureWorks2012 в службу хранилищ больших двоичных объектов Windows Azure.  
  
 [Занятие 4. Восстановление базы данных из полной резервной копии](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 На этом занятии также предстоит выполнить инструкцию T-SQL для восстановления из резервной копии базы данных, созданной на предыдущем занятии.  
  
### <a name="requirements"></a>Требования  
 Чтобы выполнить задания этого руководства, необходимо владеть основными понятиями резервного копирования и восстановления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и синтаксисом T-SQL. Для работы с этим учебником должны быть выполнены следующие требования.  
  
-   Установленный экземпляр [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] и база данных AdventureWorks2012.  
  
     Экземпляр SQL Server может быть установлен на локальном компьютере или в виртуальной машине Windows Azure.  
  
     Вместо базы данных AdventureWorks2012 можно использовать пользовательскую базу данных, соответственно изменив синтаксис инструкций T-SQL.  
  
-   Учетная запись пользователя, применяемая для выдачи команды BACKUP или RESTORE, должна находиться в роли базы данных **db_backup operator** с разрешениями **Alter any credential** .  
  
### <a name="additional-reading"></a>Дополнительные материалы  
 Чтобы разобраться в концепциях и рекомендуемых методах использования службы хранилищ больших двоичных объектов Windows Azure для резервного копирования [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], рекомендуется изучить перечисленные ниже материалы.  
  
1.  [Резервное копирование и восстановление SQL Server с помощью службы хранилищ больших двоичных объектов Microsoft Azure](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Архивация в SQL Server по URL-адресу — рекомендации и устранение неполадок](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  