---
title: Удаление обновлений Майкрософт
description: Удаление обновлений Майкрософт в системе аналитики платформы (ТД).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: a5ebe1ee911f7500505cdbd1962d28c35461a635
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74399463"
---
# <a name="uninstall-microsoft-updates-in-analytics-platform-system"></a>Удаление обновлений Майкрософт в системе аналитики платформы
В этой статье описывается, как удалить ранее установленное обновление Майкрософт на устройстве аналитики системы.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>Предварительные требования  
Для выполнения этих действий потребуется:  
  
-   Вход в систему платформы аналитики с разрешениями на доступ к консоли администрирования для мониторинга устройства.  
  
-   Сведения об учетной записи администратора домена <em> <Fabric Domain> </em>структуры для входа на узел **-HST01** .  
  
## <a name="HowToUninstallMSFT"></a>Удаление обновлений Майкрософт  
  
1.  Войдите на <em> <Fabric Domain> </em>узел **-HST01** в качестве администратора домена структуры.  
  
2.  Чтобы удалить все обновления, утвержденные для удаления WSUS, откройте окно командной строки и введите следующую команду. Замените элементы заполнителя *<  >* соответствующими сведениями.  
  
    ```  
    C:\pdwinst\media\setup.exe /action="RemoveMicrosoftUpdate" /DomainAdminPasswords="<password>"  
    ```  
  
## <a name="next-steps"></a>Дальнейшие действия
Дополнительные сведения см. в разделе:
- [Загрузите и примените обновления Майкрософт &#40;&#41;платформы аналитики](download-and-apply-microsoft-updates.md) 
- [Применить исправления системы аналитики к системе &#40;Analytics Platform&#41;](apply-analytics-platform-system-hotfixes.md)  
- [Удаление исправлений системы аналитики &#40;Analytics Platform System&#41;](uninstall-analytics-platform-system-hotfixes.md)  
- [Система обслуживания программного обеспечения &#40;Analytics Platform&#41;](software-servicing.md)  
  
