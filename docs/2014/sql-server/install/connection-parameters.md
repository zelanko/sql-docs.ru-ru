---
title: Параметры соединения | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Upgrade Advisor [SQL Server], connections
- authentication [Upgrade Advisor]
- SQL Server Upgrade Advisor, connections
- connections [Upgrade Advisor]
- server instances [Upgrade Advisor]
- default server instances
- analyzing system [Upgrade Advisor], connections
ms.assetid: f754d038-637a-4d8e-85b0-b242e6499d26
caps.latest.revision: 30
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dc99f9fc26f0e46f0f5ea0d717614bf5935f4814
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193304"
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
>  При выборе проверки подлинности Windows, имя пользователя, выполнившего вход пользователя заполняется **имя пользователя** текстовое поле.  
  
 **Пароль**  
 Введите пароль для указанного пользователя.  
  
## <a name="see-also"></a>См. также  
 [Работа с помощником по обновлению](../../../2014/sql-server/install/working-with-upgrade-advisor.md)   
 [Справочник по пользовательскому интерфейсу помощника по обновлению](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  