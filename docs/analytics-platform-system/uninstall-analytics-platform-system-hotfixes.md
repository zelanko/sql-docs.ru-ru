---
title: Удаление исправлений системы платформы аналитики (система платформы аналитики)
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
ms.assetid: c9ab596d-3f5a-48e2-bce7-c9be99b8c23b
caps.latest.revision: 21
ms.openlocfilehash: 56c6731d5a39741574999d94532b9505adaf6380
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Удаление исправлений системы платформы аналитики
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
  
