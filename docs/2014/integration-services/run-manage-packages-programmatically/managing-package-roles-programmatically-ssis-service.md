---
title: Программное управление ролями пакетов (служба SSIS) | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, roles
- roles [Integration Services]
- packages [Integration Services], roles
ms.assetid: 2e0ca0d5-d4f5-421d-b17d-a48b37b923e5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: e9ef79cf487044c9d3e07b0637d585c03daac0b4
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58385312"
---
# <a name="managing-package-roles-programmatically-ssis-service"></a>Программное управление ролями пакетов (служба SSIS)
  При программной работе с пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может потребоваться определить, какие роли доступны для пакетов, либо определить или задать роли для индивидуального пакета. Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> из пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет разнообразные методы, выполняющие эти требования.  
  
 Роли применимы только для пакетов, хранящихся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **msdb**. Дополнительные сведения о ролях пакетов см. в разделе [Роли служб Integration Services (службы SSIS)](../security/integration-services-roles-ssis-service.md).  
  
 Все методы, описываемые в этом разделе, должны ссылаться на сборку `Microsoft.SqlServer.ManagedDTS`. После добавления ссылки в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции `using` или `Imports`.  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только имена «.», localhost и имя сервера для локального сервера. Нельзя использовать имя «(local)».  
  
## <a name="determining-which-roles-are-available"></a>Определение доступных ролей  
 Чтобы определить, какие роли доступны для пакетов, хранящихся на конкретном сервере, вызовите метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetDtsServerRoles%2A> класса <xref:Microsoft.SqlServer.Dts.Runtime.Application>.  
  
## <a name="determining-which-roles-are-assigned"></a>Определение назначенных ролей  
 Чтобы определить, какие роли уже назначены определенному пакету, вызовите метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetPackageRoles%2A>. Чтобы назначить роли пакету, вызовите метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.SetPackageRoles%2A>.  
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Роли служб Integration Services (службы SSIS)](../security/integration-services-roles-ssis-service.md)  
  
  
