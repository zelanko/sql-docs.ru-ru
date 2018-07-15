---
title: Требования к учетной записи для обновления до SQL Server 2008 на контроллере домена службы | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- domain controllers
- service accounts
- network service accounts
- local service accounts
ms.assetid: 574245b6-11e2-4849-b0ca-836d673ecd0d
caps.latest.revision: 16
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9cc2ec39bee7f9a64d75ccf4753220f69693155b
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37301664"
---
# <a name="service-account-requirements-for-upgrading-to-sql-server-2008-on-a-domain-controller"></a>Требования к учетной записи службы для обновления до SQL Server 2008 на контроллере домена
  Советник по переходу обнаружил экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под учетной записью Network Service или Local Service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] контроллера домена. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на контроллере домена [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] службы [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не могут выполняться с правами доступа учетной записи Local Service или Network Service.  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Убедитесь, что все учетные записи служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] назначены учетным записям домена или локальной системы. Если этого не сделать перед обновлением, процесс установки будет заблокирован. Исключениями являются учетные записи службы SQL Writer, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и службы поддержки Active Directory, так как в них использование учетной записи сетевой службы жестко закодировано и не может быть изменено.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления компонента Database Engine](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Помощник по обновлению SQL Server 2014 &#91;new&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
