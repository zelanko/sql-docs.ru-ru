---
title: Удаление обновления Майкрософт — Analytics Platform System | Документы Microsoft»
description: Удаление обновлений в Analytics Platform System (APS).
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 57d0eb3616cf3567f63d75029f79cea6709ed955
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Удаление обновлений Майкрософт в система платформы аналитики
В этой статье описан процесс удаления ранее установленного обновления Майкрософт на устройстве, Analytics Platform System.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
Для выполнения этих действий, вам потребуется:  
  
-   Система платформы аналитики имени входа с разрешениями для доступа к консоли администрирования для мониторинга устройства.  
  
-   Знание учетной записи администратора домена структуры для входа в  *<Fabric Domain>***-HST01** узла.  
  
## <a name="HowToUninstallMSFT"></a>Удаление обновлений Майкрософт  
  
1.  Войдите на  *<Fabric Domain>***-HST01** узел администратора домена структуры.  
  
2.  Чтобы удалить все обновления, утвержденные для служб WSUS удалить, откройте окно командной строки и введите следующую команду. Заменить местозаполнитель элементы *< >* соответствующие сведения.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>Следующие шаги
Дополнительные сведения см. в разделе:
- [Загрузить и установить обновления Microsoft &#40;система платформы аналитики&#41;](download-and-apply-microsoft-updates.md) 
- [Применения исправлений системы платформы аналитики &#40;система платформы аналитики&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Удаление исправлений системы платформы аналитики &#40;система платформы аналитики&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [Обслуживание программного обеспечения &#40;система платформы аналитики&#41;](software-servicing.md)  
  
