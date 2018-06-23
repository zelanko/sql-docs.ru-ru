---
title: Программное управление запуском пакетов | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], managing
- running packages [Integration Services]
ms.assetid: 0e91f4ac-6f29-40d7-8c28-9b82e4802c35
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: f07749d44644071bb5e7aab2a5f33759ce96cdb0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36193818"
---
# <a name="managing-running-packages-programmatically"></a>Программное управление запуском пакетов
  При программном способе работы с пакетами служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] может потребоваться определить, какие пакеты уже запущены в настоящее время. Класс <xref:Microsoft.SqlServer.Dts.Runtime.Application> пространства имен <xref:Microsoft.SqlServer.Dts.Runtime> предоставляет необходимые для этого методы и классы.  
  
 Дополнительные сведения о мониторинге пакетов см. в разделе [Управление пакетами (службы SSIS)](../service/package-management-ssis-service.md).  
  
 Все методы, описываемые в этом разделе, должны ссылаться на сборку `Microsoft.SqlServer.ManagedDTS`. После добавления ссылки в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции `using` или `Imports`.  
  
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
  
![Значок служб Integration Services (маленький)](../media/dts-16.gif "значок служб Integration Services (маленький)")**оставаться установка последних со службами Integration Services** <br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетите страницу служб Integration Services в MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.  
  
## <a name="see-also"></a>См. также  
 [Управление пакетами (службы SSIS)](../service/package-management-ssis-service.md)   
 [Программное перечисление доступных пакетов](../run-manage-packages-programmatically/enumerating-available-packages-programmatically.md)  
  
  