---
title: Reporting Services проверки подлинности в режиме интеграции с SharePoint | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade SharePoint Mode [Reporting Services]
- SharePoint integration
- SharePoint Mode
ms.assetid: 2c19794a-dd55-4fe5-b901-6dd93e9f6beb
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: ff0a4f38bf9ee7d9c27fbc07308084ed3272f95d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952100"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>проверка подлинности служб Reporting Services в режиме SharePoint
  На странице **Проверка подлинности служб Reporting Services в режиме SharePoint** мастера установки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указываются учетные данные учетной записи службы, используемые в текущей установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Эти учетные данные будут использованы для создания нового пула приложений SharePoint. Кроме того, будет создано новое приложение службы SharePoint для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Имя приложения службы будет содержать имя предыдущего экземпляра [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Параметры  
  
-   Параметр **Имя учетной записи пула приложений служб SSRS:** доступен только для чтения. Его значение автоматически заполняется текущим значением из существующей установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , обновление которой производится.  
  
-   Параметр **Пароль учетной записи пула приложений служб SSRS:** будет отключен, если эта учетная запись не требует пароля. Например, "NT Authority\NetworkService". Если учетная запись пула приложений не требует пароля, то обновление нельзя будет продолжить до тех пор, пока не будет правильно введен пароль.  
  
 Дополнительные сведения см. в разделе [обновление и миграция Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) (https://go.microsoft.com/fwlink/?LinkID=245628).  
  
## <a name="see-also"></a>См. также:  
 [Upgrade and Migrate Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
