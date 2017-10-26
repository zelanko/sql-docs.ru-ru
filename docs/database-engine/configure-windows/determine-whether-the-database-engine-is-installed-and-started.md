---
title: "Проверка наличия установленного и запущенного компонента Database Engine | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 93b3736aa15a7e4fc7e7a1df829b96a0efa5ba19
ms.contentlocale: ru-ru
ms.lasthandoff: 08/02/2017

---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a>Проверка наличия установленного и запущенного компонента Database Engine
  При успешной установке компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] создаются записи в реестре, устанавливаются файлы в файловой системе и несколько программ. В этом разделе описано, как определить, успешно ли установлен и запущен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a>Просмотр состояния и запуск ядра СУБД при помощи диспетчера конфигурации SQL Server  
  
1.  В меню **Пуск**последовательно наведите указатель мыши на пункты **Программы**, **Microsoft SQL Server**, **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
     Если эти пункты отсутствуют в меню **Пуск** , то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не был установлен корректно. Запустите программу Setup для установки [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
2.  В **Диспетчере конфигурации SQL Server**на левой панели выберите **Службы SQL Server**. В правой панели содержится список служб, связанных с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен, то служба [!INCLUDE[ssDE](../../includes/ssde-md.md)] будет присутствовать в списке как **SQL Server (MSSQLSERVER)** , если это экземпляр по умолчанию, или как **SQL Server (**\<*имя_экземпляра*>**)**, если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен как именованный экземпляр. До изменения имени этого экземпляра [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливает этот экземпляр с именем **SQLEXPRESS**. Значок в виде зеленого треугольника означает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] запущен. Значок в виде красного квадрата означает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] остановлен.  
  
3.  Для запуска компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]на правой панели щелкните правой кнопкой мыши компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)]и выберите **Пуск**.  
  
> [!NOTE]  
>  Во время установки пользователь может выбрать, куда устанавливать файлы программ и баз данных. По умолчанию файлы устанавливаются в папки [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] и C:\Program Files\Microsoft SQL Server\MSSQL.*x*, где *x* является числом.  
  
  

