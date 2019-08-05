---
title: Разрешение применения репликации для базы данных (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 8a52640a104af0030d0ebf51162e0efbda80d56a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68768127"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>разрешить для базы данных применение репликации (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  
Применение репликации для базы данных неявно разрешается, когда член предопределенной роли сервера **sysadmin** создает публикацию с помощью мастера создания публикаций. Член предопределенной роли сервера **sysadmin** может также явно разрешить применение репликации для базы данных, чтобы член предопределенной роли базы данных **db_owner** мог создать в этой базе данных одну или несколько публикаций. Чтобы в явном виде включить репликацию базы данных, используйте страницу **Базы данных публикации** диалогового окна **Свойства издателя — \<издатель>** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
## <a name="using-sql-server-management-studio-ssms"></a>Использование среды SQL Server Management Studio (SSMS)
  
1.  На странице **Базы данных публикации** диалогового окна **Свойства издателя — \<издатель>** установите флажки **Транзакционная** и (или) **Слиянием** для каждой базы данных, которую требуется реплицировать. Установите флажок **Транзакционная** , чтобы разрешить для базы данных репликацию моментальных снимков.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
## <a name="using-transact-sql-t-sql"></a>Использование Transact-SQL (T-SQL)
Вы можете разрешить репликацию для базы данных с помощью следующего кода Transact-SQL: 

```sql
USE master
EXEC sp_replicationdboption @dbname = 'AdventureWorks2017',
@optname = 'publish',
@value = 'true'
GO
```

Чтобы отключить публикацию, задайте для @value значение false. 
