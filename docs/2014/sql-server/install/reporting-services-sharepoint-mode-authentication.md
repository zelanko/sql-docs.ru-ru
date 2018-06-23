---
title: Проверка подлинности в режиме интеграции с SharePoint служб Reporting Services | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
caps.latest.revision: 8
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: 42a05beda30c678f97740a536e6b50530010bff1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189167"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>проверка подлинности служб Reporting Services в режиме SharePoint
  На странице **Проверка подлинности служб Reporting Services в режиме SharePoint** мастера установки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указываются учетные данные учетной записи службы, используемые в текущей установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Эти учетные данные будут использованы для создания нового пула приложений SharePoint. Кроме того, будет создано новое приложение службы SharePoint для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Имя приложения службы будет содержать имя предыдущего экземпляра [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
  
-   Параметр **Имя учетной записи пула приложений служб SSRS:** доступен только для чтения. Его значение автоматически заполняется текущим значением из существующей установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , обновление которой производится.  
  
-   Параметр **Пароль учетной записи пула приложений служб SSRS:** будет отключен, если эта учетная запись не требует пароля. Например, «NT Authority\NetworkSerivce». Если учетная запись пула приложений не требует пароля, то обновление нельзя будет продолжить до тех пор, пока не будет правильно введен пароль.  
  
 Дополнительные сведения см. в разделе [обновление и перенос служб Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628) (http://go.microsoft.com/fwlink/?LinkID=245628).  
  
## <a name="see-also"></a>См. также  
 [Обновление и перенос служб Reporting Services](http://go.microsoft.com/fwlink/?LinkID=245628)  
  
  