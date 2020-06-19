---
title: Проверка наличия установленного и запущенного компонента Database Engine | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: 0a912cf4a89f208543605cc84f480b63955214ab
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84935396"
---
# <a name="determine-whether-the-database-engine-is-installed-and-started"></a>Проверка наличия установленного и запущенного компонента Database Engine
  При успешной установке компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] создаются записи в реестре, устанавливаются файлы в файловой системе и несколько программ. В этом разделе описано, как определить, успешно ли установлен и запущен компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , с помощью диспетчера конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
##  <a name="using-sql-server-configuration-manager"></a><a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="how-to-view-and-start-the-database-engine-by-using-sql-server-configuration-manager"></a>Просмотр состояния и запуск ядра СУБД при помощи диспетчера конфигурации SQL Server  
  
1.  В меню **Пуск**последовательно наведите указатель мыши на пункты **Программы**, **Microsoft SQL Server**, **Средства настройки**и выберите пункт **Диспетчер конфигурации SQL Server**.  
  
     Если эти пункты отсутствуют в меню **Пуск** , то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не был установлен корректно. Запустите программу Setup для установки [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
2.  В **Диспетчере конфигурации SQL Server**на левой панели выберите **Службы SQL Server**. В правой панели содержится список служб, связанных с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен, [!INCLUDE[ssDE](../../includes/ssde-md.md)] служба отображается как **SQL Server (MSSQLSERVER)** , если это экземпляр по умолчанию; или **SQL Server (** \<*instance_name*> **)**, если [!INCLUDE[ssDE](../../includes/ssde-md.md)] установлен в качестве именованного экземпляра. До изменения имени этого экземпляра [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливает этот экземпляр с именем **SQLEXPRESS**. Значок в виде зеленого треугольника означает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] запущен. Значок в виде красного квадрата означает, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] остановлен.  
  
3.  Для запуска компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]на правой панели щелкните правой кнопкой мыши компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)]и выберите **Пуск**.  
  
> [!NOTE]  
>  Во время установки пользователь может выбрать, куда устанавливать файлы программ и баз данных. По умолчанию файлы устанавливаются в папки [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)] и C:\Program Files\Microsoft SQL Server\MSSQL.*x*, где *x* является числом.  
  
  
