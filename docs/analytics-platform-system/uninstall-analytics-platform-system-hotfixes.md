---
title: Удаление исправлений система платформы аналитики на | Документы Microsoft
description: Удаление исправлений Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 83e57a676ee0eff21eb3a736484d8e286cdeee01
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31538784"
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Удаление исправлений система платформы аналитики 
Следующие шаги описывают процесс удаления ранее установленных исправлений Analytics Platform System.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
Для выполнения этих действий, вам потребуется:  
  
-   Система платформы аналитики имени входа с разрешениями для доступа к консоли администрирования для мониторинга устройства.  
  
-   Учетной записи администратора домена выполнить вход на *< appliance_domain > ***-HST01** узла.  
  
-   Номер статьи базы знаний, для установки исправления для удаления.  
  
## <a name="HowToUninstallPDW"></a>Для удаления исправления SQL Server PDW  
  
1.  Выполните вход на *< appliance_domain > ***-HST01** узел администратора домена структуры.  
  
2.  Используйте запуска от имени администратора, чтобы открыть командную строку.  
  
3.  Перейдите к `C:\PDWINST\Patches\<kbarticle>\media` где *<kbarticle>* — номер статьи базы знаний для исправления для удаления.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Чтобы удалить исправление, выполните следующую команду.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>См. также  
[Загрузить и установить обновления Microsoft &#40;система платформы аналитики&#41;](download-and-apply-microsoft-updates.md)  
[Удаление обновлений &#40;система платформы аналитики&#41;](uninstall-microsoft-updates.md)  
[Применения исправлений системы платформы аналитики &#40;система платформы аналитики&#41;](apply-analytics-platform-system-hotfixes.md)  
[Обслуживание программного обеспечения &#40;система платформы аналитики&#41;](software-servicing.md)  
  
