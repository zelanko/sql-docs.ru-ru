---
title: Проверка наличия установленного и запущенного компонента Database Engine | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, determining if installed
- verifying Database Engine installation
- viewing Database Engine installation
- installed Database Engine verification [SQL Server]
ms.assetid: babb02e4-3521-4b75-b5df-e09205594375
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f459f96ba44811997d33f592892d759389c4666a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796812"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a>Проверка наличия установленного и запущенного компонента Database Engine
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  При успешной установке компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] создаются записи в реестре, устанавливаются файлы в файловой системе и несколько программ. В этом разделе описано, как определить, успешно ли установлен и запущен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a>Просмотр состояния и запуск ядра СУБД при помощи диспетчера конфигурации SQL Server  
  
1.  В меню **Пуск**последовательно наведите указатель мыши на пункты **Программы**, **Microsoft SQL Server**, **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
     Если эти пункты отсутствуют в меню **Пуск** , то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не был установлен корректно. Запустите программу Setup для установки [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
2.  В **Диспетчере конфигурации SQL Server**на левой панели выберите **Службы SQL Server**. В правой панели содержится список служб, связанных с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен, то служба [!INCLUDE[ssDE](../../includes/ssde-md.md)] будет присутствовать в списке как **SQL Server (MSSQLSERVER)** , если это экземпляр по умолчанию, или как **SQL Server (**\<*имя_экземпляра*>**)**, если компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен как именованный экземпляр. До изменения имени этого экземпляра [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливает этот экземпляр с именем **SQLEXPRESS**. Значок в виде зеленого треугольника означает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] запущен. Значок в виде красного квадрата означает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] остановлен.  
  
3.  Для запуска компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]на правой панели щелкните правой кнопкой мыши компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)]и выберите **Пуск**.  
  
> [!NOTE]  
>  Во время установки пользователь может выбрать, куда устанавливать файлы программ и баз данных. По умолчанию файлы устанавливаются в папки [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] и C:\Program Files\Microsoft SQL Server\MSSQL.*x*, где *x* является числом.  
  
  
