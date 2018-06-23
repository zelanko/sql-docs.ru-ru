---
title: MSSQLSERVER_21893 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: bf6c8b8f2ad46c1874a2b46fb74ec46c67d634c7
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36190439"
---
# <a name="mssqlserver21893"></a>MSSQLSERVER_21893
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21893|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21893|  
|Текст сообщения|Подписчики ( %s ) исходного издателя «%s» не отображаются как удаленные серверы на перенаправленном издателе «%s». Запустите `sp_addlinkedserver` на перенаправленном издателе, чтобы добавить эти подписчики в качестве удаленных серверов.|  
  
## <a name="explanation"></a>Объяснение  
 `sp_validate_redirected_publisher` использует таблицы метаданных подписки в базе данных издателя на удаленном сервере, для определения связанных подписчиков и проверяет наличие связанных записей в master.dbo.sysservers для подписчиков. Эта ошибка возвращается, если отсутствует какой-либо из идентифицированных подписчиков.  
  
 Эта ошибка не считается неустранимой ошибкой. Агенты, на которых возникает эта ошибка, регистрируют в журнале информацию об ошибке, но не прерывают работу, так как невозможность найти соответствующие записи подписчиков на новом издателе не оказывает серьезного влияния на репликацию. Если для подписчика нет соответствующей записи в sysservers, некоторые операции по управлению подпиской могут завершаться ошибкой при вызове через [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Однако те же операции можно успешно выполнять путем явного вызова хранимых процедур управления.  
  
## <a name="user-action"></a>Действие пользователя  
 Запустите `sp_addlinkedserver` на перенаправленном издателе для каждого из обнаруженных подписчиков, чтобы добавить их в качестве удаленных серверов. Затем запустите `sp_serveroption`, чтобы установить бит подписчика для сервера.  
  
  