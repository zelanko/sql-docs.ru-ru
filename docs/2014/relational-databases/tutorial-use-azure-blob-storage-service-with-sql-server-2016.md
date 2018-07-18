---
title: 'Учебник: SQL Server Data Files в службе хранилища Windows Azure | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e69be67d-da1c-41ae-8c9a-6b12c8c2fb61
caps.latest.revision: 7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f805d7a9b0997d9f5a7cecbf61b5120bdf09f3cd
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323864"
---
# <a name="tutorial-sql-server-data-files-in-windows-azure-storage-service"></a>Учебник. Файлы данных SQL Server в службе хранилища Windows Azure
  Учебник по интеграции файлов данных SQL Server со службой хранилища Windows Azure. С помощью этого учебника вы научитесь напрямую сохранять файлы данных SQL Server в службе хранилища больших двоичных объектов Windows Azure.  
  
 Поддержка службы хранилища больших двоичных объектов для интеграции SQL Server стала возможной благодаря усовершенствованиям в версии SQL Server 2014. Обзор функциональных возможностей и преимуществ использования этих функций, см. в разделе [SQL Server Data Files в Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md).  
  
## <a name="what-you-will-learn"></a>Новые знания  
 В данном учебнике в ходе ряда занятий показано, как сохранить файлы данных SQL Server в службе хранилища Windows Azure. Каждое занятие сфокусировано на конкретной задаче. В начале будет показано, как создавать учетную запись хранилища и контейнер в Windows Azure. Затем вы узнаете, как создать имя входа SQL Server, чтобы иметь возможность интегрировать SQL Server с хранилищем Windows Azure. Затем вы напрямую создадите новую базу данных в хранилище Windows Azure. Кроме того, в учебнике демонстрируются сценарии шифрования, миграции, резервного копирования и восстановления.  
  
 Учебник разделен на девять занятий.  
  
 **[Занятие 1: Создание учетной записи хранения Azure для Windows и контейнера](../tutorials/lesson-1-create-windows-azure-storage-account-and-container.md)**  
 На этом занятии вы создадите учетную запись хранилища Windows Azure и контейнер.  
  
 **[Занятие 2. Создать политику для контейнера и создать подпись общего доступа &#40;SAS&#41; ключ](lesson-1-create-stored-access-policy-and-shared-access-signature.md)**  
 На этом занятии вы создадите политику в контейнере больших двоичных объектов, а также сформируете подписанный URL-адрес.  
  
 **[Занятие 3: Создание учетных данных SQL Server](lesson-2-create-a-sql-server-credential-using-a-shared-access-signature.md)**  
 На этом занятии вы также создадите учетные данные для хранения сведений о безопасности, которые будут использоваться для доступа к учетной записи хранения Windows Azure.  
  
 **[Занятие 4: Создание базы данных в хранилище Windows Azure](../relational-databases/lesson-3-database-backup-to-url.md)**  
 На этом занятии вы создадите базу данных в хранилище Windows Azure с помощью параметра CREATE Database FILENAME.  
  
 **[Занятие 5. &#40;Необязательно&#41; зашифровать базу данных с помощью прозрачного шифрования данных](../relational-databases/lesson-4-restore-database-to-virtual-machine-from-url.md)**  
 На этом занятии вы зашифруете базу данных с помощью прозрачного шифрования данных (TDE) и сертификата сервера.  
  
 **[Занятие 6: Перенос базы данных из источника локального компьютера на целевой компьютер в Windows Azure](lesson-5-backup-database-using-file-snapshot-backup.md)**  
 На этом занятии вы перенесете базу данных с локальной на виртуальную машину в Windows Azure с помощью параметра CREATE DATABASE FOR ATTACH.  
  
 **[Занятие 7: Перемещение файлов данных в хранилище Windows Azure](../relational-databases/lesson-6-generate-activity-and-backup-log-using-file-snapshot-backup.md)**  
 На этом занятии вы перенесете свои файлы данных в хранилище Windows Azure с помощью инструкции ALTER DATABASE.  
  
 **[Занятие 8. Восстановление базы данных в хранилище Windows Azure](../relational-databases/lesson-7-restore-a-database-to-a-point-in-time.md)**  
 На этом занятии вы выполните восстановление базы данных в хранилище Windows Azure с помощью параметра RESTORE Database MOVE.  
  
 **[Занятие 9. Восстановление базы данных из хранилища Windows Azure](lesson-8-restore-as-new-database-from-log-backup.md)**  
 На этом занятии вы выполните восстановление базы данных из хранилища Windows Azure с помощью параметра RESTORE Database MOVE.  
  
## <a name="see-also"></a>См. также  
 [Файлы данных SQL Server в Windows Azure](databases/sql-server-data-files-in-microsoft-azure.md)  
  
  
