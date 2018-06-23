---
title: База данных сервера отчетов не настроена (Советник по переходу) | Документы Microsoft
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
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
caps.latest.revision: 14
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: f86e9963750d2bacbdc55e235e4975a05c2f625e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109855"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>База данных сервера отчетов настроена (советник по переходу)
  Обновление заблокировано в связи с тем, что настройка сервера отчетов не завершена. База данных сервера отчетов не настроена.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Собственный режим &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Описание  
 Программа обновления может обновить только полностью настроенный экземпляр сервера отчетов. Чтобы продолжить, необходимо настроить базу данных сервера отчетов, либо использовать Microsoft Windows **панели управления** для удаления сервера отчетов из [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки. После удаления служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] можно произвести обновление других компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если база данных сервера отчетов не была настроена, сервер отчетов находится в нерабочем состоянии и должен быть удален до обновления.  
  
 Дополнительные сведения об удалении [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , в разделе [удаление служб Reporting Services 2012](http://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)). в разделе описывается удаление конкретной версии. Эта процедура похожа на ту, которая была в предыдущих версиях.  
  
## <a name="see-also"></a>См. также  
 [Проблемы обновления служб Reporting Services &#40;помощник по обновлению&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  