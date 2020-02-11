---
title: Учебник. SQL Server файлов данных в службе хранилища Azure | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: a15f6735ef0ef79b7eb953445c926f60f6bfb12e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "70176084"
---
# <a name="tutorial-sql-server-data-files-in-azure-storage-service"></a>Учебник. Файлы данных SQL Server в службе хранилища Azure
  Добро пожаловать в учебник по SQL Server файлы данных в службе хранилища Azure. С помощью этого руководства вы научитесь напрямую сохранять файлы данных SQL Server в службе хранилища BLOB-объектов Azure.  
  
 Поддержка интеграции SQL Server для службы хранилища BLOB-объектов Azure — это усовершенствование SQL Server 2014. Общие сведения о функциональных возможностях и преимуществах использования этой функции см. [в статье SQL Server файлы данных в Azure](databases/sql-server-data-files-in-microsoft-azure.md).  
  
## <a name="what-you-will-learn"></a>Новые знания  
 В этом руководстве показано, как хранить файлы данных SQL Server в службе хранилища Azure на нескольких занятиях. Каждое занятие сфокусировано на конкретной задаче. Во-первых, вы узнаете, как создать учетную запись хранения и контейнер в Azure. Затем вы узнаете, как создать SQL Server учетные данные для интеграции SQL Server с хранилищем Azure. Затем вы создадите базу данных непосредственно в службе хранилища Azure. Кроме того, в учебнике демонстрируются сценарии шифрования, миграции, резервного копирования и восстановления.  
  
 Учебник разделен на девять занятий.  
  
 **[Занятие 1. Создание учетной записи службы хранилища Azure и контейнера](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 На этом занятии вы создадите учетную запись хранения Azure и контейнер.  
  
 **[Занятие 2. Создание политики в контейнере и создание подписанного URL-адрес &#40;ключ SAS&#41;](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 На этом занятии вы создадите политику в контейнере больших двоичных объектов, а также сформируете подписанный URL-адрес.  
  
 **[Занятие 3. Создание учетных данных SQL Server](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 На этом занятии вы создадите учетные данные для хранения сведений о безопасности, которые будут использоваться для доступа к учетной записи хранения Azure.  
  
 **[Занятие 4. Создание базы данных в службе хранилища Azure](../relational-databases/lesson-3-database-backup-to-url.md)**  
 На этом занятии вы создадите базу данных в службе хранилища Azure, используя параметр создания имени файла базы данных.  
  
 **[Занятие 5. &#40;необязательно&#41; шифрование базы данных с помощью TDE](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
 На этом занятии вы зашифруете базу данных с помощью прозрачного шифрования данных (TDE) и сертификата сервера.  
  
 **[Занятие 6. Перенос базы данных с исходного локального компьютера на целевой компьютер в Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 На этом занятии вы перенесете базу данных из локальной среды в виртуальную машину в Azure с помощью команды CREATE DATABASE для ATTACH.  
  
 **[Занятие 7. Перенос файлов данных в службу хранилища Azure](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 На этом занятии вы перемещаете файлы данных в службу хранилища Azure с помощью инструкции ALTER DATABASE.  
  
 **[Занятие 8. Восстановление базы данных в службе хранилища Azure](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 На этом занятии вы восстановите базу данных в службе хранилища Azure с помощью параметра RESTORE DATABASE MOVE.  
  
 **[Занятие 9. Восстановление базы данных из службы хранилища Azure](lesson-8-restore-as-new-database-from-log-backup.md)**  
 На этом занятии вы восстановите базу данных из службы хранилища Azure с помощью параметра RESTORE DATABASE MOVE.  
  
## <a name="see-also"></a>См. также:  
 [Файлы данных SQL Server в Azure](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
