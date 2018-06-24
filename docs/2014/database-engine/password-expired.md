---
title: Срок действия пароля истек | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.passwordexpired.f1
helpviewer_keywords:
- Password Expired dialog box
ms.assetid: 9831b194-9ad5-47b0-8009-59c7aef4319b
caps.latest.revision: 22
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6b065bcf5e973c00b24398226510801e333181f9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195429"
---
# <a name="password-expired"></a>Срок действия пароля истек
  Появляется при соединении с сервером, на котором установлена среда [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и который использует проверку подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , если введен верный пароль, срок действия которого истек. Также появляется при соединении с сервером с применением новой учетной записи, созданной при помощи параметра **Пользователь должен сменить пароль при следующем входе в систему** . Используйте диалоговое окно **Срок действия пароля истек** , чтобы сменить пароль для этого имени входа с проверкой подлинности [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
 **Имя входа**  
 Отображает используемое имя входа [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 **Новый пароль**  
 Введите новый пароль для этого имени входа.  
  
 **Подтвердите пароль**  
 Еще раз введите новый пароль для подтверждения.  
  
## <a name="see-also"></a>См. также  
 [Надежные пароли](../relational-databases/security/strong-passwords.md)   
 [Выбор режима проверки подлинности](../relational-databases/security/choose-an-authentication-mode.md)   
 [Изменение режима проверки подлинности сервера](configure-windows/change-server-authentication-mode.md)   
 [Изменение пароля учетных записей, используемых SQL Server (диспетчер конфигурации SQL Server)](configure-windows/scm-services-change-the-password-of-the-accounts-used.md)  
  
  