---
title: "Администрирование нескольких серверов с использованием центральных серверов управления | Документация Майкрософт"
ms.custom: 
ms.date: 08/12/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 96c7ee447ddb7b353bebaa67d20f134bcb222d6b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="administer-multiple-servers-using-central-management-servers"></a>Администрирование нескольких серверов с использованием центральных серверов управления
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Вы можете администрировать сразу несколько серверов, назначив центральные серверы управления и создав группы серверов.  
  
## <a name="what-is-a-central-management-server-and-server-groups"></a>Что такое центральный сервер управления и группы серверов?  
 Экземпляр SQL Server, предназначенный для работы в качестве центрального сервера управления, обслуживает группы серверов, в которых содержатся сведения о соединении для одного или нескольких экземпляров. Инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] и политики управления на основе политик можно выполнять для групп серверов одновременно. Можно также просмотреть файлы журналов на экземплярах, управляемых через центральный сервер управления. 
 
 По сути, центральный сервер управления представляет собой центральный репозиторий, содержащий список управляемых серверов. Версии ранее [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] нельзя назначить в качестве центрального сервера управления.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] также можно выполнить для локальных групп серверов в окне «Зарегистрированные серверы».  
  
## <a name="create-central-management-server-and-server-groups"></a>Создание центрального сервера управления и групп серверов 
 Для создания сервера централизованного управления и групп серверов воспользуйтесь окном **Зарегистрированные серверы** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Обратите внимание, что сервер центрального управления не может быть членом группы, которую он обслуживает. 
 
 Дополнительные сведения о создании центральных серверов управления и групп серверов см. в разделе [Создание центрального сервера управления и группы серверов &#40;среда SQL Server Management Studio&#41;](../tools/sql-server-management-studio/create-a-central-management-server-and-server-group.md).  
  
## <a name="see-also"></a>См. также:  
 [Администрирование серверов с помощью управления на основе политик](../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
