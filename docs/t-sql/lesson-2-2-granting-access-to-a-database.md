---
title: Предоставление доступа к базе данных | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: t-sql
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- SQL Server 2016
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 75d4f048573ce60b0be6704196b376c8136aa213
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37424093"
---
# <a name="lesson-2-2---granting-access-to-a-database"></a>Урок 2–2. Предоставление доступа к базе данных
[!INCLUDE[tsql-appliesto-ss2008-all-md](../includes/tsql-appliesto-ss2008-all-md.md)]
Теперь Mary имеет доступ к данному экземпляру [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], но не имеет разрешения на доступ к базе данных. У нее даже нет доступа к своей базе данных по умолчанию **TestData** , пока вы не авторизируете ее в качестве пользователя базы данных.  
  
Чтобы предоставить Mary доступ, переключитесь на базу данных **TestData** и при помощи инструкции CREATE USER сопоставьте ее имя входа с именем пользователя «Mary».  
  
### <a name="to-create-a-user-in-a-database"></a>Создание пользователя в базе данных  
  
1.  Введите и выполните следующие инструкции (заменяя `computer_name` на имя компьютера), чтобы предоставить пользователю `Mary` доступ к базе данных `TestData` .  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
    Теперь пользователь Mary имеет доступ к [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и к базе данных `TestData` .  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
[Создание представлений и хранимых процедур](../t-sql/lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
  
