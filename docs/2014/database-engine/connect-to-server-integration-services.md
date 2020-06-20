---
title: Соединение с сервером (службы Integration Services) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.connection.login.dtsserver.f1
ms.assetid: 5be897bd-f36c-4c6a-a91a-13d0d016f8b6
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7b0d52d28440a92f79b08e90aff73b45fe643070
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84934655"
---
# <a name="connect-to-server-integration-services"></a>Соединение с сервером (службы Integration Services)
  Используйте это диалоговое окно для просмотра или настройки параметров при подключении к [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="options"></a>Параметры  
 **Тип сервера**  
 При регистрации сервера из обозревателя объектов выберите тип сервера для подключения: [!INCLUDE[ssDE](../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services. В остальной части диалогового окна показаны параметры, которые применяются только к выбранному типу сервера. При регистрации сервера в окне «Зарегистрированные серверы» поле «Тип сервера» доступно только для чтения и соответствует типу сервера, который выводится в компоненте «Зарегистрированные серверы». Чтобы зарегистрировать другой тип сервера, выберите компонент [!INCLUDE[ssDE](../includes/ssde-md.md)], службы Analysis Services, службы Reporting Services или службы Integration Services на панели инструментов «Зарегистрированные серверы», прежде чем начать регистрацию нового сервера.  
  
 **Имя сервера**  
 Выберите имя сервера для подключения. По умолчанию выводится экземпляр сервера, к которому подключение выполнялось в последний раз.  
  
> [!NOTE]  
>  Не используйте *\<servername>* \\ *\<instancename>* , поскольку не [!INCLUDE[ssIS](../includes/ssis-md.md)] поддерживает несколько экземпляров на компьютере.  
  
 **Аутентификация**  
 Для служб [!INCLUDE[msCoName](../includes/msconame-md.md)] доступна только проверка подлинности [!INCLUDE[ssIS](../includes/ssis-md.md)]Windows. Режим проверки подлинности Windows позволяет подключаться с учетной записью Windows.  
  
 **User name**  
 Этот параметр недоступен, поскольку для служб [!INCLUDE[ssIS](../includes/ssis-md.md)]возможен только режим проверки подлинности Windows.  
  
 **Пароль**  
 Этот параметр недоступен, поскольку для служб [!INCLUDE[ssIS](../includes/ssis-md.md)]возможен только режим проверки подлинности Windows.  
  
 **Подключить**  
 Нажмите, чтобы подключиться к выбранному выше серверу.  
  
 **Параметры**  
 Нажмите, чтобы вывести дополнительные параметры соединения с сервером, такие как регистрация сервера и запоминание пароля.  
  
  
