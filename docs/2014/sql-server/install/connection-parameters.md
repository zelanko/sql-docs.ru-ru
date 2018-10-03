---
title: Параметры соединения | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
ms.openlocfilehash: b5259f12613a67d94f704d9c6d170e09f2ee5f17
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48125394"
---
# <a name="connection-parameters"></a>Параметры соединения
  Для анализа определенных типов сервера, таких как [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], необходимо выбрать конкретный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Автоматически выбирается экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию. Этот выбор можно изменить, однако советник по переходу одновременно может выполнять анализ только одного экземпляра. Если выбран тип сервера, требующий проверки подлинности, необходимо указать режим проверки подлинности и ввести учетные данные.  
  
## <a name="options"></a>Параметры  
 **Имя сервера**  
 Заранее заданное имя компьютера, введенное на панели «Компоненты [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]».  
  
 **Имя экземпляра**  
 Выберите из экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], имеющихся на компьютере. Если не удается получить список экземпляров, используйте MSSQLSERVER для просмотра экземпляра по умолчанию. В особенности это относится к удаленным компьютерам. Для просмотра экземпляра по умолчанию можно также использовать слово «default».  
  
 **Проверка подлинности**  
 Выберите из списка имеющихся режимов проверки подлинности на этом компьютере. По умолчанию установлен режим проверки подлинности Windows.  
  
 **Имя пользователя**  
 При использовании проверки подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] введите в поле имя пользователя. Рекомендуется, чтобы имя пользователя имело учетные данные администратора на компьютере.  
  
> [!NOTE]  
>  Если выбрана проверка подлинности Windows, имя пользователя, выполнившего вход пользователя заполняется **имя пользователя** текстовое поле.  
  
 **Пароль**  
 Введите пароль для указанного пользователя.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
