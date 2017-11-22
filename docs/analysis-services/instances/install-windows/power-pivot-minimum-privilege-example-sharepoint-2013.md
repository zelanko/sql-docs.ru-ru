---
title: "Power Pivot минимальными правами пример – SharePoint 2013 | Документы Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: instances
ms.reviewer: 
ms.suite: sql
ms.technology: setup-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1e09e6c-52d3-48ab-8c70-818d5d775087
caps.latest.revision: "12"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 96d0bc028312b4bfcaa0e5fbf9932d77881c087b
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="power-pivot-minimum-privilege-example---sharepoint-2013"></a>Power Pivot минимальными правами пример – SharePoint 2013
  В этом разделе описывается пример настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2013 с минимальными правами доступа. В конфигурации используется отдельная учетная запись для каждого из трех компонентов и каждая учетная запись имеет минимальный уровень прав доступа.  
  
||  
|-|  
|**[!INCLUDE[applies](../../../includes/applies-md.md)]**  SharePoint 2013|  
  
## <a name="summary-of-accounts"></a>Сводка учетных записей  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2013 позволяет использовать учетную запись сетевой службы для учетной записи служб Analysis Services. Учетная запись сетевой службы не поддерживается в SharePoint 2010. Дополнительные сведения об учетных записях службы см. в разделе [Настройка учетных записей службы Windows и разрешений](http://msdn.microsoft.com/library/ms143504.aspx) (http://msdn.microsoft.com/library/ms143504.aspx).  
  
 В следующей таблице представлены три учетные записи, используемые в данном примере конфигурации с минимальными правами доступа.  
  
|Область действия|Название|  
|-----------|----------|  
|Учетная запись администратора SharePoint|**SPAdmin**|  
|Учетная запись фермы SharePoint|**SPFarm**|  
|Учетная запись службы Analysis Services|**SPsvc**|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a>Учетная запись администратора SharePoint (SpAdmin)  
 **SPAdmin** — учетная запись домена, используемая для установки и настройки фермы. Это учетная запись для запуска мастера настройки SharePoint и средства настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2013. Учетная запись **SPAdmin** — единственная запись, которая требует прав локального администратора. Перед запуском средства настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] предоставьте учетной записи **SPAdmin** права доступа к экземпляру базы данных SQL Server, где SharePoint формирует базы данных содержимого и конфигурации. Чтобы можно было настроить учетную запись SPAdmin с минимальными правами доступа, она должна быть членом ролей **securityadmin** и **dbcreator**.  
  
### <a name="the-farm-account-spfarm"></a>Учетная запись фермы (SPFarm)  
 **SPFarm** — учетная запись домена, используемая службой таймера SharePoint и веб-приложением для центра администрирования служб, чтобы получить доступ к базе данных содержимого SharePoint. Эта учетная запись не обязательно должна быть локальным администратором. Мастер настройки SharePoint предоставляет необходимые минимальные права доступа к внутренней базе данных SQL Server. Конфигурация SQL Server с минимальными правами доступа — членство в ролях **securityadmin** и **dbcreator**.  
  
### <a name="the-service-account-for-power-pivot-service-spsvc"></a>Учетная запись службы для службы PowerPivot (SPsvc)  
 Если новая ферма SharePoint не настроена перед запуском средства настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , по умолчанию средство настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] создает:  
  
-   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Приложение службы.  
  
-   Приложение службы Excel.  
  
-   Приложение безопасного хранения.  
  
 Средство настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] настраивает все три приложения службы в пуле приложений по умолчанию. Этот пул приложений обычно настроен для запуска с учетной записью SPFarm, которая имеет доступ ко многим ресурсам, ненужным учетной записи службы. Чтобы наделить среду минимальными правами, настройте новую учетную запись домена, которая будет использоваться соответствующим пулом приложений и веб-приложением.  
  
 **Чтобы создать новую учетную запись домена SPsvc, которая будет использоваться в качестве учетной записи службы SharePoint:**  
  
1.  В центре администрирования SharePoint выберите **Безопасность**.  
  
2.  Выберите **Настройка учетных записей служб**.  
  
3.  Выберите **Регистрация новой управляемой учетной записи**.  
  
 Учетная запись **SPSvc** не имеет прав доступа локального администратора, и SPsvc не будет иметь никаких прав в базе данных SharePoint. Единственные права доступа, необходимые SPsvc, — права администратора для экземпляра [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] служб Analysis Services.  
  
 **Чтобы настроить соответствующий пул приложений для использования учетной записи SPsvc:**  
  
1.  В центре администрирования SharePoint выберите **Безопасность**.  
  
2.  Выберите **Настройка учетных записей служб**.  
  
3.  Выберите пул приложений служб, используемый приложением службы [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] . Выберите учетную запись SPSvc.  
  
 **Чтобы предоставить доступ к веб-приложению с PowerShell:**  
  
1.  Запустите консоль управления SharePoint 2013 с правом доступа администратора.  
  
2.  Выполните следующий код PowerShell:  
  
    ```  
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")  
  
    ```  
  
  
