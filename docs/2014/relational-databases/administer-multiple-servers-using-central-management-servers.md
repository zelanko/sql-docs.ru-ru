---
title: Администрирование нескольких серверов с использованием центральных серверов управления | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- multiserver queries
- central management server
- multiserver administration [SQL Server]
- master servers [SQL Server], central management servers
- target configuration [SQL Server]
- server configuration [SQL Server]
ms.assetid: 427911a7-57d4-4542-8846-47c3267a5d9c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f47eec543c21e74565d750035d20fbcee9baa82e
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877314"
---
# <a name="administer-multiple-servers-using-central-management-servers"></a>Администрирование нескольких серверов с использованием центральных серверов управления
  Можно администрировать сразу несколько серверов, назначив центральные серверы управления и создав группы серверов.  
  
## <a name="benefits-of-central-management-servers-and-server-groups"></a>Преимущества центральных серверов управления и групп серверов  
 Экземпляр [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], предназначенный для работы в качестве сервера центрального управления, обслуживает группы серверов, в которых содержатся сведения о соединении для одного или нескольких экземпляров [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] и политики управления на основе политик могут одновременно выполняться для всех групп серверов. Можно также просмотреть файлы журналов [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на экземплярах, управляемых через сервер централизованного управления. Версии [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ранее [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] нельзя назначить в качестве сервера централизованного управления.  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] также можно выполнить для локальных групп серверов в окне «Зарегистрированные серверы».  
  
### <a name="related-tasks"></a>Связанные задачи  
 Для создания сервера централизованного управления и групп серверов воспользуйтесь окном **Зарегистрированные серверы** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Обратите внимание, что сервер центрального управления не может быть членом группы, которую он обслуживает. Дополнительные сведения о создании центральных серверов управления и групп серверов см. в разделе [Создание центрального сервера управления и группы серверов (среда SQL Server Management Studio)](../ssms/register-servers/create-a-central-management-server-and-server-group.md).  
  
## <a name="see-also"></a>См. также  
 [Администрирование серверов с помощью управления на основе политик](policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
