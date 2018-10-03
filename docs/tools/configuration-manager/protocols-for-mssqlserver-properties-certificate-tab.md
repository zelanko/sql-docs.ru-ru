---
title: Протоколы для свойств MSSQLSERVER (вкладка "Сертификат") | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql13.swb.computermgr.cert.general.f1
helpviewer_keywords:
- MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
author: stevestein
ms.author: sstein
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 85e7e9cbc454785379fac029cbe970a492e0fffd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47760102"
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a>Протоколы для свойств MSSQLSERVER (вкладка «Сертификат»)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  Используйте вкладку **Сертификат** диалогового окна **Протоколы для свойств MSSQLSERVER** , чтобы выбрать сертификат для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или просмотреть свойства сертификата. До выбора сертификата все поля остаются пустыми.  
  
 Сертификаты хранятся локально на пользовательских компьютерах. Чтобы загрузить сертификат для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо запустить диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с той же учетной записью пользователя, что и служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="page-header"></a>Заголовок страницы  
 **Вид**  
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
  
  
