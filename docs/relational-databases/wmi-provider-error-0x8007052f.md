---
title: "Ошибка WMI 0x8007052f | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: relational-databases-misc
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c036078af7bd9c0f90e5b2de6f1d73e74f62bc26
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="wmi-provider-error-0x8007052f"></a>Ошибка поставщика WMI 0x8007052f
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|0x8007052f|  
|Источник события|Ошибка поставщика WMI|  
|Компонент|Диспетчер конфигурации SQL Server|  
|Символическое имя|Н/Д|  
|Текст сообщения|Ошибка входа в систему: ограничение учетной записи. Возможные причины: запрещено использование пустых паролей, имеется ограничение по времени входа или применено ограничение, предусмотренное политикой.|  
  
## <a name="explanation"></a>Объяснение  
 Эта ошибка может произойти при использовании диспетчера конфигурации [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] для переключения на встроенные учетные записи (сетевой службы, локальной службы или локальной системы) в случаях, если [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] работает в кластере Windows Server или на контроллере домена Windows Server. Не запускайте службы от имени встроенных учетных записей в кластере Windows Server или на контроллере домена Windows Server. Дополнительные сведения об учетных записях см. в разделе «Настройка учетных записей служб Windows» электронной документации по [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
## <a name="user-action"></a>Действие пользователя  
 Настройте [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] на использование учетной записи домена.  
  
  
