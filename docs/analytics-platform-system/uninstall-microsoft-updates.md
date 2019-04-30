---
title: Удаление обновлений - Analytics Platform System | Документация по Microsoft»
description: Удаление обновлений в Analytics Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 4739d05b1878c8b7fc9f66f2e0b8145ff1044e54
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63243828"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Удаление обновлений в Analytics Platform System
В этой статье описан процесс удаления ранее установленного обновления Майкрософт на устройстве, Analytics Platform System.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
Чтобы выполнить эти действия, вам потребуется:  
  
-   Система Analytics Platform System имя входа с разрешениями для доступа к консоли администрирования для мониторинга устройства.  
  
-   Знания домена администратор структуры учетной записи для входа в <em> <Fabric Domain> </em> **-HST01** узла.  
  
## <a name="HowToUninstallMSFT"></a>Удаление обновлений Майкрософт  
  
1.  Войдите в <em> <Fabric Domain> </em> **-HST01** узел администратора домена Fabric.  
  
2.  Чтобы удалить все обновления, утвержденные для служб WSUS для удаления, откройте окно командной строки и введите следующую команду. Замените заполнитель элементы *< >* соответствующими сведениями.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения см. в разделе:
- [Скачивание и применение обновлений Майкрософт &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md) 
- [Примените обновления системы платформы аналитики &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Удаление исправлений системы платформы аналитики &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [Обслуживание программного обеспечения &#40;Analytics Platform System&#41;](software-servicing.md)  
  
