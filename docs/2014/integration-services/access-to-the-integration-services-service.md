---
title: Доступ к интеграции службы служб | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- SSIS packages, security
- viewing packages while running
- displaying packacges while running
- security [Integration Services], running packages
- packages [Integration Services], security
- current packages running
- Integration Services packages, security
- SQL Server Integration Services packages, security
ms.assetid: 1088aafc-14c5-4e7d-9930-606a24c3049b
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 7e9baff13c2bc368557a49b4509c6e48a444d583
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132124"
---
# <a name="access-to-the-integration-services-service"></a>Доступ к службам Integration Services
  Уровни защиты пакетов могут ограничивать круг пользователей, которым разрешается изменять и выполнять пакет. Дополнительная защита требуется для ограничения круга пользователей, которым разрешается просматривать список пакетов, выполняющихся в данный момент на сервере, и останавливать выполнение пакетов в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
 Для перечисления выполняемых пакетов среда [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] использует службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Члены группы «Администраторы» Windows могут просматривать и останавливать все выполняемые в текущее время пакеты. Пользователи, не являющиеся членами группы «Администраторы», могут просматривать и останавливать только пакеты, запущенные ими самими.  
  
 Важно ограничить доступ к компьютерам, на которых запущены службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , особенно службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , которые могут перечислить удаленные папки. Любой пользователь, прошедший проверку подлинности, может запрашивать перечисление пакетов. Даже если служба не находит службу, служба перечисляет папки. Имена папок могут оказаться полезными сведениями для злоумышленника. Если администратор настроил службу для перечисления папок на удаленном компьютере, пользователи также смогут увидеть имена, которые они в действительности не должны были видеть.  
  
  
