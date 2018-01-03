---
title: "Задайте пароль входа администратора AD узлы в режиме восстановления служб каталогов (APS)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97a9c715-2763-417d-b45c-bb0180759e47
caps.latest.revision: "20"
ms.openlocfilehash: 2e0379093db9364f45793adc20635bfa4ad53748
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2017
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm"></a>Задать пароль администратора для входа в систему узлов AD в режиме восстановления служб каталогов (DSRM)
Режим восстановления служб каталогов (DSRM) — это режим загрузки для восстановления в доменных службах Active Directory (AD DS). Он используется для входа на узлы устройств AD после неудачного AD DS или AD DS должны быть восстановлены. Пароль DSRM была инициализирована во время установки устройства на сайте поставщика оборудования и должны изменяться администратора устройства. Система платформы аналитики имеет два AD DS (контроллера домена);  ***appliance_domain*-AD01** и  ***appliance_domain*-AD02**. Для каждого узла устройства AD измените пароль DSRM, выполнив следующие действия.  
  
## <a name="HowToDSRM"></a>Чтобы сбросить пароль администратора  
  
1.  Откройте окно командной строки на узле устройства AD   ***appliance_domain*— AD*xx*** виртуальной машины.  
  
2.  В командной строке введите `ntdsutil`.  
  
3.  В **ntdsutil** , введите `set dsrm password`.  
  
4.  В **сброс пароля администратора:** , введите `reset password on server null`.  
  
5.  В командной строке введите новый пароль.  
  
6.  Повторите шаги 1 – 5 для каждой виртуальной машины AD устройства.  
  
    > [!WARNING]  
    > Система платформы аналитики не поддерживает символ доллара ($) пароль локального администратора или администратора домена. Пароль, содержащий символ доллара будет проверить и будет использовать но могут блокировать обновление и обслуживание действий.  
  
> [!NOTE]  
> Если для конкретной виртуальной машины AD поврежден виртуальной машины или доменных служб Active Directory, на котором запущен **ReplaceVM** для затронутых AD виртуальная машина — Рекомендуемое действие по исправлению. Обратитесь в службу поддержки пользователей обратитесь за помощью.  
  
## <a name="see-also"></a>См. также:  
[Сброс пароля &#40; Система платформы аналитики &#41;](password-reset.md)  
  
