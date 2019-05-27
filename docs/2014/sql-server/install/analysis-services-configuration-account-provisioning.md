---
title: Службы Analysis Services Настройка — Провизионирование учетных записей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services configuration
- account provisioning
ms.assetid: 169b1af2-6fe2-467f-8ca4-919f24c620ce
author: heidisteen
ms.author: heidist
manager: craigg
ms.openlocfilehash: 033c1ec1b0ad478e525f3ea9e8f172c5e5e31eef
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2019
ms.locfileid: "66096798"
---
# <a name="analysis-services-configuration---account-provisioning"></a>Настройка служб Analysis Services — провизионирование учетных записей
  На этой странице можно выбрать режим сервера и предоставить административные разрешения пользователям или службам, которым требуется неограниченный доступ к службам [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. Программа установки не добавляет автоматически локальную группу Windows BUILTIN\Администраторы в роль администратора сервера служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] устанавливаемого экземпляра. Если к роли администратора сервера требуется добавить локальную группу администраторов, необходимо явно указать эту группу.  
  
 При установке [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] необходимо предоставить административные разрешения администраторам ферм SharePoint или администраторам служб, отвечающим за развертывание сервера [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] в ферме [!INCLUDE[SPS2010](../../includes/sps2010-md.md)]. Дополнительные сведения о [!INCLUDE[ssGeminiMTS](../../includes/ssgeminimts-md.md)] установки и требования к учетной записи службы, см. в разделе [Установка компонентов SQL Server BI с SharePoint &#40;PowerPivot и служб Reporting Services&#41;](../../../2014/sql-server/install/install-sql-server-bi-features-sharepoint-powerpivot-reporting-services.md).  
  
## <a name="options"></a>Параметры  
 **Режим сервера**. Указывает тип баз данных служб Analysis Services, которые могут быть развернуты на сервере. Режимы сервера задаются во время установки, впоследствии изменить их будет невозможно. Каждый режим является взаимоисключающим, в силу чего необходимо будет установить два экземпляра служб Analysis Services, каждый из которых будет настроен для работы в другом режиме, чтобы обеспечить поддержку классических решений OLAP и табличных моделей.  
  
 **Определить администраторов** — для экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо указать хотя бы одного администратора сервера. Указанные пользователи или группы станут членами роли администратора сервера устанавливаемого экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. В домене, где зарегистрирован компьютер, на который выполняется установка программного обеспечения, должны иметься учетные записи пользователей домена Windows.  
  
> [!NOTE]  
>  Контроль учетных записей представляет собой средство безопасности Windows, которое требует, чтобы администратор явно одобрил административные действия или приложения, прежде чем будет разрешено их выполнение. Поскольку контроль учетных записей включен по умолчанию, администратор получает запрос на разрешение определенных операций, требующих более высокого уровня привилегий. Можно настроить контроль учетных записей, изменив поведение по умолчанию, или задать определенную конфигурацию для конкретных программ. Дополнительные сведения о контроле учетных записей и его настройке см. в материалах [Пошаговое руководство по контролю учетных записей](https://go.microsoft.com/fwlink/?linkid=196350) и [User Account Control (Wikipedia)](https://go.microsoft.com/fwlink/?linkid=196351).  
  
## <a name="see-also"></a>См. также  
 [Настройка учетных записей служб &#40;служб Analysis Services&#41;](../../../2014/analysis-services/instances/configure-service-accounts-analysis-services.md)   
 [Настройка учетных записей службы Windows и разрешений](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)  
  
  
