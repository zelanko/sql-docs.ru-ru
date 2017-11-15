---
title: "Настройка сервера для прослушивания альтернативного канала | Документы Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Named Pipes [SQL Server], configuring
- listening [SQL Server], pipes
- pipes [SQL Server], alternate
- alternate pipes [SQL Server]
ms.assetid: 914f7491-e2be-4b0d-b3aa-fe5409cdbafa
caps.latest.revision: "29"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: f45914bf0fbb614e8f59bfc0c413296ed44c68f9
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="configure-a-server-to-listen-on-an-alternate-pipe"></a>Настройка сервера для прослушивания альтернативного канала
  В этом разделе описан процесс настройки сервера на прослушивание другого канала в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью диспетчера конфигурации SQL Server. По умолчанию неименованный экземпляр компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] прослушивает именованный канал \\\\.\pipe\sql\query. Именованные экземпляры компонентов [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и [!INCLUDE[ssEW](../../includes/ssew-md.md)] настроены на прослушивание других каналов.  
  
 Клиентское приложение можно подключить к конкретному именованному каналу тремя способами:  
  
-   запустив на сервере службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   создав псевдоним клиента с указанием именованного канала;  
  
-   Настройте клиент на использование пользовательской строки подключения.  
  
##  <a name="SSMSProcedure"></a> Использование диспетчера конфигурации SQL Server  
  
#### <a name="to-configure-the-named-pipe-used-by-the-sql-server-database-engine"></a>Настройка именованного канала, используемого компонентом SQL Server Database Engine  
  
1.  В области консоли диспетчера конфигурации SQL Server разверните узел **Сетевая конфигурация SQL Server**, а затем — **Протоколы для** *\<имя экземпляра>*.  
  
2.  В области сведений щелкните правой кнопкой мыши **Именованные каналы**и выберите пункт **Свойства**.  
  
3.  На вкладке **Протоколы** в поле **Имя канала** укажите канал, который должен прослушиваться компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)] , и нажмите кнопку **ОК**.  
  
4.  В области консоли выберите **Службы SQL Server**.  
  
5.  В области сведений щелкните правой кнопкой мыши **SQL Server (**\<имя экземпляра>**)**, а затем нажмите кнопку **Перезагрузка**, чтобы остановить и перезагрузить [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Если [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] прослушивает альтернативный канал, то подключить клиентское приложение к конкретному именованному каналу можно тремя способами:  
  
-   запустив на сервере службу браузера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ;  
  
-   создав псевдоним клиента с указанием именованного канала;  
  
-   Настройте клиент на использование пользовательской строки подключения.  
  
## <a name="see-also"></a>См. также:  
 [Создание или удаление псевдонима сервера для использования клиентом (диспетчер конфигурации SQL Server)](../../database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client.md)   
 [Сетевая конфигурация сервера](../../database-engine/configure-windows/server-network-configuration.md)  
  
  
