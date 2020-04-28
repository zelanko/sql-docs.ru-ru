---
title: Удаление исправлений
description: Удалите исправления системы аналитики для платформы.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: ef6929aeb06c9472eb3ff210de016117a9636ded
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "74399764"
---
# <a name="uninstall-analytics-platform-system-hotfixes"></a>Удаление исправлений для системы аналитики платформы 
Ниже описаны действия по удалению ранее установленного исправления платформы аналитики.  
  
## <a name="before-you-begin"></a>Перед началом  
  
### <a name="prerequisites"></a>Предварительные требования  
Для выполнения этих действий потребуется:  
  
-   Вход в систему платформы аналитики с разрешениями на доступ к консоли администрирования для мониторинга устройства.  
  
-   Учетная запись администратора домена для входа на узел <em><appliance_domain></em> **-HST01** .  
  
-   Номер статьи базы знаний для удаляемого исправления.  
  
## <a name="to-uninstall-a-sql-server-pdw-hotfix"></a><a name="HowToUninstallPDW"></a>Удаление исправления SQL Server PDW  
  
1.  Войдите в <em><appliance_domain узел></em> **-HST01** в качестве администратора домена структуры.  
  
2.  Чтобы открыть командную строку, используйте команду Запуск от имени администратора.  
  
3.  Перейдите в `C:\PDWINST\Patches\<kbarticle>\media` каталог, *<kbarticle>* где — номер статьи базы знаний для удаляемого исправления.  
  
    ```  
    cd /d c:\PDWINST\Patches\<kbarticle>\media  
    ```  
  
4.  Чтобы удалить исправление, выполните следующую команду.  
  
    ```  
    setup.exe /action="removepatch" /DomainAdminPassword="<password>"  
    ```  
  
## <a name="see-also"></a>См. также:  
[Загрузите и примените обновления Майкрософт &#40;&#41;платформы аналитики](download-and-apply-microsoft-updates.md)  
[Удаление центра обновления Майкрософт &#40;система аналитики&#41;](uninstall-microsoft-updates.md)  
[Применить исправления системы аналитики к системе &#40;Analytics Platform&#41;](apply-analytics-platform-system-hotfixes.md)  
[Система обслуживания программного обеспечения &#40;Analytics Platform&#41;](software-servicing.md)  
  
