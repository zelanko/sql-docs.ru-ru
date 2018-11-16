---
title: Установка пароля Active Directory - Analytics Platform System | Документация Майкрософт
description: Задать пароль для входа администратора Active Directory узлы в режиме восстановления служб каталогов в Analytics Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: cd116bbb0305f56302f679881ef0a2a795739eb3
ms.sourcegitcommit: 0638b228980998de9056b177c83ed14494b9ad74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/14/2018
ms.locfileid: "51641401"
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>Задание пароля администратора для входа в систему узлы AD в службах каталогов восстановление (DSRM) - Analytics Platform System
Режим восстановления служб каталогов (DSRM) — это режим загрузки для восстановления в доменных службах Active Directory (AD DS). Он используется для входа на устройство AD узлы после сбоя AD DS или AD DS должны быть восстановлены. Пароль DSRM был инициализирован во время настройки устройства на сайте поставщика оборудования и следует изменять администратор устройства. Система Analytics Platform System имеет два AD DS (контроллеры домена);  **_appliance_domain_-AD01** и  **_appliance_domain_-AD02**. Для каждого узла устройства AD измените пароль DSRM, выполнив следующие действия.  
  
## <a name="HowToDSRM"></a>Чтобы сбросить пароль администратора  
  
1.  Откройте окно командной строки на узле устройство AD ***appliance_domain *— AD*xx***виртуальной машины.  
  
2.  В командной строке введите `ntdsutil`.  
  
3.  В **ntdsutil** , введите `set dsrm password`.  
  
4.  В **сброс пароля администратора:** , введите `reset password on server null`.  
  
5.  В командной строке введите новый пароль.  
  
6.  Повторите шаги 1 – 5 выше для каждой виртуальной машины AD устройства.  
  
    > [!WARNING]  
    > Система Analytics Platform System не поддерживает символ доллара ($) в администратора домена или локального администратора паролей. Пароль, содержащий знак доллара будут проверены и быть можно использовать но может блокировать обновление и обслуживание действия.  
  
> [!NOTE]  
> Если для конкретной виртуальной машины AD повреждения в доменных службах Active Directory или виртуальную машину под управлением **ReplaceVM** для затронутых AD виртуальная машина — Рекомендуемое действие по исправлению. Контактные CSS для получения помощи.  
  
## <a name="see-also"></a>См. также  
[Сброс пароля &#40;Analytics Platform System&#41;](password-reset.md)  
  
