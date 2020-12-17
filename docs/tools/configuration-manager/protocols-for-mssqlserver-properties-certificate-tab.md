---
title: Протоколы для свойств MSSQLSERVER (вкладка «Сертификат»)
description: Выберите сертификат для SQL Server или просмотрите свойства сертификата с помощью вкладки "Сертификат" в диалоговом окне "Протоколы для свойств MSSQLSERVER".
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
f1_keywords:
- sql13.swb.computermgr.cert.general.f1
helpviewer_keywords:
- MSSQLSERVER property protocols
ms.assetid: 776addd6-25f3-4875-9a71-064035787090
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016'
ms.openlocfilehash: c7656957aa0a45b4456ae2e27408d3176dd0c5b6
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97463815"
---
# <a name="protocols-for-mssqlserver-properties-certificate-tab"></a>Протоколы для свойств MSSQLSERVER (вкладка «Сертификат»)
[!INCLUDE [SQL Server Windows Only - ASDBMI ](../../includes/applies-to-version/sql-windows-only-asdbmi.md)]
  Используйте вкладку **Сертификат** в диалоговом окне **Протоколы для свойств MSSQLSERVER**, чтобы выбрать сертификат для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]или просмотреть свойства сертификата. До выбора сертификата все поля остаются пустыми.  
  
 Сертификаты хранятся локально на пользовательских компьютерах. Чтобы загрузить сертификат для использования [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], необходимо запустить диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с той же учетной записью пользователя, что и служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="page-header"></a>Заголовок страницы  
 **View** (Вид)  
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
  
  
