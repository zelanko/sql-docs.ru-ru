---
title: Просмотр пакетов в SQL Server Management Studio (службы SSIS) служб Integration Services | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- viewing packages
- connections [Integration Services], packages
ms.assetid: 783e653c-0f1f-45ed-b3ef-5ba07b019f27
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cffcc0e48851f3d023251d03d210fb78e3d1bd09
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48163364"
---
# <a name="view-integration-services-packages-in-sql-server-management-studio-ssis-service"></a>Просмотр пакетов служб Integration Services в среде SQL Server Management Studio (службы SSIS)
    
> [!IMPORTANT]  
>  В данном разделе описывается компонент [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] — служба Windows для управления пакетами служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] поддерживает эту службу для обеспечения обратной совместимости с более ранними версиями служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Начиная с [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], на сервере служб Integration Services можно управлять пакетами.  
  
 Эта процедура описывает подключение к службам [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и просмотр списка пакетов, которыми управляют службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] .  
  
### <a name="to-connect-to-integration-services"></a>Подключение к службам Integration Services  
  
1.  Нажмите кнопку **Пуск**, укажите пункт **Все программы**, пункт **Microsoft SQL Server**, а затем выберите команду **Среда SQL Server Management Studio**.  
  
2.  В диалоговом окне **Соединение с сервером** выберите **Службы Integration Services** в списке **Тип сервера** , введите имя сервера в поле **Имя сервера** и нажмите **Соединить**.  
  
    > [!IMPORTANT]  
    >  Если подключиться к [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]не удается, возможно, что служба [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] не запущена. Чтобы узнать о состоянии службы, нажмите кнопку **Пуск**и последовательно выберите пункты **Все программы**, **Microsoft SQL Server**, **Средства настройки**и **Диспетчер конфигурации SQL Server**. На левой панели щелкните **Службы SQL Server**. На панели справа найдите службу [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Если служба не запущена, запустите ее.  
  
     [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] . По умолчанию окно «Обозреватель объектов» открыто и находится в нижнем левом углу среды разработки. Если обозреватель объектов не открыт, выберите **Обозреватель объектов** в меню **Вид** .  
  
### <a name="to-view-the-packages-that-integration-services-service-manages"></a>Просмотр пакетов, управляемых службой служб Integration Services  
  
1.  В обозревателе объектов разверните папку «Сохраненные пакеты».  
  
2.  Разверните вложенные папки в папке «Сохраненные пакеты», чтобы показать пакеты.  
  
## <a name="see-also"></a>См. также  
 [Управление пакетами (службы SSIS)](service/package-management-ssis-service.md)   
 [Использование среды SQL Server Management Studio](../database-engine/use-sql-server-management-studio.md)  
  
  
