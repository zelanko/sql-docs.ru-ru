---
title: Соединение с сервером (страница "Имя входа") службы Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connecttodtsserver.login.f1
- sql12.swb.connecttodts.login.f1
ms.assetid: 402c2de4-f4ea-40b0-909f-3ddf3bd59950
caps.latest.revision: 23
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 95eac72a39ec2d110411fbae2d2494108e5cff41
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43812400"
---
# <a name="connect-to-server-login-page-integration-services"></a>Соединение с сервером (страница «Имя входа») службы Integration Services
  Используйте эту вкладку для просмотра или задания следующих параметров при соединении со службами [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Тип сервера**  
 При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера c панели "Зарегистрированные серверы" поле **Тип сервера** не может быть изменено и совпадает с типом сервера, показанного в компоненте "Зарегистрированные серверы". Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
 **Имя сервера**  
 Выберите имя сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
> [!NOTE]  
>  Не используйте  *\<servername >*\\*\<instancename >*, так как [!INCLUDE[ssIS](../includes/ssis-md.md)] не поддерживают несколько экземпляров на одном компьютере.  
  
 **Проверка подлинности**  
 Для служб [!INCLUDE[msCoName](../includes/msconame-md.md)] доступна только проверка подлинности [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows. Режим проверки подлинности Windows позволяет подключаться с учетной записью Windows.  
  
 **Имя пользователя**  
 Этот параметр недоступен, поскольку для служб [!INCLUDE[ssIS](../includes/ssis-md.md)]возможен только режим проверки подлинности Windows.  
  
 **Пароль**  
 Этот параметр недоступен, поскольку для служб [!INCLUDE[ssIS](../includes/ssis-md.md)]возможен только режим проверки подлинности Windows.  
  
 **Запомнить пароль**  
 Этот параметр недоступен, поскольку для служб [!INCLUDE[ssIS](../includes/ssis-md.md)]возможен только режим проверки подлинности Windows.  
  
 **Подключить**  
 Подключиться к выбранному выше серверу.  
  
 **Параметры**  
 Выберите этот пункт, чтобы изменить диалоговое окно и скрыть такие дополнительные параметры соединения сервера, как запоминание пароля.  
  
  
