---
title: Разработка пользовательского интерфейса для пользовательского регистратора | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.component: extending-packages-custom-objects
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom user interface [Integration Services], custom log providers
- custom log providers [Integration Services], developing custom user interface
ms.assetid: 6fd2d269-d87a-4134-82a1-40a09b3b5453
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c9705b17884585ab43b8f4848a19ee44140e39ea
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="developing-a-user-interface-for-a-custom-log-provider"></a>Разработка пользовательского интерфейса для пользовательского регистратора
  Многие регистраторы служб [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] имеют собственный пользовательский интерфейс, в котором реализован интерфейс <xref:Microsoft.SqlServer.Dts.Runtime.Design.IDtsLogProviderUI>, а вместо содержимого текстового поля **Конфигурация** в диалоговом окне **Настройка журналов служб SSIS** используется фильтруемый раскрывающийся список доступных диспетчеров соединений. Однако пользовательские интерфейсы для пользовательских регистраторов не реализуются в службах [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Создание пользовательского регистратора](../../../integration-services/extending-packages-custom-objects/log-provider/creating-a-custom-log-provider.md)   
 [Создание кода пользовательского регистратора](../../../integration-services/extending-packages-custom-objects/log-provider/coding-a-custom-log-provider.md)  
  
  
