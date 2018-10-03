---
title: Отключение автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- automatic SQL Server startup
- SQL Server, stopping
- SQL Server, automatic startup
- canceling automatic startup
- stopping SQL Server
- preventing automatic startups [SQL Server]
ms.assetid: 782663cf-f3d7-4cc6-b621-21e4550f0322
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b3256362692c7319404ca564291ed98ac0ca0c6c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178304"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a>Отключение автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)
  В этом разделе описано, как отключить автоматический запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно настраивается для автоматического запуска. Это вы можете изменить, задав для экземпляра режим запуска вручную.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>Отключение автоматического запуска экземпляра SQL Server  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
2.  В диспетчере конфигурации SQL Server разверните **Службы**, затем выберите **SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой мыши **MSSQLServer**и выберите пункт **Свойства**.  
  
4.  В **SQL Server \< ***instancename***> свойства** отображаемое в диалоговом окне **свойства** поле, установите для параметра **перейти в режим**для **вручную**.  
  
5.  Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно **Свойства SQL Server \<***имя_экземпляра***>**, а затем закройте диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Запуск, остановка, приостановка, возобновление и перезапуск ядра СУБД, агента SQL Server и обозревателя SQL Server](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
