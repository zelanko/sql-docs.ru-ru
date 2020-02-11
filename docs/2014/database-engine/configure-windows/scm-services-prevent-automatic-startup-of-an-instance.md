---
title: Запрет автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
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
ms.openlocfilehash: 6af4597a4ddf802c80bc98cb38363d59348fa0bb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62810054"
---
# <a name="prevent-automatic-startup-of-an-instance-of-sql-server-sql-server-configuration-manager"></a>Отключение автоматического запуска экземпляра SQL Server (диспетчер конфигурации SQL Server)
  В этом разделе описано, как отключить автоматический запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] обычно настраивается для автоматического запуска. Это вы можете изменить, задав для экземпляра режим запуска вручную.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-prevent-automatic-startup-of-an-instance-of-sql-server"></a>Отключение автоматического запуска экземпляра SQL Server  
  
1.  В меню **Пуск** последовательно выберите пункты **Все программы**, [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)], **Средства настройки**и щелкните **Диспетчер конфигурации SQL Server**.  
  
2.  В диспетчер конфигурации SQL Server разверните узел **службы**и выберите пункт **SQL Server**.  
  
3.  В области сведений щелкните правой кнопкой мыши **MSSQLServer** и выберите пункт **Свойства**.  
  
4.  В диалоговом окне свойства ** \<SQL Server ** _instanceName_ **>** в поле **Свойства** установите для параметра **режим запуска** значение **вручную**.  
  
5.  Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно свойства ** \<SQL Server ** _instanceName_ **>** , а [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] затем закройте Configuration Manager.  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка, приостановка, возобновление и перезапуск компонента Database Engine, агента SQL и службы браузера SQL Server](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
