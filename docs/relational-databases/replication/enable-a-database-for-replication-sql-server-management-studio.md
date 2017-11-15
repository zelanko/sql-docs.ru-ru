---
title: "Разрешение применения репликации для базы данных (среда SQL Server Management Studio) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
caps.latest.revision: "33"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 39e82237c70f26f8ecf27ba879d0c82f4b279523
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>разрешить для базы данных применение репликации (среда SQL Server Management Studio)
  Применение репликации для базы данных неявно разрешается, когда член предопределенной роли сервера **sysadmin** создает публикацию с помощью мастера создания публикаций. Член предопределенной роли сервера **sysadmin** может также явно разрешить применение репликации для базы данных, чтобы член предопределенной роли базы данных **db_owner** мог создать в этой базе данных одну или несколько публикаций. Чтобы в явном виде включить репликацию базы данных, используйте страницу **Базы данных публикации** диалогового окна **Свойства издателя — \<издатель>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>Разрешение применения репликации для базы данных  
  
1.  На странице **Базы данных публикации** диалогового окна **Свойства издателя — \<издатель>** установите флажки **Транзакционная** и (или) **Слиянием** для каждой базы данных, которую требуется реплицировать. Установите флажок **Транзакционная** , чтобы разрешить для базы данных репликацию моментальных снимков.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
