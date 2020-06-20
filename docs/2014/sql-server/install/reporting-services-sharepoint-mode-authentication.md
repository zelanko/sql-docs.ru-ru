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
ms.openlocfilehash: 3b1316a1a49726ab0754f39160125425fec116d4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85059015"
---
# <a name="reporting-services-sharepoint-mode-authentication"></a>проверка подлинности служб Reporting Services в режиме SharePoint
  На странице **Проверка подлинности служб Reporting Services в режиме SharePoint** мастера установки [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] указываются учетные данные учетной записи службы, используемые в текущей установке служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Эти учетные данные будут использованы для создания нового пула приложений SharePoint. Кроме того, будет создано новое приложение службы SharePoint для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] . Имя приложения службы будет содержать имя предыдущего экземпляра [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
## <a name="options"></a>Варианты  
  
-   Параметр **Имя учетной записи пула приложений служб SSRS:** доступен только для чтения. Его значение автоматически заполняется текущим значением из существующей установки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , обновление которой производится.  
  
-   Параметр **Пароль учетной записи пула приложений служб SSRS:** будет отключен, если эта учетная запись не требует пароля. Например, "NT Authority\NetworkService". Если учетная запись пула приложений не требует пароля, то обновление нельзя будет продолжить до тех пор, пока не будет правильно введен пароль.  
  
 Дополнительные сведения см. в разделе [обновление и миграция Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628) ( https://go.microsoft.com/fwlink/?LinkID=245628) .  
  
## <a name="see-also"></a>См. также:  
 [Обновление и перенос служб Reporting Services](https://go.microsoft.com/fwlink/?LinkID=245628)  
  
  
