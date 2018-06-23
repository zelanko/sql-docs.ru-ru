---
title: Виртуальный каталог использует неподдерживаемый метод проверки подлинности (Советник по переходу) | Документы Microsoft
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
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
caps.latest.revision: 13
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 1504b19f521258e2491626540baf49988d7605c4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36098114"
---
# <a name="virtual-directory-has-unsupported-authentication-method-upgrade-advisor"></a>Виртуальный каталог использует неподдерживаемый метод проверки подлинности (советник по переходу)
  Помощник по обновлению обнаружил неподдерживаемый метод проверки подлинности в виртуальном каталоге диспетчера отчетов или сервера отчетов. Обновлением не поддерживаются следующие методы проверки подлинности: анонимный доступ, дайджест-проверка подлинности и .NET Passport.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в основном режиме.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Программа установки не может обновить установку служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], где используется один из следующих методов проверки подлинности.  
  
-   Анонимная проверка подлинности  
  
-   Дайджест  
  
-   Пароль .NET  
  
 Чтобы продолжить установку, либо измените метод проверки подлинности, заданный в виртуальных каталогах IIS служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], либо выполните миграцию установки. Дополнительные сведения о миграции установки см. в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы продолжить обновление, измените метод проверки подлинности в службах IIS для виртуальных каталогов ReportServer и Reports. Дополнительные сведения об изменении методов проверки подлинности в службах IIS см. в документации по службам IIS. После изменения метода проверки подлинности для виртуальных директорий служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] повторно запустите помощник по обновлению, чтобы убедиться в отсутствии проблем обновления.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  