---
title: Разрешение применения репликации для базы данных (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: 33
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8f565f2847c0ff7091503b924a087b3211b6c76f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>разрешить для базы данных применение репликации (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Применение репликации для базы данных неявно разрешается, когда член предопределенной роли сервера **sysadmin** создает публикацию с помощью мастера создания публикаций. Член предопределенной роли сервера **sysadmin** может также явно разрешить применение репликации для базы данных, чтобы член предопределенной роли базы данных **db_owner** мог создать в этой базе данных одну или несколько публикаций. Чтобы в явном виде включить репликацию базы данных, используйте страницу **Базы данных публикации** диалогового окна **Свойства издателя — \<издатель>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>Разрешение применения репликации для базы данных  
  
1.  На странице **Базы данных публикации** диалогового окна **Свойства издателя — \<издатель>** установите флажки **Транзакционная** и (или) **Слиянием** для каждой базы данных, которую требуется реплицировать. Установите флажок **Транзакционная** , чтобы разрешить для базы данных репликацию моментальных снимков.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
