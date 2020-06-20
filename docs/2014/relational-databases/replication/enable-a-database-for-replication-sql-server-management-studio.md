---
title: Разрешение применения репликации для базы данных (среда SQL Server Management Studio) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- databases [SQL Server replication]
ms.assetid: 8092faa3-9cff-4f81-926c-6a0070d1ce2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 307d52e24187e35c1c30f609facd13bfad569216
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010738"
---
# <a name="enable-a-database-for-replication-sql-server-management-studio"></a>разрешить для базы данных применение репликации (среда SQL Server Management Studio)
  Применение репликации для базы данных неявно разрешается, когда член предопределенной роли сервера **sysadmin** создает публикацию с помощью мастера создания публикаций. Член предопределенной роли сервера **sysadmin** может также явно разрешить применение репликации для базы данных, чтобы член предопределенной роли базы данных **db_owner** мог создать в этой базе данных одну или несколько публикаций. Чтобы включить базу данных явным образом, используйте страницу **базы данных публикации** диалогового окна **свойства \<Publisher> издателя —** . Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [Create a Publication](publish/create-a-publication.md).  
  
### <a name="to-enable-a-database-for-replication"></a>Разрешение применения репликации для базы данных  
  
1.  На странице **базы данных публикации** диалогового окна **Свойства издателя \<Publisher> —** установите флажок **транзакционная** и/или **Слияние** для каждой базы данных, которую необходимо реплицировать. Установите флажок **Транзакционная** , чтобы разрешить для базы данных репликацию моментальных снимков.  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
