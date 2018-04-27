---
title: Программное управление запуском пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.service: ''
ms.component: run-manage-packages-programmatically
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
caps.latest.revision: 19
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1e87373afb607c598d3cc5095bd15dc855f4908e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="managing-running-packages-programmatically"></a>Программное управление запуском пакетов
  При программном способе работы с пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может потребоваться определить, какие пакеты уже запущены в настоящее время. Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет необходимые для этого методы и классы.  
  
 Дополнительные сведения о мониторинге пакетов см. в разделе [Управление пакетами (службы SSIS)](../../integration-services/service/package-management-ssis-service.md).  
  
 Все методы, используемые в данном разделе, требуют наличия ссылки на сборку **Microsoft.SqlServer.ManagedDTS**. После добавления ссылки в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции **using** или **Imports**.  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только имена «.», localhost и имя сервера для локального сервера. Нельзя использовать имя «(local)».  
  
## <a name="determining-which-packages-are-currently-running"></a>Определение, какие пакеты запущены в настоящее время  
 Чтобы определить, какие пакеты запущены в настоящее время на указанном сервере, вызовите метод <xref:Microsoft.SqlServer.Dts.Runtime.Application.GetRunningPackages%2A>. Этот метод возвращает коллекцию <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> объектов <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage>.  
  
> [!NOTE]  
>  Администраторы могут видеть все пакеты, выполняющиеся в настоящее время на компьютере, а другие пользователи видят только те пакеты, которые запустили они сами.  
  
## <a name="working-with-running-packages"></a>Работа с запущенными пакетами  
 Определив, какие пакеты запущены в настоящее время, можно получить сведения об этих пакетах и запросить остановку выполнения пакета.  
  
### <a name="getting-information-about-a-running-package"></a>Получение сведений о запущенном пакете  
 При просмотре коллекции <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackages> можно с помощью свойств объекта <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage> найти пакет или получить дополнительные сведения о запущенных пакетах.  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionDuration%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.ExecutionStartTime%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.InstanceID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageDescription%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageID%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.PackageName%2A>  
  
-   <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.UserName%2A>  
  
### <a name="stopping-a-running-package"></a>Остановка выполнения пакета  
 Можно вызвать метод <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage.Stop%2A> объекта <xref:Microsoft.SqlServer.Dts.Runtime.RunningPackage>, чтобы остановить выполнение пакета. Между созданием запроса на остановку пакета и действительной остановкой пакета может пройти некоторое время.  
  
## <a name="see-also"></a>См. также:  
 [Управление пакетами (службы SSIS)](../../integration-services/service/package-management-ssis-service.md)   
 [Программное перечисление доступных пакетов](../../integration-services/run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  
