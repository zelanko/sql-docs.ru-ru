---
title: "Протоколы для свойств MSSQLSERVER (вкладка «сертификат») | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: configuration-manager
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.swb.computermgr.cert.general.f1
helpviewer_keywords: MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
caps.latest.revision: "17"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 811489d75af39d9b7cd33eb3f8aaadec5ae045cf
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a>Протоколы для свойств MSSQLSERVER (вкладка «Сертификат»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]Используйте **сертификат** на вкладке **протоколы для свойств MSSQLSERVER** диалоговое окно «», чтобы выбрать сертификат для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], или просмотреть свойства сертификата. До выбора сертификата все поля остаются пустыми.  
  
 Сертификаты хранятся локально на пользовательских компьютерах. Чтобы загрузить сертификат для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо запустить диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с той же учетной записью пользователя, что и служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="page-header"></a>Заголовок страницы  
 **Просмотр**  
 Обеспечивает доступ к дополнительным данным сертификата. Недоступно до тех пор, пока сертификат не выбран в поле **Сертификат** . Дополнительные сведения о данных сертификата см. в документации по [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Clear**  
 Отменяет выбор в поле **Сертификат** .  
  
 **Сертификат**  
 Имя сертификата определяется поставщиком безопасности. Выберите сертификат, чтобы просмотреть данные в сетке свойств.  
  
## <a name="options"></a>Параметры  
 Срок действия  
 Дата окончания периода, в течение которого сертификат действителен.  
  
 Понятное имя  
 Понятное или общее имя для физического лица или центра сертификации, которому выдан сертификат.  
  
 Кем выдан  
 Сведения, относящиеся к центру сертификации, выдавшему сертификат.  
  
 Кому выдан  
 Сведения, относящиеся к получателю сертификата.  
  
  
