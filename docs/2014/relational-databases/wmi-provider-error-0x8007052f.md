---
title: Ошибка WMI 0x8007052f | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- 0x8007052f (WMI error)
ms.assetid: a33f12bd-15c4-42a8-b343-de44c3e87729
caps.latest.revision: 9
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d9fd50d33dbcc60cddf03a04d439f3b8630152a5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "35999960"
---
# <a name="wmi-error-0x8007052f"></a>WMI Error 0x8007052f
    
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
  
  