---
title: Удаление исправлений Analytics Platform System | Документация Майкрософт
description: Удаление исправлений Analytics Platform System.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 5507eae7bb2f8a5ce138223a031ac4946d9f0030
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62675674"
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Удаление исправлений Analytics Platform System 
Следующие шаги содержат описание удаления ранее установленных исправлений Analytics Platform System.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>предварительные требования  
Чтобы выполнить эти действия, вам потребуется:  
  
-   Система Analytics Platform System имя входа с разрешениями для доступа к консоли администрирования для мониторинга устройства.  
  
-   Учетной записи администратора домена выполнить вход в <em>< appliance_domain ></em> **-HST01** узла.  
  
-   Номер статьи базы знаний, исправления для удаления.  
  
## <a name="HowToUninstallPDW"></a>Чтобы удалить исправление SQL Server PDW  
  
1.  Выполните вход на <em>< appliance_domain ></em> **-HST01** узел администратора домена Fabric.  
  
2.  Открыть командную строку с помощью запуска от имени администратора.  
  
3.  Перейдите в каталог `C:\PDWINST\Patches\<kbarticle>\media` где *<kbarticle>* — номер статьи базы знаний для исправления для удаления.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Чтобы удалить исправление, выполните следующую команду.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>См. также  
[Скачивание и применение обновлений Майкрософт &#40;Analytics Platform System&#41;](download-and-apply-microsoft-updates.md)  
[Удаление обновлений &#40;Analytics Platform System&#41;](uninstall-microsoft-updates.md)  
[Примените обновления системы платформы аналитики &#40;Analytics Platform System&#41;](apply-analytics-platform-system-hotfixes.md)  
[Обслуживание программного обеспечения &#40;Analytics Platform System&#41;](software-servicing.md)  
  
