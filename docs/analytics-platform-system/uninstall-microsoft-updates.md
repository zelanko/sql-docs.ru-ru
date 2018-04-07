---
title: Удаление обновлений (система платформы аналитики)
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.technology: mpp-data-warehouse
ms.custom: ''
ms.date: 01/05/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: df61570a-210d-4154-822f-98acd721f075
caps.latest.revision: 19
ms.openlocfilehash: b428cdacefefa96cdd5c500d34225c6963f5cb1f
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="uninstall-microsoft-updates"></a>Удаление обновлений
В этом разделе описывается удаление ранее установленного обновления Майкрософт на устройстве, Analytics Platform System.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
Для выполнения этих действий, вам потребуется:  
  
-   Система платформы аналитики имя входа с разрешениями для доступа к консоли администрирования для мониторинга устройства.  
  
-   Знание учетную запись администратора домена структуры, чтобы войти в  *<Fabric Domain>***-HST01** узла.  
  
## <a name="HowToUninstallMSFT"></a>Удаление обновлений Майкрософт  
  
1.  Имя входа для  *<Fabric Domain>***-HST01** узел администратора домена структуры.  
  
2.  Чтобы удалить все обновления, утвержденные для служб WSUS удалить, откройте окно командной строки и введите следующую команду. Заменить местозаполнитель элементы *< >* соответствующие сведения.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="see-also"></a>См. также  
[Загрузить и установить обновления Microsoft &#40;система платформы аналитики&#41;](download-and-apply-microsoft-updates.md)  
[Применения исправлений системы платформы аналитики &#40;система платформы аналитики&#41;](apply-analytics-platform-system-hotfixes.md)  
[Удаление исправлений системы платформы аналитики &#40;система платформы аналитики&#41;](uninstall-analytics-platform-system-hotfixes.md)  
[Обслуживание программного обеспечения &#40;система платформы аналитики&#41;](software-servicing.md)  
  
