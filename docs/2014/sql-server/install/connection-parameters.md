---
title: Параметры подключения | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca5d6ed8f1e8a92d22bd32e39c8afe946a0fcfee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66095981"
---
# <a name="connection-parameters"></a>Параметры подключения
  Для анализа определенных типов сервера, таких как [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], необходимо выбрать конкретный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Автоматически выбирается экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию. Этот выбор можно изменить, однако советник по переходу одновременно может выполнять анализ только одного экземпляра. Если выбран тип сервера, требующий проверки подлинности, необходимо указать режим проверки подлинности и ввести учетные данные.  
  
## <a name="options"></a>Параметры  
 **Имя сервера**  
 Заранее заданное имя компьютера, введенное на панели «Компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]».  
  
 **Имя экземпляра**  
 Выберите из экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеющихся на компьютере. Если не удается получить список экземпляров, используйте MSSQLSERVER для просмотра экземпляра по умолчанию. В особенности это относится к удаленным компьютерам. Для просмотра экземпляра по умолчанию можно также использовать слово «default».  
  
 **Аутентификация**  
 Выберите из списка имеющихся режимов проверки подлинности на этом компьютере. По умолчанию установлен режим проверки подлинности Windows.  
  
 **User name**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] введите в поле имя пользователя. Рекомендуется, чтобы имя пользователя имело учетные данные администратора на компьютере.  
  
> [!NOTE]  
>  Если выбран вариант Проверка подлинности Windows, то имя пользователя, вошедшего в систему, будет заполнено в текстовом поле **имя пользователя** .  
  
 **Пароль**  
 Введите пароль для указанного пользователя.  
  
## <a name="see-also"></a>См. также:  
 [Работа с советником по переходу](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
