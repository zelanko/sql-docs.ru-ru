---
title: Учебник. Резервное копирование и восстановление SQL Server с помощью службы хранилища BLOB-объектов Azure | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 9e1d94ce-2c93-45d1-ae2a-2a7d1fa094c4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 8a9cbb46b04491be3fe97cb707ad79c98990ff19
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155332"
---
# <a name="tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service"></a>Учебник. Резервное копирование и восстановление SQL Server с помощью службы хранилищ BLOB-объектов Azure
  Добро пожаловать в начало работы с помощью SQL Server резервного копирования и восстановления с помощью службы хранилища BLOB-объектов Azure. С помощью этого руководства вы научитесь создавать и восстанавливать резервные копии, используя службу хранилища BLOB-объектов Azure.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 В этом учебнике показано, как создать учетную запись хранения Windows, контейнер больших двоичных объектов, учетные данные для доступа к учетной записи хранения, как записать резервную копию в службу хранилищ больших двоичных объектов и выполнить простое восстановление. Учебник разделен на четыре занятия.  
  
 [Занятие 1. Создание объектов службы хранилища Azure](../tutorials/lesson-1-create-windows-azure-storage-objects.md)  
 На этом занятии вы создадите учетную запись хранения Azure и контейнер больших двоичных объектов.  
  
 [Занятие 2. Создание учетных данных SQL Server](../tutorials/lesson-2-create-a-sql-server-credential.md)  
 На этом занятии вы создадите учетные данные для хранения сведений о безопасности, которые будут использоваться для доступа к учетной записи хранения Azure.  
  
 [Занятие 3. Запись полной резервной копии базы данных в службу хранилища BLOB-объектов Azure](../tutorials/lesson-3-write-a-full-database-backup-to-the-windows-azure-blob-storage-service.md)  
 На этом занятии вам предстоит выполнить инструкцию Т-SQL для записи резервной копии базы данных AdventureWorks2012 в службу хранилища BLOB-объектов Azure.  
  
 [Занятие 4. Восстановление из полной резервной копии базы данных](../tutorials/lesson-4-perform-a-restore-from-a-full-database-backup.md)  
 На этом занятии также предстоит выполнить инструкцию T-SQL для восстановления из резервной копии базы данных, созданной на предыдущем занятии.  
  
### <a name="requirements"></a>Требования  
 Чтобы выполнить задания этого руководства, необходимо владеть основными понятиями резервного копирования и восстановления [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и синтаксисом T-SQL. Для работы с этим учебником должны быть выполнены следующие требования.  
  
-   Установленный экземпляр [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] и база данных AdventureWorks2012.  
  
     SQL Server экземпляр может быть локальным или виртуальной машиной Azure.  
  
     Вместо базы данных AdventureWorks2012 можно использовать пользовательскую базу данных, соответственно изменив синтаксис инструкций T-SQL.  
  
-   Учетная запись пользователя, применяемая для выдачи команды BACKUP или RESTORE, должна находиться в роли базы данных **db_backup operator** с разрешениями **Alter any credential** .  
  
### <a name="additional-reading"></a>Дополнительные материалы  
 Чтобы разобраться в концепциях и предпочтительных методах использования службы хранилища BLOB-объектов Azure для резервного копирования [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], рекомендуется изучить перечисленные ниже материалы.  
  
1.  [SQL Server резервного копирования и восстановления с помощью службы хранилища BLOB-объектов Azure](backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
2.  [Архивация в SQL Server по URL-адресу — рекомендации и устранение неполадок](backup-restore/sql-server-backup-to-url-best-practices-and-troubleshooting.md)  
  
  
