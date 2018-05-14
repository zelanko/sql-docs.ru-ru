---
title: MSSQLSERVER_21893 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
caps.latest.revision: 6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: c3e26e6386461aa04b6819d302035536e8a80b02
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="mssqlserver21893"></a>MSSQLSERVER_21893
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21893|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21893|  
|Текст сообщения|Подписчики ( %s ) исходного издателя «%s» не отображаются как удаленные серверы на перенаправленном издателе «%s». Запустите **sp_addlinkedserver** на перенаправленном издателе, чтобы добавить этих подписчиков в качестве удаленных серверов.|  
  
## <a name="explanation"></a>Объяснение  
**sp_validate_redirected_publisher** использует таблицы метаданных подписки в базе данных издателя на удаленном сервере для определения связанных подписчиков, а также проверяет наличие связанных записей в таблице master.dbo.sysservers для подписчиков. Эта ошибка возвращается, если отсутствует какой-либо из идентифицированных подписчиков.  
  
Эта ошибка не считается неустранимой ошибкой. Агенты, на которых возникает эта ошибка, регистрируют в журнале информацию об ошибке, но не прерывают работу, так как невозможность найти соответствующие записи подписчиков на новом издателе не оказывает серьезного влияния на репликацию. Если для подписчика нет соответствующей записи в sysservers, некоторые операции по управлению подпиской могут завершаться ошибкой при вызове через [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Однако те же операции можно успешно выполнять путем явного вызова хранимых процедур управления.  
  
## <a name="user-action"></a>Действие пользователя  
Запустите **sp_addlinkedserver** в перенаправленном издателе для каждого из обнаруженных подписчиков, чтобы добавить их в качестве удаленных серверов. Затем запустите **sp_serveroption**, чтобы установить бит подписчика для сервера.  
  
