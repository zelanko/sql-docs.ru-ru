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
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: craigg
ms.openlocfilehash: 2da05501cca599f3aa22e083d07424f54715cca9
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/10/2019
ms.locfileid: "67731277"
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
  
  
