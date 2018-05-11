---
title: Power Pivot минимальными правами пример – SharePoint 2016 | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e616b1aa6dd04d7488e23cfdfe76f41b819bf4
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="power-pivot-minimum-privilege-example---sharepoint-2016"></a>Power Pivot минимальными правами пример – SharePoint 2016
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  В этом разделе описывается пример настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2016 с минимальными правами доступа. В конфигурации используется отдельная учетная запись для каждого из трех компонентов и каждая учетная запись имеет минимальный уровень прав доступа.  
  
## <a name="summary-of-accounts"></a>Сводка учетных записей  
 [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2016 позволяет использовать учетную запись сетевой службы для учетной записи служб Analysis Services. Учетная запись сетевой службы не поддерживается в SharePoint 2010. Дополнительные сведения об учетных записях служб см. в разделе [Настройка учетных записей службы Windows и разрешений](http://msdn.microsoft.com/library/ms143504.aspx) (http://msdn.microsoft.com/library/ms143504.aspx).  
  
 В следующей таблице представлены три учетные записи, используемые в данном примере конфигурации с минимальными правами доступа.  
  
|Область действия|Название|  
|-----------|----------|  
|Учетная запись администратора SharePoint|**SPAdmin**|  
|Учетная запись фермы SharePoint|**SPFarm**|  
|Учетная запись службы Analysis Services|**SPsvc**|  
  
### <a name="the-sharepoint-administrator-account-spadmin"></a>Учетная запись администратора SharePoint (SpAdmin)  
 **SPAdmin** — учетная запись домена, используемая для установки и настройки фермы. Это учетная запись для запуска мастера настройки SharePoint и средства настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] для SharePoint 2016. Учетная запись **SPAdmin** — единственная запись, которая требует прав локального администратора. Перед запуском средства настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] предоставьте учетной записи **SPAdmin** права доступа к экземпляру базы данных SQL Server, где SharePoint формирует базы данных содержимого и конфигурации. Чтобы можно было настроить учетную запись SPAdmin с минимальными правами доступа, она должна быть членом ролей **securityadmin** и **dbcreator**.  
  
### <a name="the-farm-account-spfarm"></a>Учетная запись фермы (SPFarm)  
 **SPFarm** — учетная запись домена, используемая службой таймера SharePoint и веб-приложением для центра администрирования служб, чтобы получить доступ к базе данных содержимого SharePoint. Эта учетная запись не обязательно должна быть локальным администратором. Мастер настройки SharePoint предоставляет необходимые минимальные права доступа к внутренней базе данных SQL Server. Конфигурация SQL Server с минимальными правами доступа — членство в ролях **securityadmin** и **dbcreator**.  
  
### <a name="the-service-account-for-power-pivot-service-spsvc"></a>Учетная запись службы для службы PowerPivot (SPsvc)  
 Если новая ферма SharePoint не настроена перед запуском средства настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] , по умолчанию средство настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] создает:  
  
-   [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] Приложение службы.  
  
-   Приложение безопасного хранения.  
  
 Средство настройки [!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)] настраивает оба приложения службы в пуле приложений по умолчанию. Этот пул приложений обычно настроен для запуска с учетной записью SPFarm, которая имеет доступ ко многим ресурсам, ненужным учетной записи службы. Чтобы наделить среду минимальными правами, настройте новую учетную запись домена, которая будет использоваться соответствующим пулом приложений и веб-приложением.  
  
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
  
1.  Запустите консоль управления SharePoint 2016 с правом доступа администратора.  
  
2.  Выполните следующий код PowerShell:  
  
    ```  
    $webApp = Get-SPWebApplication "http://<servername>"  
    $webApp.GrantAccessToProcessIdentity("DOMAIN\<ServiceAccountName>")  
  
    ```  
  
  
