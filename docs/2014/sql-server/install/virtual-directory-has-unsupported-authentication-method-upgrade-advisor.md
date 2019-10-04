---
title: Виртуальный каталог имеет неподдерживаемый метод проверки подлинности (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- virtual directories [Reporting Services]
ms.assetid: 216eca6f-9a66-42e1-aa54-dcf99cec9f7d
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 26420df466860677f22d39d57133568a2f02bc68
ms.sourcegitcommit: ffe2fa1b22e6040cdbd8544fb5a3083eed3be852
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/04/2019
ms.locfileid: "71952012"
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
 [Советник по переходу Reporting Services проблем &#40;обновления&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
