---
title: Разработка пользовательского интерфейса для пользовательского регистратора | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3834457421187b8186042e169e939c76bfa6e05d
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2019
ms.locfileid: "58376762"
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a>Разработка пользовательского интерфейса для пользовательского регистратора
  Многие регистраторы служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеют собственный пользовательский интерфейс, в котором реализован интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>, а вместо содержимого текстового поля **Конфигурация** в диалоговом окне **Настройка журналов служб SSIS** используется фильтруемый раскрывающийся список доступных диспетчеров соединений. Однако пользовательские интерфейсы для пользовательских регистраторов не реализуются в службах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
![Значок служб Integration Services (маленький)](../../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться до даты со службами Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательского регистратора](creating-a-custom-log-provider.md)   
 [Создание кода пользовательского регистратора](coding-a-custom-log-provider.md)  
  
  
